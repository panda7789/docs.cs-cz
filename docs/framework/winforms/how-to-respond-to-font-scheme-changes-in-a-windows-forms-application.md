---
title: 'Postupy: Reakce na změny schématu písem ve formulářové aplikaci Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 73a6c20f1790ca4ad1dbe331d693af2331da1ea1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682265"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="c6067-102">Postupy: Reakce na změny schématu písem ve formulářové aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="c6067-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="c6067-103">V operačních systémech Windows uživatel může změnit nastavení systémová písma a ujistěte se zobrazí výchozí písmo větší nebo menší.</span><span class="sxs-lookup"><span data-stu-id="c6067-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="c6067-104">Změna těchto písmo nastavení je velmi důležité pro uživatele, kteří jsou slabozraké a vyžadují větší typ čtení textu na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="c6067-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="c6067-105">Můžete upravit aplikaci Windows Forms k reagovat na tyto změny zvýšením nebo snížením velikosti formuláře a veškerý text při každé změně schématu písem.</span><span class="sxs-lookup"><span data-stu-id="c6067-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="c6067-106">Pokud chcete formuláře dynamicky přizpůsobí změny velikosti písma, můžete přidat kód do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c6067-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="c6067-107">Obvykle je výchozí písmo použité ve Windows Forms písma vrácené <xref:Microsoft.Win32> obor názvů volání `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="c6067-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="c6067-108">Pokud se rozlišení změní pouze změní písmo vrácený toto volání.</span><span class="sxs-lookup"><span data-stu-id="c6067-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="c6067-109">Jak je znázorněno v následujícím postupu, musí váš kód změnit výchozí písmo na <xref:System.Drawing.SystemFonts.IconTitleFont%2A> reakce na změny velikosti písma.</span><span class="sxs-lookup"><span data-stu-id="c6067-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="c6067-110">Písmo plochy pomocí a reagovat na změny schématu písem</span><span class="sxs-lookup"><span data-stu-id="c6067-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1.  <span data-ttu-id="c6067-111">Vytvoření formuláře a ovládací prvky, které chcete přidat do ní.</span><span class="sxs-lookup"><span data-stu-id="c6067-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="c6067-112">Další informace najdete v tématu [jak: Vytvoření aplikace Windows Forms z příkazového řádku](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) a [ovládací prvky používané ve formulářích Windows](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c6067-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="c6067-113">Přidejte odkaz na <xref:Microsoft.Win32> oboru názvů do vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="c6067-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="c6067-114">Přidejte následující kód do konstruktoru formuláře k obslužné rutiny události požadované připojení a chcete-li změnit výchozí písmo používané pro daný formulář.</span><span class="sxs-lookup"><span data-stu-id="c6067-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="c6067-115">Implementujte obslužnou rutinu pro <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> událost, která způsobí, že formulář pro automatické škálování při <xref:Microsoft.Win32.UserPreferenceCategory.Window> změny kategorií.</span><span class="sxs-lookup"><span data-stu-id="c6067-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  <span data-ttu-id="c6067-116">A konečně, implementujte obslužnou rutinu pro <xref:System.Windows.Forms.Form.FormClosing> událost, která se odpojí <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c6067-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="c6067-117">Nepodařilo se přidat tento kód způsobí aplikace únik paměti.</span><span class="sxs-lookup"><span data-stu-id="c6067-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6.  <span data-ttu-id="c6067-118">Kompilace a spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="c6067-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="c6067-119">Ruční změny schématu písem ve Windows XP</span><span class="sxs-lookup"><span data-stu-id="c6067-119">To manually change the font scheme in Windows XP</span></span>  
  
1.  <span data-ttu-id="c6067-120">Když je spuštěna aplikace Windows Forms, klikněte pravým tlačítkem na plochu Windows a zvolte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="c6067-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="c6067-121">V **vlastnosti zobrazení** dialogové okno, klikněte na tlačítko **vzhled** kartu.</span><span class="sxs-lookup"><span data-stu-id="c6067-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3.  <span data-ttu-id="c6067-122">Z **velikost písma** rozevíracího seznamu vyberte novou velikost písma.</span><span class="sxs-lookup"><span data-stu-id="c6067-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="c6067-123">Můžete si všimnout, že formulář nyní reaguje na změny za běhu v režimu plochy písma.</span><span class="sxs-lookup"><span data-stu-id="c6067-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="c6067-124">Když uživatel změní mezi **normální**, **velká písma**, a **další velký písma**, formulář se změní písmo a škáluje správně.</span><span class="sxs-lookup"><span data-stu-id="c6067-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6067-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6067-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="c6067-126">Constructer v tomto příkladu kód obsahuje volání `InitializeComponent`, který je definován při vytváření nového projektu Windows Forms v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6067-126">The constructer in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="c6067-127">Odeberte tento řádek kódu, pokud vytváříte aplikaci na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="c6067-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6067-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6067-128">See also</span></span>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [<span data-ttu-id="c6067-129">Automatická změna měřítka ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6067-129">Automatic Scaling in Windows Forms</span></span>](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
