# 🖼️ Image Processor
Um pacote Python completo para processamento de imagens com suporte a múltiplas operações e formatos. Desenvolvido para ser simples de usar, mas poderoso o suficiente para tarefas complexas de processamento de imagem.

---

## ✨ Funcionalidades

### 🎨 Filtros de Imagem
- **Conversão para Escala de Cinza**: Transforme imagens coloridas em preto e branco.
- **Aplicação de Filtros**: Blur, Sharpen, Emboss, Contour, Edge Enhance, Smooth, Detail, Find Edges e mais.
- **Filtro Gaussiano**: Blur com controle de intensidade.
- **Detecção de Bordas**: Utilizando algoritmo Canny do OpenCV.
- **Ajustes de Cor**: Brilho e contraste ajustáveis.

### 🔄 Transformações
- **Redimensionamento**: Alterar tamanho com diferentes algoritmos de interpolação.
- **Rotação**: Gire imagens em qualquer ângulo.
- **Flip**: Espelhamento horizontal e vertical.
- **Crop**: Recorte preciso de regiões da imagem.

### 🛠️ Utilitários
- **Validação de Imagens**: Verifique se arquivos são imagens válidas.
- **Informações da Imagem**: Obtenha metadados detalhados.
- **Conversão de Formatos**: Suporte para JPEG, PNG, BMP, GIF, TIFF, WEBP.
- **Tratamento de Erros**: Exceções específicas para diferentes cenários.

---

## 🚀 Instalação

### Instalação via pip
```bash
pip install Pillow opencv-python numpy
```

### Instalação a partir do código fonte
```bash
git clone https://github.com/seu-usuario/image_processor.git
cd image_processor
pip install -e .
```

---

## 📦 Dependências
- Pillow >= 9.0.0 — Processamento básico de imagens.
- opencv-python >= 4.5.0 — Processamento avançado e visão computacional.
- numpy >= 1.21.0 — Manipulação de arrays numéricos.

---

## ⚡ Uso Rápido
```python
from image_processor import (
    convert_to_grayscale,
    resize_image,
    apply_filter,
    detect_edges,
    get_image_info
)

# Converter para escala de cinza
convert_to_grayscale("input.jpg", "output_gray.jpg")

# Redimensionar imagem
resize_image("input.jpg", "output_resized.jpg", 300, 200)

# Aplicar filtro blur
apply_filter("input.jpg", "output_blur.jpg", "blur")

# Detectar bordas (requer OpenCV)
detect_edges("input.jpg", "output_edges.jpg", threshold=100)

# Obter informações da imagem
info = get_image_info("input.jpg")
print(f"Tamanho: {info['width']}x{info['height']}")
```

---

## 🎯 Exemplos Completos

### Exemplo 1: Pipeline de Processamento
```python
from image_processor import (
    convert_to_grayscale,
    resize_image,
    apply_filter,
    adjust_brightness
)

input_path = "foto.jpg"
convert_to_grayscale(input_path, "temp_gray.jpg")
resize_image("temp_gray.jpg", "temp_resized.jpg", 800, 600)
apply_filter("temp_resized.jpg", "temp_blur.jpg", "gaussian_blur", radius=2)
adjust_brightness("temp_blur.jpg", "final_result.jpg", 1.2)
```

### Exemplo 2: Processamento em Lote
```python
from pathlib import Path
from image_processor import convert_to_grayscale

input_dir = Path("fotos/")
output_dir = Path("processadas/")
output_dir.mkdir(exist_ok=True)

for img_path in input_dir.glob("*.jpg"):
    output_path = output_dir / f"gray_{img_path.name}"
    convert_to_grayscale(str(img_path), str(output_path))
```

### Exemplo 3: Uso Avançado com Tratamento de Erros
```python
from image_processor import (
    convert_to_grayscale,
    detect_edges,
    ImageNotFoundError,
    FilterError
)

try:
    convert_to_grayscale("input.jpg", "gray.jpg")
    detect_edges("gray.jpg", "edges.jpg")
except ImageNotFoundError as e:
    print(f"Erro: Arquivo não encontrado - {e}")
except FilterError as e:
    print(f"Erro no processamento - {e}")
except Exception as e:
    print(f"Erro inesperado - {e}")
```

---

## 🧪 Testes
O pacote inclui uma suíte completa de testes:
```bash
# Executar todos os testes
pytest

# Executar testes com cobertura
pytest --cov=image_processor
```

---

## 📁 Estrutura do Projeto
```
image_processor/
├── image_processor/       # Código fonte do pacote
│   ├── __init__.py
│   ├── filters.py
│   ├── transformations.py
│   ├── utils.py
│   └── exceptions.py
├── tests/                 # Testes unitários
├── examples/              # Exemplos de uso
├── requirements.txt
├── setup.py
├── pyproject.toml
└── README.md
```

---

## 🛡️ Tratamento de Erros
O pacote utiliza exceções específicas para melhor tratamento de erros:
```python
from image_processor.exceptions import (
    ImageNotFoundError,      # Arquivo não encontrado
    InvalidImageError,       # Arquivo corrompido ou inválido
    UnsupportedFormatError,  # Formato não suportado
    FilterError              # Erro durante processamento
)
```

---

## 🌟 Características Avançadas
✅ Tipagem Estática: Type hints completos para melhor desenvolvimento  
✅ Documentação Completa: Docstrings detalhadas em todas as funções  
✅ Compatibilidade: Suporte para Python 3.8+  
✅ Performance: Otimizado para processamento rápido de imagens  
✅ Extensível: Fácil de adicionar novos filtros e funcionalidades  

---

## 🤝 Contribuição
Contribuições são bem-vindas!
1. Faça um fork do projeto  
2. Crie uma branch para sua feature (`git checkout -b feature/NovaFeature`)  
3. Commit suas mudanças (`git commit -m 'Adiciona NovaFeature'`)  
4. Push para a branch (`git push origin feature/NovaFeature`)  
5. Abra um Pull Request  

---

## 📜 Licença
Distribuído sob licença MIT. Veja o arquivo LICENSE para mais informações.

---

## 👨‍💻 Autor
Douglas Castilho — @Castilhos02

Aluno de TI na UNIVESP

[Perfil DIO](https://www.dio.me/users/dcastilhosdrive)
