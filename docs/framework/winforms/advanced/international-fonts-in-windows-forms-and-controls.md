---
title: Mezinárodní písma v model Windows Forms a ovládacích prvcích
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
ms.openlocfilehash: 0ddbd6d7a1b614d588a2572b410957a5ed3b768c
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956908"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="934b4-102">Mezinárodní písma v model Windows Forms a ovládacích prvcích</span><span class="sxs-lookup"><span data-stu-id="934b4-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="934b4-103">V mezinárodních aplikacích je doporučeným způsobem výběru písem použití nouzového písma, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="934b4-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="934b4-104">Náhradní písmo znamená, že systém Určuje, do kterého skriptu patří znak.</span><span class="sxs-lookup"><span data-stu-id="934b4-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="934b4-105">Použití Fallback písma</span><span class="sxs-lookup"><span data-stu-id="934b4-105">Using font fallback</span></span>

<span data-ttu-id="934b4-106">Chcete-li tuto funkci využít, nenastavujte vlastnost <xref:System.Drawing.Font> pro formulář nebo jiný prvek.</span><span class="sxs-lookup"><span data-stu-id="934b4-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="934b4-107">Aplikace automaticky použije výchozí systémové písmo, které se bude lišit od jednoho lokalizovaného jazyka operačního systému do jiného.</span><span class="sxs-lookup"><span data-stu-id="934b4-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="934b4-108">Po spuštění aplikace systém automaticky poskytne správné písmo pro jazykovou verzi vybranou v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="934b4-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="934b4-109">Existuje výjimka pro pravidlo nenastavené písma, které je pro změnu stylu písma.</span><span class="sxs-lookup"><span data-stu-id="934b4-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="934b4-110">To může být důležité pro aplikaci, ve které uživatel klikne na tlačítko, aby se text v textovém poli zobrazoval tučně.</span><span class="sxs-lookup"><span data-stu-id="934b4-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="934b4-111">K tomu byste měli napsat funkci, která změní styl písma textového pole na tučné, a to na základě toho, jestli je písmo formuláře.</span><span class="sxs-lookup"><span data-stu-id="934b4-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="934b4-112">Je důležité zavolat tuto funkci na dvou místech: v obslužné rutině události <xref:System.Windows.Forms.Control.Click> na tlačítku a v obslužné rutině události <xref:System.Windows.Forms.Control.FontChanged>.</span><span class="sxs-lookup"><span data-stu-id="934b4-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="934b4-113">Pokud je funkce volána pouze v obslužné rutině události <xref:System.Windows.Forms.Control.Click> a jiná část kódu změní rodinu písem celého formuláře, textové pole se nezmění se zbytkem formuláře.</span><span class="sxs-lookup"><span data-stu-id="934b4-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

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

<span data-ttu-id="934b4-114">Při lokalizaci aplikace se ale tučné písmo může zobrazit v některých jazycích špatně.</span><span class="sxs-lookup"><span data-stu-id="934b4-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="934b4-115">Pokud se to týká, chcete, aby měly Lokalizovatelný možnost přepnout písmo z tučného na běžný text.</span><span class="sxs-lookup"><span data-stu-id="934b4-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="934b4-116">Vzhledem k tomu, že lokalizováni nejsou obvykle vývojáři a nemají přístup ke zdrojovému kódu, pouze soubory prostředků, tato možnost musí být nastavena v souborech prostředků.</span><span class="sxs-lookup"><span data-stu-id="934b4-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="934b4-117">Chcete-li to provést, nastavte vlastnost <xref:System.Drawing.Font.Bold%2A> na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="934b4-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="934b4-118">To vede k tomu, že se nastavení fontu zapisuje do souborů prostředků, kde je mohou lokalizovat mohli upravovat.</span><span class="sxs-lookup"><span data-stu-id="934b4-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="934b4-119">Potom napíšete kód za metodou `InitializeComponent` pro resetování písma na základě toho, co je písmo formuláře, ale s použitím stylu písma zadaného v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="934b4-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="934b4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="934b4-120">See also</span></span>

- [<span data-ttu-id="934b4-121">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="934b4-121">Using Fonts and Text</span></span>](using-fonts-and-text.md)
