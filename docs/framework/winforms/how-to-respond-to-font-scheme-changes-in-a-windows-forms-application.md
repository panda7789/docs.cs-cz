---
title: Reakce na změny schématu písem v aplikaci model Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739225"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="2399e-102">Postupy: Odpověď na změny schématu písem v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2399e-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="2399e-103">V operačních systémech Windows může uživatel změnit nastavení písem v rámci systému tak, aby výchozí písmo bylo větší nebo menší.</span><span class="sxs-lookup"><span data-stu-id="2399e-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="2399e-104">Změna těchto nastavení písma je zásadní pro uživatele, kteří jsou vizuálně poškozeni a vyžadují větší typ pro čtení textu na svých obrazovkách.</span><span class="sxs-lookup"><span data-stu-id="2399e-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="2399e-105">Aplikaci model Windows Forms můžete upravit tak, aby reagovala na tyto změny tím, že se zvětší nebo zmenší velikost formuláře a veškerý text, kdykoli se změní schéma písem.</span><span class="sxs-lookup"><span data-stu-id="2399e-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="2399e-106">Pokud chcete, aby formulář přizpůsobil změny velikosti písma dynamicky, můžete do formuláře přidat kód.</span><span class="sxs-lookup"><span data-stu-id="2399e-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="2399e-107">Výchozí písmo, které používá model Windows Forms, je obvykle písmo, které je vráceno voláním <xref:Microsoft.Win32> oboru názvů do `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="2399e-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="2399e-108">Písmo vrácené tímto voláním se změní pouze při změně rozlišení obrazovky.</span><span class="sxs-lookup"><span data-stu-id="2399e-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="2399e-109">Jak je znázorněno v následujícím postupu, váš kód musí změnit výchozí písmo, aby <xref:System.Drawing.SystemFonts.IconTitleFont%2A> reagovat na změny velikosti písma.</span><span class="sxs-lookup"><span data-stu-id="2399e-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="2399e-110">Použití písma desktopu a reakce na změny schématu písem</span><span class="sxs-lookup"><span data-stu-id="2399e-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1. <span data-ttu-id="2399e-111">Vytvořte formulář a přidejte do něj ovládací prvky, které chcete do něj přidat.</span><span class="sxs-lookup"><span data-stu-id="2399e-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="2399e-112">Další informace najdete v tématu [Postup: Vytvoření aplikace model Windows Forms z příkazového řádku](how-to-create-a-windows-forms-application-from-the-command-line.md) a [ovládací prvky pro použití v model Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2399e-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="2399e-113">Přidejte odkaz na obor názvů <xref:Microsoft.Win32> do kódu.</span><span class="sxs-lookup"><span data-stu-id="2399e-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="2399e-114">Přidejte následující kód do konstruktoru formuláře pro zapojení požadovaných obslužných rutin událostí a pro změnu výchozího písma používaného pro formulář.</span><span class="sxs-lookup"><span data-stu-id="2399e-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="2399e-115">Implementujte obslužnou rutinu pro událost <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>, která způsobuje automatické škálování formuláře při změně kategorie <xref:Microsoft.Win32.UserPreferenceCategory.Window>.</span><span class="sxs-lookup"><span data-stu-id="2399e-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. <span data-ttu-id="2399e-116">Nakonec Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.Form.FormClosing>, která odpojí obslužnou rutinu události <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="2399e-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="2399e-117">Pokud nechcete tento kód zahrnout do paměti, může vaše aplikace nevrácená paměť.</span><span class="sxs-lookup"><span data-stu-id="2399e-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. <span data-ttu-id="2399e-118">Zkompilujte a spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="2399e-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="2399e-119">Ruční změna schématu písem v systému Windows XP</span><span class="sxs-lookup"><span data-stu-id="2399e-119">To manually change the font scheme in Windows XP</span></span>  
  
1. <span data-ttu-id="2399e-120">Když je vaše aplikace model Windows Forms spuštěná, klikněte pravým tlačítkem myši na plochu Windows a v místní nabídce vyberte **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="2399e-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="2399e-121">V dialogovém okně **zobrazení vlastností** klikněte na kartu **vzhled** .</span><span class="sxs-lookup"><span data-stu-id="2399e-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3. <span data-ttu-id="2399e-122">V rozevíracím seznamu **Velikost písma** vyberte novou velikost písma.</span><span class="sxs-lookup"><span data-stu-id="2399e-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="2399e-123">Všimněte si, že formulář nyní reaguje na změny za běhu ve schématu písem pro stolní počítače.</span><span class="sxs-lookup"><span data-stu-id="2399e-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="2399e-124">Když se uživatel změní mezi **normálním**, **velkým písmem**a **dalšími velkými**písmy, změní formulář písmo a správně škáluje.</span><span class="sxs-lookup"><span data-stu-id="2399e-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2399e-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="2399e-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="2399e-126">Konstruktor v tomto příkladu kódu obsahuje volání `InitializeComponent`, které je definováno při vytváření nového projektu model Windows Forms v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2399e-126">The constructor in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="2399e-127">Odeberte tento řádek kódu, pokud vytváříte aplikaci na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="2399e-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2399e-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="2399e-128">See also</span></span>

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [<span data-ttu-id="2399e-129">Automatická změna měřítka ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2399e-129">Automatic Scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
