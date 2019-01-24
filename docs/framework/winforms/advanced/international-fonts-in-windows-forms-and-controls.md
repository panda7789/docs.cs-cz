---
title: Mezinárodní písma ve Windows Forms a ovládacích prvků
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
ms.openlocfilehash: 1f9afd575e2de04e0b11556ad34436839e13d968
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693237"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Mezinárodní písma ve Windows Forms a ovládacích prvků

V aplikacích výběru písma doporučujeme použít záložní písma, kdykoli je to možné. Písmo záložní znamená, že systém zjišťuje, co skript znak, který patří do.

## <a name="using-font-fallback"></a>Použití záložního písma

Abyste mohli využívat tuto funkci, nemají nastavený <xref:System.Drawing.Font> vlastnost formuláře nebo jiný prvek. Aplikace automaticky použije výchozí systémové písmo, které se liší od jednoho lokalizovaný jazyk operačního systému do druhého. Při spuštění aplikace, systém automaticky poskytovat použitím správného písma pro jazykovou verzi vybrané v operačním systému.

Dojde k výjimce z pravidla nelze nastavit písmo, které je pro změnu styl písma. To může být důležité pro aplikaci, ve kterém uživatel klikne na tlačítko provést text v textovém poli se zobrazí v tučné písmo. K tomu, měli byste napsat funkci, kterou chcete změnit písmo textového pole mají být zobrazena tučně, podle toho libovolné formuláře písma. Je důležité pro volání této funkce na dvou místech: na tlačítku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události a <xref:System.Windows.Forms.Control.FontChanged> obslužné rutiny události. Pokud je tato funkce volána pouze v <xref:System.Windows.Forms.Control.Click> obslužná rutina události a další část kódu změní rodinu písem celý formulář, do textového pole se nezmění se zbytkem formuláře.

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

Však při lokalizaci berte vaší aplikace, tučné písmo se může zobrazit nesprávně pro určité jazyky. Pokud je to žádný problém, chcete Lokalizátoři nabízet možnost přepínání písmo z tučného písma na běžný text. Lokalizátoři obvykle nejsou vývojáři a nemáte přístup ke zdrojovému kódu, pouze na soubory prostředků, tato možnost musí být nastavena v souborech prostředků. Chcete-li to provést, nastavte <xref:System.Drawing.Font.Bold%2A> vlastnost `true`. Výsledkem je zapsán do souborů prostředků, kde Lokalizátoři můžete upravit nastavení písma. Potom napíšete kód za `InitializeComponent` metoda resetovat písmo podle je písmo libovolné formuláře, ale styl písma pomocí zadaných v souboru prostředků.

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>Viz také:

- [Globalizace aplikací Windows Forms](globalizing-windows-forms.md)
- [Použití písem a textu](using-fonts-and-text.md)
