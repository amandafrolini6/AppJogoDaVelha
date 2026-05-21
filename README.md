# 🎮 App Jogo da Velha — .NET MAUI

Projeto desenvolvido para a disciplina de **Programação para Dispositivos Móveis II** na **Fatec Jahu**, ministrada pelo professor [Tiago](https://github.com/tiagotas).

---

## 📋 Sobre o Projeto

Implementação do clássico **Jogo da Velha** para dispositivos móveis e desktop, desenvolvido com **.NET MAUI** (Multi-platform App UI). O app permite que dois jogadores se alternem em uma mesma tela, disputando rodadas no tabuleiro 3x3, com detecção automática de vencedor e empate.

---

## 🎯 Objetivos

- Praticar o uso do layout **Grid** para organização de elementos em linhas e colunas
- Implementar e reutilizar **eventos Clicked** compartilhados entre múltiplos botões
- Manipular **matrizes bidimensionais** em C# para representar o estado do tabuleiro
- Aplicar o conceito de **code-behind** no padrão XAML + C# do MAUI
- Praticar lógica de programação com verificação de condições de vitória

---

## 🗂️ Estrutura do Projeto

```
AppJogoDaVelha/
├── MainPage.xaml          # Interface visual (Grid, Botões, Labels)
├── MainPage.xaml.cs       # Lógica do jogo (code-behind)
├── AppShell.xaml          # Shell de navegação do app
├── App.xaml               # Recursos globais do app
├── MauiProgram.cs         # Ponto de entrada e configuração do MAUI
└── Platforms/             # Configurações específicas por plataforma
    ├── Android/
    ├── iOS/
    ├── Windows/
    └── MacCatalyst/
```

---

## 📸 Fotos da Tela

<img width="335" height="694" alt="image" src="https://github.com/user-attachments/assets/3b3560bf-7360-42d9-8990-9035a0e47ea1" />
<img width="334" height="681" alt="image" src="https://github.com/user-attachments/assets/42b58e3c-c2a4-4cc9-ad66-9985195de639" />
<img width="327" height="679" alt="image" src="https://github.com/user-attachments/assets/4574d6ce-008c-42c1-bf4b-bd2ab93f8211" />
<img width="333" height="699" alt="image" src="https://github.com/user-attachments/assets/98e900d2-3f78-4ff2-a0de-660effa79677" />

---

## 🧱 Conceitos Técnicos Utilizados

### Grid (Layout)
O tabuleiro é construído com o layout `Grid`, que organiza elementos em **linhas e colunas**. O uso de `*` nas definições garante distribuição proporcional do espaço, tornando o layout responsivo em qualquer tamanho de tela.

```xml
<Grid x:Name="jogo"
      RowDefinitions="*, *, *, *, *, *"
      ColumnDefinitions="*, *, *"
      RowSpacing="5"
      ColumnSpacing="5">
```

| Linha | Conteúdo |
|---|---|
| Row 0 | Título "Jogo da Velha" |
| Row 1 | 1ª fileira de botões |
| Row 2 | 2ª fileira de botões |
| Row 3 | 3ª fileira de botões |
| Row 4 | Label de status ("Vez do X") |
| Row 5 | Botão "Novo jogo" |

### Evento Clicked Compartilhado
Todos os 9 botões do tabuleiro apontam para o **mesmo handler** `Button_Clicked`. O botão clicado é identificado via o parâmetro `sender`, eliminando duplicação de código.

```csharp
private async void Button_Clicked(object sender, EventArgs e)
{
    Button clicado = (Button)sender; // identifica qual botão foi clicado
    clicado.Text = vez;              // marca X ou O
    clicado.IsEnabled = false;       // impede clique duplo
    ...
}
```

### Matriz de Jogadas
O estado do tabuleiro é espelhado em uma matriz `string[3,3]`, atualizada a cada jogada. As posições são lidas diretamente das propriedades `Grid.GetRow()` e `Grid.GetColumn()`.

```csharp
string[,] matriz_jogadas = new string[3, 3];
// [0,0][0,1][0,2]
// [1,0][1,1][1,2]
// [2,0][2,1][2,2]
```

### Verificação de Vitória
A cada jogada são verificadas três condições:
- **Horizontal** — três iguais na mesma linha
- **Vertical** — três iguais na mesma coluna
- **Diagonal** — três iguais em qualquer diagonal

---

## 🛠️ Tecnologias

| Tecnologia | Uso |
|---|---|
| .NET MAUI | Framework multiplataforma |
| C# | Lógica do jogo (code-behind) |
| XAML | Declaração da interface visual |
| .NET 9 | Versão da plataforma |
