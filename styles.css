// Elementos do DOM
const form = document.getElementById('curriculumForm');
const previewBtn = document.getElementById('previewBtn');
const generatePdfBtn = document.getElementById('generatePdfBtn');
const preview = document.getElementById('curriculumPreview');
const pdfTemplate = document.getElementById('pdfTemplate');

// Campos do formulário
const fields = {
    nome: document.getElementById('nome'),
    email: document.getElementById('email'),
    telefone: document.getElementById('telefone'),
    endereco: document.getElementById('endereco'),
    resumo: document.getElementById('resumo'),
    experiencia: document.getElementById('experiencia'),
    educacao: document.getElementById('educacao'),
    habilidades: document.getElementById('habilidades')
};

// Elementos de erro
const errorElements = {
    nome: document.getElementById('nome-error'),
    email: document.getElementById('email-error'),
    resumo: document.getElementById('resumo-error')
};

// Função para validar email
function isValidEmail(email) {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return emailRegex.test(email);
}

// Função para validar campos obrigatórios
function validateField(fieldName, value) {
    const errors = [];
    
    switch (fieldName) {
        case 'nome':
            if (!value.trim()) {
                errors.push('Nome é obrigatório');
            } else if (value.trim().length < 2) {
                errors.push('Nome deve ter pelo menos 2 caracteres');
            }
            break;
            
        case 'email':
            if (!value.trim()) {
                errors.push('E-mail é obrigatório');
            } else if (!isValidEmail(value)) {
                errors.push('E-mail deve ter um formato válido');
            }
            break;
            
        case 'resumo':
            if (!value.trim()) {
                errors.push('Resumo profissional é obrigatório');
            } else if (value.trim().length < 10) {
                errors.push('Resumo deve ter pelo menos 10 caracteres');
            }
            break;
    }
    
    return errors;
}

// Função para mostrar erro
function showError(fieldName, message) {
    const errorElement = errorElements[fieldName];
    const fieldElement = fields[fieldName];
    
    if (errorElement && fieldElement) {
        errorElement.textContent = message;
        errorElement.classList.add('show');
        fieldElement.parentElement.classList.add('error');
    }
}

// Função para limpar erro
function clearError(fieldName) {
    const errorElement = errorElements[fieldName];
    const fieldElement = fields[fieldName];
    
    if (errorElement && fieldElement) {
        errorElement.textContent = '';
        errorElement.classList.remove('show');
        fieldElement.parentElement.classList.remove('error');
    }
}

// Função para validar formulário completo
function validateForm() {
    let isValid = true;
    const requiredFields = ['nome', 'email', 'resumo'];
    
    // Limpar erros anteriores
    requiredFields.forEach(fieldName => clearError(fieldName));
    
    // Validar cada campo obrigatório
    requiredFields.forEach(fieldName => {
        const value = fields[fieldName].value;
        const errors = validateField(fieldName, value);
        
        if (errors.length > 0) {
            showError(fieldName, errors[0]);
            isValid = false;
        }
    });
    
    return isValid;
}

// Função para formatar texto com quebras de linha
function formatText(text) {
    if (!text) return '';
    return text.split('\n').map(line => line.trim()).filter(line => line).join('<br>');
}

// Função para gerar preview do currículo
function generatePreview() {
    const data = {};
    
    // Coletar dados do formulário
    Object.keys(fields).forEach(key => {
        data[key] = fields[key].value.trim();
    });
    
    // Verificar se há dados suficientes para preview
    if (!data.nome && !data.email && !data.resumo) {
        preview.innerHTML = `
            <div class="preview-placeholder">
                <p>Preencha o formulário para ver a pré-visualização do seu currículo</p>
            </div>
        `;
        return;
    }
    
    // Gerar HTML do preview
    let previewHTML = '<div class="curriculum-document">';
    
    // Header
    if (data.nome || data.email || data.telefone || data.endereco) {
        previewHTML += '<header class="curriculum-header">';
        if (data.nome) {
            previewHTML += `<h1>${data.nome}</h1>`;
        }
        previewHTML += '<div class="contact-info">';
        if (data.email) {
            previewHTML += `<p>📧 ${data.email}</p>`;
        }
        if (data.telefone) {
            previewHTML += `<p>📞 ${data.telefone}</p>`;
        }
        if (data.endereco) {
            previewHTML += `<p>📍 ${data.endereco}</p>`;
        }
        previewHTML += '</div></header>';
    }
    
    // Resumo Profissional
    if (data.resumo) {
        previewHTML += `
            <section class="curriculum-section">
                <h2>Resumo Profissional</h2>
                <p>${formatText(data.resumo)}</p>
            </section>
        `;
    }
    
    // Experiência Profissional
    if (data.experiencia) {
        previewHTML += `
            <section class="curriculum-section">
                <h2>Experiência Profissional</h2>
                <div>${formatText(data.experiencia)}</div>
            </section>
        `;
    }
    
    // Formação Acadêmica
    if (data.educacao) {
        previewHTML += `
            <section class="curriculum-section">
                <h2>Formação Acadêmica</h2>
                <div>${formatText(data.educacao)}</div>
            </section>
        `;
    }
    
    // Habilidades
    if (data.habilidades) {
        previewHTML += `
            <section class="curriculum-section">
                <h2>Habilidades</h2>
                <div>${formatText(data.habilidades)}</div>
            </section>
        `;
    }
    
    previewHTML += '</div>';
    
    preview.innerHTML = previewHTML;
    preview.classList.add('loaded');
}

