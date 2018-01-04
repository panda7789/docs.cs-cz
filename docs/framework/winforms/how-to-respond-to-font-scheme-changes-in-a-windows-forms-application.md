---
title: "Postupy: Odpověď na změny schématu písem ve formulářové aplikaci Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aac8d56c87ff03b313565a3d04cd3f3cc4e85f72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="41044-102">Postupy: Odpověď na změny schématu písem ve formulářové aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="41044-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="41044-103">V operačních systémech Windows uživatel může změnit nastavení systémového písma, aby byly výchozí písmo zobrazí větší nebo menší.</span><span class="sxs-lookup"><span data-stu-id="41044-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="41044-104">Změna těchto nastavení písma je velmi důležitá pro uživatele, kteří jsou slabozraké a vyžadují větší typ ke čtení textu na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="41044-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="41044-105">Můžete upravit aplikaci Windows Forms reagování na tyto změny zvýšením nebo snížením velikosti formulář a všechny obsažené text vždy, když změny schématu písem.</span><span class="sxs-lookup"><span data-stu-id="41044-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="41044-106">Pokud chcete, aby svého formuláře dynamicky zohlednit změny velikosti písem, můžete přidat kód do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="41044-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="41044-107">Výchozí písmo použité ve Windows Forms je obvykle písmo vrácený <xref:Microsoft.Win32> volání obor názvů `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="41044-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="41044-108">Písmo vrácený toto volání se změní jenom v případě změny rozlišení obrazovky.</span><span class="sxs-lookup"><span data-stu-id="41044-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="41044-109">Jak je znázorněno v následujícím postupu, kódu musíte změnit výchozí písmo na <xref:System.Drawing.SystemFonts.IconTitleFont%2A> reagovat na změny velikosti písma.</span><span class="sxs-lookup"><span data-stu-id="41044-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="41044-110">Použít plochy písma a reagovat na změny schématu písem</span><span class="sxs-lookup"><span data-stu-id="41044-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1.  <span data-ttu-id="41044-111">Vytvořte svého formuláře a ovládací prvky, které chcete přidat do ní.</span><span class="sxs-lookup"><span data-stu-id="41044-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="41044-112">Další informace najdete v tématu [postupy: Vytvoření Formulářové aplikace Windows z příkazového řádku](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) a [ovládací prvky používané ve formulářích Windows](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="41044-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="41044-113">Přidat odkaz na <xref:Microsoft.Win32> oboru názvů do vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="41044-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="41044-114">Přidejte následující kód do konstruktoru objektu svého formuláře spojit Obslužné rutiny požadované událostí a chcete-li změnit písmo výchozí používá pro daný formulář.</span><span class="sxs-lookup"><span data-stu-id="41044-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="41044-115">Implementujte obslužnou rutinu pro <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> událost, která způsobí, že formulář automaticky škálovat při <xref:Microsoft.Win32.UserPreferenceCategory.Window> kategorie změny.</span><span class="sxs-lookup"><span data-stu-id="41044-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  <span data-ttu-id="41044-116">Nakonec implementovat obslužnou rutinu pro <xref:System.Windows.Forms.Form.FormClosing> událost, která umožňuje odpojit <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="41044-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="41044-117">Selhání zahrnout tento kód způsobí, že vaše aplikace a nastat únik paměti.</span><span class="sxs-lookup"><span data-stu-id="41044-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  <span data-ttu-id="41044-118">Zkompilování a spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="41044-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="41044-119">Ruční změny schématu písem v systému Windows XP</span><span class="sxs-lookup"><span data-stu-id="41044-119">To manually change the font scheme in Windows XP</span></span>  
  
1.  <span data-ttu-id="41044-120">Když je spuštěna aplikace Windows Forms, klikněte pravým tlačítkem na ploše systému Windows a vyberte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="41044-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="41044-121">V **vlastností zobrazení** dialogové okno, klikněte na tlačítko **vzhled** kartě.</span><span class="sxs-lookup"><span data-stu-id="41044-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3.  <span data-ttu-id="41044-122">Z **velikost písma** rozevíracího seznamu vyberte novou velikost písma.</span><span class="sxs-lookup"><span data-stu-id="41044-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="41044-123">Si všimnete, že formulář nyní reaguje na spuštění čas změny ve schématu plochy písma.</span><span class="sxs-lookup"><span data-stu-id="41044-123">You will notice that the form now reacts to run time changes in the desktop font scheme.</span></span> <span data-ttu-id="41044-124">Když uživatel změní mezi **normální**, **velká písma**, a **navíc velká písma**, formulář změní písmo a škáluje správně.</span><span class="sxs-lookup"><span data-stu-id="41044-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41044-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="41044-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="41044-126">Constructer v tomto příkladu kódu obsahuje volání `InitializeComponent`, který je definován při vytvoření nového projektu Windows Forms v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41044-126">The constructer in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="41044-127">Pokud vytváříte aplikace na příkazovém řádku, odeberte tento řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="41044-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41044-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="41044-128">See Also</span></span>  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [<span data-ttu-id="41044-129">Automatická změna měřítka ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41044-129">Automatic Scaling in Windows Forms</span></span>](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
