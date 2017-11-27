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
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="feba1-102">Mezinárodní písma ve Windows Forms a ovládacích prvcích</span><span class="sxs-lookup"><span data-stu-id="feba1-102">International Fonts in Windows Forms and Controls</span></span>
<span data-ttu-id="feba1-103">Doporučené metody výběru písem mezinárodní aplikace je použít záložní písma, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="feba1-103">In International applications the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="feba1-104">Písmo záložní znamená systém zjišťuje, jaké skriptu znak, který patří do.</span><span class="sxs-lookup"><span data-stu-id="feba1-104">Font fallback means that the system determines what script the character belongs to.</span></span>  
  
## <a name="using-font-fallback"></a><span data-ttu-id="feba1-105">Použití záložního písma</span><span class="sxs-lookup"><span data-stu-id="feba1-105">Using Font Fallback</span></span>  
 <span data-ttu-id="feba1-106">Chcete-li tuto funkci využít, nenastavujte <xref:System.Drawing.Font> vlastnost pro daný formulář nebo jiného elementu.</span><span class="sxs-lookup"><span data-stu-id="feba1-106">To take advantage of this feature, do not set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="feba1-107">Aplikace budou automaticky používat na písmo, které se liší od jednoho lokalizovaném jazyce operačního systému do jiného.</span><span class="sxs-lookup"><span data-stu-id="feba1-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="feba1-108">Když je aplikace spuštěná, systém automaticky poskytovat správné písmo pro jazykovou verzi vybrané v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="feba1-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>  
  
 <span data-ttu-id="feba1-109">Dojde k výjimce pravidla není nastavení písma, který je pro změnu styl písma.</span><span class="sxs-lookup"><span data-stu-id="feba1-109">There is an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="feba1-110">To může být důležité pro aplikaci, ve kterém uživatel kliknutím na tlačítko, chcete-li text v textovém poli se zobrazí v tučné písmo.</span><span class="sxs-lookup"><span data-stu-id="feba1-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="feba1-111">Kvůli tomu by zápis funkce chcete-li změnit písmo textového pole na tučné písmo podle toho, ať formuláře písma.</span><span class="sxs-lookup"><span data-stu-id="feba1-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="feba1-112">Je důležité pro volání této funkce na dvou místech: na tlačítku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události a <xref:System.Windows.Forms.Control.FontChanged> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="feba1-112">It is important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="feba1-113">Pokud je tato funkce volána pouze v <xref:System.Windows.Forms.Control.Click> obslužné rutiny události a dalších částí kódu změní rodiny písem celého formuláře, textového pole nezmění se zbytkem formuláře.</span><span class="sxs-lookup"><span data-stu-id="feba1-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box will not change with the rest of the form.</span></span>  
  
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
  
 <span data-ttu-id="feba1-114">Ale při lokalizaci berte vaší aplikace, tučným písmem může zobrazit chybně pro určité jazyky.</span><span class="sxs-lookup"><span data-stu-id="feba1-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="feba1-115">Pokud se jedná o problém, budete chtít překladatelům při lokalizaci mít možnost přepínání z tučné písmo na běžný text.</span><span class="sxs-lookup"><span data-stu-id="feba1-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="feba1-116">Vzhledem k tomu, že překladatelům při lokalizaci nejsou obvykle vývojáři a nemají přístup ke zdrojovému kódu, pouze na soubory prostředků, tato možnost je třeba nastavit v souborech prostředků.</span><span class="sxs-lookup"><span data-stu-id="feba1-116">Since localizers are typically not developers and do not have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="feba1-117">K tomuto účelu se nastavuje <xref:System.Drawing.Font.Bold%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="feba1-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="feba1-118">Výsledkem zápisem na soubory prostředků, kde překladatelům při lokalizaci můžete upravit nastavení písma.</span><span class="sxs-lookup"><span data-stu-id="feba1-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="feba1-119">Potom napíšete kód po `InitializeComponent` metoda resetovat písmo podle toho, bez ohledu na tvar na písma, ale pomocí styl písma zadaný v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="feba1-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## <a name="see-also"></a><span data-ttu-id="feba1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="feba1-120">See Also</span></span>  
 [<span data-ttu-id="feba1-121">Globalizace Windows Forms</span><span class="sxs-lookup"><span data-stu-id="feba1-121">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)  
 [<span data-ttu-id="feba1-122">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="feba1-122">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
