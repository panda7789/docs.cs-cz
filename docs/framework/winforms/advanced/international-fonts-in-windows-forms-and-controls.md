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
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="97b67-102">Mezinárodní písma ve Windows Forms a ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="97b67-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="97b67-103">V aplikacích výběru písma doporučujeme použít záložní písma, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="97b67-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="97b67-104">Písmo záložní znamená, že systém zjišťuje, co skript znak, který patří do.</span><span class="sxs-lookup"><span data-stu-id="97b67-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="97b67-105">Použití záložního písma</span><span class="sxs-lookup"><span data-stu-id="97b67-105">Using font fallback</span></span>

<span data-ttu-id="97b67-106">Abyste mohli využívat tuto funkci, nemají nastavený <xref:System.Drawing.Font> vlastnost formuláře nebo jiný prvek.</span><span class="sxs-lookup"><span data-stu-id="97b67-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="97b67-107">Aplikace automaticky použije výchozí systémové písmo, které se liší od jednoho lokalizovaný jazyk operačního systému do druhého.</span><span class="sxs-lookup"><span data-stu-id="97b67-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="97b67-108">Při spuštění aplikace, systém automaticky poskytovat použitím správného písma pro jazykovou verzi vybrané v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="97b67-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="97b67-109">Dojde k výjimce z pravidla nelze nastavit písmo, které je pro změnu styl písma.</span><span class="sxs-lookup"><span data-stu-id="97b67-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="97b67-110">To může být důležité pro aplikaci, ve kterém uživatel klikne na tlačítko provést text v textovém poli se zobrazí v tučné písmo.</span><span class="sxs-lookup"><span data-stu-id="97b67-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="97b67-111">K tomu, měli byste napsat funkci, kterou chcete změnit písmo textového pole mají být zobrazena tučně, podle toho libovolné formuláře písma.</span><span class="sxs-lookup"><span data-stu-id="97b67-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="97b67-112">Je důležité pro volání této funkce na dvou místech: na tlačítku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události a <xref:System.Windows.Forms.Control.FontChanged> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="97b67-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="97b67-113">Pokud je tato funkce volána pouze v <xref:System.Windows.Forms.Control.Click> obslužná rutina události a další část kódu změní rodinu písem celý formulář, do textového pole se nezmění se zbytkem formuláře.</span><span class="sxs-lookup"><span data-stu-id="97b67-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

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

<span data-ttu-id="97b67-114">Však při lokalizaci berte vaší aplikace, tučné písmo se může zobrazit nesprávně pro určité jazyky.</span><span class="sxs-lookup"><span data-stu-id="97b67-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="97b67-115">Pokud je to žádný problém, chcete Lokalizátoři nabízet možnost přepínání písmo z tučného písma na běžný text.</span><span class="sxs-lookup"><span data-stu-id="97b67-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="97b67-116">Lokalizátoři obvykle nejsou vývojáři a nemáte přístup ke zdrojovému kódu, pouze na soubory prostředků, tato možnost musí být nastavena v souborech prostředků.</span><span class="sxs-lookup"><span data-stu-id="97b67-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="97b67-117">Chcete-li to provést, nastavte <xref:System.Drawing.Font.Bold%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="97b67-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="97b67-118">Výsledkem je zapsán do souborů prostředků, kde Lokalizátoři můžete upravit nastavení písma.</span><span class="sxs-lookup"><span data-stu-id="97b67-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="97b67-119">Potom napíšete kód za `InitializeComponent` metoda resetovat písmo podle je písmo libovolné formuláře, ale styl písma pomocí zadaných v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="97b67-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="97b67-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97b67-120">See also</span></span>

- [<span data-ttu-id="97b67-121">Globalizace aplikací Windows Forms</span><span class="sxs-lookup"><span data-stu-id="97b67-121">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
- [<span data-ttu-id="97b67-122">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="97b67-122">Using Fonts and Text</span></span>](using-fonts-and-text.md)
