---
title: Mezinárodní písma ve formulářích a ovládacích prvcích
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: 59dde6bb384d644321a8ff5674d735f8e6d36fd0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743518"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Mezinárodní písma v model Windows Forms a ovládacích prvcích

V mezinárodních aplikacích je doporučeným způsobem výběru písem použití nouzového písma, pokud je to možné. Náhradní písmo znamená, že systém Určuje, do kterého skriptu patří znak.

## <a name="using-font-fallback"></a>Použití Fallback písma

Chcete-li tuto funkci využít, nenastavujte vlastnost <xref:System.Drawing.Font> pro formulář nebo jiný prvek. Aplikace automaticky použije výchozí systémové písmo, které se bude lišit od jednoho lokalizovaného jazyka operačního systému do jiného. Po spuštění aplikace systém automaticky poskytne správné písmo pro jazykovou verzi vybranou v operačním systému.

Existuje výjimka pro pravidlo nenastavené písma, které je pro změnu stylu písma. To může být důležité pro aplikaci, ve které uživatel klikne na tlačítko, aby se text v textovém poli zobrazoval tučně. K tomu byste měli napsat funkci, která změní styl písma textového pole na tučné, a to na základě toho, jestli je písmo formuláře. Je důležité zavolat tuto funkci na dvou místech: v obslužné rutině události <xref:System.Windows.Forms.Control.Click> tlačítka a v obslužné rutině události <xref:System.Windows.Forms.Control.FontChanged>. Pokud je funkce volána pouze v obslužné rutině události <xref:System.Windows.Forms.Control.Click> a některé jiné části kódu mění rodinu písem celého formuláře, textové pole se nezmění se zbytkem formuláře.

```vb
Private Sub MakeBold()
   ' Change the TextBox to a bold version of the form font
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)
End Sub

Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
   ' Clicking this button makes the TextBox bold
   MakeBold()
End Sub

Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged
   ' If the TextBox is already bold and the form's font changes,
   ' change the TextBox to a bold version of the new form font
   If (TextBox1.Font.Style = FontStyle.Bold) Then
      MakeBold()
   End If
End Sub
```

```csharp
private void button1_Click(object sender, System.EventArgs e)
{
   // Clicking this button makes the TextBox bold
   MakeBold();
}

private void MakeBold()
{
   // Change the TextBox to a bold version of the form's font
   textBox1.Font = new Font(this.Font, FontStyle.Bold);
}

private void Form1_FontChanged(object sender, System.EventArgs e)
{
   // If the TextBox is already bold and the form's font changes,
   // change the TextBox to a bold version of the new form font
   if (textBox1.Font.Style == FontStyle.Bold)
   {
      MakeBold();
   }
}
```

Při lokalizaci aplikace se ale tučné písmo může zobrazit v některých jazycích špatně. Pokud se to týká, chcete, aby měly Lokalizovatelný možnost přepnout písmo z tučného na běžný text. Vzhledem k tomu, že lokalizováni nejsou obvykle vývojáři a nemají přístup ke zdrojovému kódu, pouze soubory prostředků, tato možnost musí být nastavena v souborech prostředků. Chcete-li to provést, nastavte vlastnost <xref:System.Drawing.Font.Bold%2A> na hodnotu `true`. To vede k tomu, že se nastavení fontu zapisuje do souborů prostředků, kde je mohou lokalizovat mohli upravovat. Potom můžete napsat kód za `InitializeComponent` metodou pro resetování písma na základě toho, co je písmo formuláře, ale pomocí stylu písma zadaného v souboru prostředků.

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>Viz také

- [Použití písem a textu](using-fonts-and-text.md)