// Função para popular template PDF
function populatePdfTemplate() {
    const data = {};
    
    // Coletar dados do formulário
    Object.keys(fields).forEach(key => {
        data[key] = fields[key].value.trim();
    });
    
    // Popular elementos do template PDF
    const pdfNome = document.getElementById('pdf-nome');
    const pdfEmail = document.getElementById('pdf-email');
    const pdfTelefone = document.getElementById('pdf-telefone');
    const pdfEndereco = document.getElementById('pdf-endereco');
    const pdfResumo = document.getElementById('pdf-resumo');
    const pdfExperiencia = document.getElementById('pdf-experiencia');
    const pdfEducacao = document.getElementById('pdf-educacao');
    const pdfHabilidades = document.getElementById('pdf-habilidades');
    
    // Limpar conteúdo anterior
    [pdfNome, pdfEmail, pdfTelefone, pdfEndereco, pdfResumo, pdfExperiencia, pdfEducacao, pdfHabilidades].forEach(el => {
        if (el) el.innerHTML = '';
    });
    
    // Popular com novos dados
    if (pdfNome) pdfNome.textContent = data.nome || '';
    if (pdfEmail && data.email) pdfEmail.textContent = `📧 ${data.email}`;
    if (pdfTelefone && data.telefone) pdfTelefone.textContent = `📞 ${data.telefone}`;
    if (pdfEndereco && data.endereco) pdfEndereco.textContent = `📍 ${data.endereco}`;
    
    // Formatar textos com quebras de linha
    if (pdfResumo && data.resumo) {
        pdfResumo.innerHTML = formatText(data.resumo);
    }
    if (pdfExperiencia && data.experiencia) {
        pdfExperiencia.innerHTML = formatText(data.experiencia);
    }
    if (pdfEducacao && data.educacao) {
        pdfEducacao.innerHTML = formatText(data.educacao);
    }
    if (pdfHabilidades && data.habilidades) {
        pdfHabilidades.innerHTML = formatText(data.habilidades);
    }
    
    // Mostrar/ocultar seções baseado no conteúdo
    const sections = [
        { id: 'pdf-resumo-section', content: data.resumo },
        { id: 'pdf-experiencia-section', content: data.experiencia },
        { id: 'pdf-educacao-section', content: data.educacao },
        { id: 'pdf-habilidades-section', content: data.habilidades }
    ];
    
    sections.forEach(section => {
        const element = document.getElementById(section.id);
        if (element) {
            element.style.display = section.content ? 'block' : 'none';
        }
    });
    
    // Garantir que o header seja sempre visível se houver pelo menos nome
    const headerElement = document.querySelector('#pdfTemplate .curriculum-header');
    if (headerElement) {
        headerElement.style.display = data.nome ? 'block' : 'none';
    }
}

