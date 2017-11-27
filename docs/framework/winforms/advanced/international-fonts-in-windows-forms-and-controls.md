---
title: "Mezinárodní písma ve Windows Forms a ovládacích prvcích"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5901113021deffd601b5325ff9a1b8912e74329d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Mezinárodní písma ve Windows Forms a ovládacích prvcích
Doporučené metody výběru písem mezinárodní aplikace je použít záložní písma, kdykoli je to možné. Písmo záložní znamená systém zjišťuje, jaké skriptu znak, který patří do.  
  
## <a name="using-font-fallback"></a>Použití záložního písma  
 Chcete-li tuto funkci využít, nenastavujte <xref:System.Drawing.Font> vlastnost pro daný formulář nebo jiného elementu. Aplikace budou automaticky používat na písmo, které se liší od jednoho lokalizovaném jazyce operačního systému do jiného. Když je aplikace spuštěná, systém automaticky poskytovat správné písmo pro jazykovou verzi vybrané v operačním systému.  
  
 Dojde k výjimce pravidla není nastavení písma, který je pro změnu styl písma. To může být důležité pro aplikaci, ve kterém uživatel kliknutím na tlačítko, chcete-li text v textovém poli se zobrazí v tučné písmo. Kvůli tomu by zápis funkce chcete-li změnit písmo textového pole na tučné písmo podle toho, ať formuláře písma. Je důležité pro volání této funkce na dvou místech: na tlačítku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události a <xref:System.Windows.Forms.Control.FontChanged> obslužné rutiny události. Pokud je tato funkce volána pouze v <xref:System.Windows.Forms.Control.Click> obslužné rutiny události a dalších částí kódu změní rodiny písem celého formuláře, textového pole nezmění se zbytkem formuláře.  
  
```  
' Visual Basic  
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
  
// C#  
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
  
 Ale při lokalizaci berte vaší aplikace, tučným písmem může zobrazit chybně pro určité jazyky. Pokud se jedná o problém, budete chtít překladatelům při lokalizaci mít možnost přepínání z tučné písmo na běžný text. Vzhledem k tomu, že překladatelům při lokalizaci nejsou obvykle vývojáři a nemají přístup ke zdrojovému kódu, pouze na soubory prostředků, tato možnost je třeba nastavit v souborech prostředků. K tomuto účelu se nastavuje <xref:System.Drawing.Font.Bold%2A> vlastnost `true`. Výsledkem zápisem na soubory prostředků, kde překladatelům při lokalizaci můžete upravit nastavení písma. Potom napíšete kód po `InitializeComponent` metoda resetovat písmo podle toho, bez ohledu na tvar na písma, ale pomocí styl písma zadaný v souboru prostředků.  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## <a name="see-also"></a>Viz také  
 [Globalizace Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)  
 [Použití písem a textu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
