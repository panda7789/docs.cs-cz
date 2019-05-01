---
title: Shromáždění rukopisu v aplikacích WPF
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: 0d0796eae469f8a40e01e3de02c00149eb3f00c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051270"
---
# <a name="collect-ink"></a><span data-ttu-id="2d3d2-102">Shromáždění inkoustu</span><span class="sxs-lookup"><span data-stu-id="2d3d2-102">Collect Ink</span></span>

<span data-ttu-id="2d3d2-103">[Windows Presentation Foundation](../index.md) platformy shromažďuje digitálních inkoust jeho funkce v rámci jádra.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-103">The [Windows Presentation Foundation](../index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="2d3d2-104">Toto téma popisuje metody pro kolekci rukopis ve Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="2d3d2-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2d3d2-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d3d2-105">Prerequisites</span></span>

<span data-ttu-id="2d3d2-106">Pokud chcete použít v následujících příkladech, je třeba nejprve nainstalovat Visual Studio a [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d3d2-106">To use the following examples, you must first install Visual Studio and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="2d3d2-107">Musíte taky vědět, jak pro psaní aplikací pro WPF.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="2d3d2-108">Další informace o zahájení práce s WPF naleznete v tématu [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="2d3d2-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="2d3d2-109">Použít inkcanvas – Element</span><span class="sxs-lookup"><span data-stu-id="2d3d2-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="2d3d2-110"><xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> Element poskytuje nejjednodušší způsob, jak shromažďovat rukopisu v subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="2d3d2-111">Použití <xref:System.Windows.Controls.InkCanvas> – element pro příjem a zobrazení vstupu rukopisu.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="2d3d2-112">Běžně vstupu inkoustu pomocí pera, která komunikuje s digitizéru k vytvoření inkoustových tahů.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="2d3d2-113">Kromě toho je možné místo stylus myši.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="2d3d2-114">Vytvořený tahy jsou reprezentovány ve formě <xref:System.Windows.Ink.Stroke> objekty a jejich lze ovládat jak prostřednictvím kódu programu a uživatelem vstup.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="2d3d2-115"><xref:System.Windows.Controls.InkCanvas> Umožňuje uživatelům vybrat, upravit nebo odstranit existující <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="2d3d2-116">Pomocí XAML můžete nastavit kolekce inkoustů stejně snadno, jako přidávání **InkCanvas** element vaše stromové struktury.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="2d3d2-117">Následující příklad přidá <xref:System.Windows.Controls.InkCanvas> do projektu WPF výchozí vytvořeného v sadě Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="2d3d2-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="2d3d2-118">**InkCanvas** element může také obsahovat podřízené prvky, což umožňuje přidat poznámky funkce inkoustu na téměř libovolný typ elementu XAML.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="2d3d2-119">Například pro přidání možností rukopisu do textu elementu, stačí udělat podřízeným z <xref:System.Windows.Controls.InkCanvas>:</span><span class="sxs-lookup"><span data-stu-id="2d3d2-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="2d3d2-120">Přidání podpory pro označení image s rukopisem je stejně jednoduché:</span><span class="sxs-lookup"><span data-stu-id="2d3d2-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="2d3d2-121">Režimy InkCollection</span><span class="sxs-lookup"><span data-stu-id="2d3d2-121">InkCollection Modes</span></span>

<span data-ttu-id="2d3d2-122"><xref:System.Windows.Controls.InkCanvas> Poskytuje podporu pro různé vstupní režimy prostřednictvím jeho <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="2d3d2-123">Zpracování inkoustu</span><span class="sxs-lookup"><span data-stu-id="2d3d2-123">Manipulate Ink</span></span>

<span data-ttu-id="2d3d2-124"><xref:System.Windows.Controls.InkCanvas> Poskytuje podporu pro mnoho inkoustu operace úprav.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="2d3d2-125">Například <xref:System.Windows.Controls.InkCanvas> vymazat podporuje back sady pera a bez dalšího kódu, je potřeba přidat funkce do elementu.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="2d3d2-126">Výběr</span><span class="sxs-lookup"><span data-stu-id="2d3d2-126">Selection</span></span>

<span data-ttu-id="2d3d2-127">Nastavení režimu výběru je stejně jednoduché jako nastavení <xref:System.Windows.Controls.InkCanvasEditingMode> vlastnost **vyberte**.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="2d3d2-128">Následující kód nastaví režim úprav podle hodnoty <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="2d3d2-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="2d3d2-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="2d3d2-129">DrawingAttributes</span></span>

<span data-ttu-id="2d3d2-130">Použití <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> vlastnost změnit vzhled inkoustových tahů.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="2d3d2-131">Například <xref:System.Windows.Ink.DrawingAttributes.Color%2A> členem <xref:System.Windows.Ink.DrawingAttributes> nastavuje barvu vygenerované <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="2d3d2-132">Následující příklad změní barvu vybraných tahů na červený:</span><span class="sxs-lookup"><span data-stu-id="2d3d2-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="2d3d2-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="2d3d2-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="2d3d2-134"><xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Poskytuje přístup k vlastnosti, jako je výšku, šířku a barvu tahů bude vytvořena ve vlastnosti <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="2d3d2-135">Po změně <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, všechny budoucí tahy do <xref:System.Windows.Controls.InkCanvas> jsou generovány s novými hodnotami vlastností.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="2d3d2-136">Spolu s prováděním změn <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> v souboru kódu na pozadí, můžete použít syntaxe XAML pro určení <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="2d3d2-137">Následující příklad ukazuje, jak nastavit <xref:System.Windows.Ink.DrawingAttributes.Color%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="2d3d2-138">Chcete-li tento kód použít, vytvořte nový projekt WPF s názvem "HelloInkCanvas" v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="2d3d2-139">Nahraďte kód v *souboru MainWindow.xaml* souboru následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2d3d2-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="2d3d2-140">Pak přidejte do souboru uvnitř třídy hlavního okna MainWindow kódu obslužné rutiny událostí následující tlačítka:</span><span class="sxs-lookup"><span data-stu-id="2d3d2-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="2d3d2-141">Po zkopírování tento kód, stiskněte klávesu **F5** v sadě Visual Studio ke spuštění programu v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="2d3d2-142">Všimněte si, že jak <xref:System.Windows.Controls.StackPanel> umístí tlačítka v horní části <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="2d3d2-143">Pokud se pokusíte rukopisu v horní části na tlačítka, <xref:System.Windows.Controls.InkCanvas> shromažďuje a vykreslí rukopis za tlačítka.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="2d3d2-144">Důvodem je, že tlačítka jsou na stejné úrovni <xref:System.Windows.Controls.InkCanvas> na rozdíl od podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="2d3d2-145">Tlačítka jsou také, výše v pořadí vykreslování, takže se vykreslí rukopis za nimi stojí.</span><span class="sxs-lookup"><span data-stu-id="2d3d2-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d3d2-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d3d2-146">See also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>