// Função para gerar PDF
async function generatePDF() {
    if (!validateForm()) {
        alert('Por favor, corrija os erros no formulário antes de gerar o PDF.');
        return;
    }
    
    // Mostrar estado de loading
    generatePdfBtn.classList.add('loading');
    generatePdfBtn.textContent = 'Gerando PDF...';
    generatePdfBtn.disabled = true;
    
    try {
        // Popular template PDF
        populatePdfTemplate();
        
        // Tornar o template visível temporariamente para captura
        const originalDisplay = pdfTemplate.style.display;
        pdfTemplate.style.display = 'block';
        pdfTemplate.style.position = 'absolute';
        pdfTemplate.style.left = '-9999px';
        pdfTemplate.style.top = '0';
        
        // Aguardar um momento para o DOM se atualizar
        await new Promise(resolve => setTimeout(resolve, 100));
        
        // Configurações do PDF
        const options = {
            margin: [10, 10, 10, 10],
            filename: `curriculo_${fields.nome.value.replace(/\s+/g, '_').toLowerCase()}.pdf`,
            image: { type: 'jpeg', quality: 0.98 },
            html2canvas: { 
                scale: 2,
                useCORS: true,
                letterRendering: true,
                allowTaint: true,
                backgroundColor: '#ffffff'
            },
            jsPDF: { 
                unit: 'mm', 
                format: 'a4', 
                orientation: 'portrait' 
            }
        };
        
        // Gerar PDF
        await html2pdf().set(options).from(pdfTemplate).save();
        
        // Restaurar estado original do template
        pdfTemplate.style.display = originalDisplay;
        pdfTemplate.style.position = '';
        pdfTemplate.style.left = '';
        pdfTemplate.style.top = '';
        
        // Mostrar mensagem de sucesso
        showToast('PDF gerado com sucesso!', 'success');
        
    } catch (error) {
        console.error('Erro ao gerar PDF:', error);
        showToast('Erro ao gerar PDF. Tente novamente.', 'error');
        
        // Restaurar estado original do template em caso de erro
        pdfTemplate.style.display = 'none';
        pdfTemplate.style.position = '';
        pdfTemplate.style.left = '';
        pdfTemplate.style.top = '';
    } finally {
        // Remover estado de loading
        generatePdfBtn.classList.remove('loading');
        generatePdfBtn.textContent = 'Gerar PDF';
        generatePdfBtn.disabled = false;
    }
}

// Event listeners
document.addEventListener('DOMContentLoaded', function() {
    // Validação em tempo real
    Object.keys(fields).forEach(fieldName => {
        const field = fields[fieldName];
        
        field.addEventListener('blur', function() {
            if (['nome', 'email', 'resumo'].includes(fieldName)) {
                const errors = validateField(fieldName, this.value);
                if (errors.length > 0) {
                    showError(fieldName, errors[0]);
                } else {
                    clearError(fieldName);
                }
            }
        });
        
        field.addEventListener('input', function() {
            // Limpar erro quando usuário começar a digitar
            if (errorElements[fieldName]) {
                clearError(fieldName);
            }
            
            // Atualizar preview em tempo real (com debounce)
            clearTimeout(field.debounceTimer);
            field.debounceTimer = setTimeout(generatePreview, 300);
        });
    });
    
    // Botão de preview
    previewBtn.addEventListener('click', function() {
        generatePreview();
        
        // Scroll suave para o preview
        document.querySelector('.preview-container').scrollIntoView({
            behavior: 'smooth',
            block: 'start'
        });
    });
    
    // Botão de gerar PDF
    generatePdfBtn.addEventListener('click', generatePDF);
    
    // Validação do formulário ao submeter
    form.addEventListener('submit', function(e) {
        e.preventDefault();
        generatePDF();
    });
    
    // Gerar preview inicial se houver dados
    generatePreview();
});

// Função para formatar telefone automaticamente
fields.telefone.addEventListener('input', function(e) {
    let value = e.target.value.replace(/\D/g, '');
    
    if (value.length <= 11) {
        if (value.length <= 2) {
            value = value.replace(/(\d{0,2})/, '($1');
        } else if (value.length <= 7) {
            value = value.replace(/(\d{2})(\d{0,5})/, '($1) $2');
        } else {
            value = value.replace(/(\d{2})(\d{5})(\d{0,4})/, '($1) $2-$3');
        }
    }
    
    e.target.value = value;
});

// Função para melhorar a experiência do usuário
function showToast(message, type = 'info') {
    // Criar elemento de toast
    const toast = document.createElement('div');
    toast.className = `toast toast-${type}`;
    toast.textContent = message;
    
    // Estilos do toast
    Object.assign(toast.style, {
        position: 'fixed',
        top: '20px',
        right: '20px',
        padding: '12px 24px',
        borderRadius: '8px',
        color: 'white',
        fontWeight: '500',
        zIndex: '9999',
        transform: 'translateX(100%)',
        transition: 'transform 0.3s ease',
        backgroundColor: type === 'success' ? '#16a34a' : type === 'error' ? '#dc2626' : '#2563eb'
    });
    
    document.body.appendChild(toast);
    
    // Animar entrada
    setTimeout(() => {
        toast.style.transform = 'translateX(0)';
    }, 100);
    
    // Remover após 3 segundos
    setTimeout(() => {
        toast.style.transform = 'translateX(100%)';
        setTimeout(() => {
            document.body.removeChild(toast);
        }, 300);
    }, 3000);
}

