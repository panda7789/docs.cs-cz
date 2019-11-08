---
title: Shromažďování rukopisu v aplikacích WPF
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
ms.openlocfilehash: 8109e0d6a746d6ca23c25643c510014c1a1e656c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740875"
---
# <a name="collect-ink"></a><span data-ttu-id="6bba6-102">Shromáždit rukopis</span><span class="sxs-lookup"><span data-stu-id="6bba6-102">Collect Ink</span></span>

<span data-ttu-id="6bba6-103">Platforma [Windows Presentation Foundation](../index.md) shromažďuje digitální inkoust jako základní součást jeho funkcí.</span><span class="sxs-lookup"><span data-stu-id="6bba6-103">The [Windows Presentation Foundation](../index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="6bba6-104">Toto téma popisuje metody pro kolekci rukopisu v Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="6bba6-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6bba6-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bba6-105">Prerequisites</span></span>

<span data-ttu-id="6bba6-106">Chcete-li použít následující příklady, je nutné nejprve nainstalovat aplikaci Visual Studio a Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="6bba6-106">To use the following examples, you must first install Visual Studio and the Windows SDK.</span></span> <span data-ttu-id="6bba6-107">Měli byste také pochopit, jak psát aplikace pro WPF.</span><span class="sxs-lookup"><span data-stu-id="6bba6-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="6bba6-108">Další informace o tom, jak začít používat WPF, najdete v tématu [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="6bba6-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="6bba6-109">Použití elementu InkCanvas</span><span class="sxs-lookup"><span data-stu-id="6bba6-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="6bba6-110">Element <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> poskytuje nejjednodušší způsob, jak v WPF shromažďovat rukopis.</span><span class="sxs-lookup"><span data-stu-id="6bba6-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="6bba6-111">Použijte prvek <xref:System.Windows.Controls.InkCanvas> pro příjem a zobrazení vstupu rukopisu.</span><span class="sxs-lookup"><span data-stu-id="6bba6-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="6bba6-112">Obvykle zadáváte inkoust pomocí stylusu, který komunikuje s digitizérem, aby vytvořil tahy perem.</span><span class="sxs-lookup"><span data-stu-id="6bba6-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="6bba6-113">Kromě toho lze použít myš místo stylusu.</span><span class="sxs-lookup"><span data-stu-id="6bba6-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="6bba6-114">Vytvořené tahy jsou reprezentovány jako <xref:System.Windows.Ink.Stroke> objekty a lze je manipulovat programově i uživatelským vstupem.</span><span class="sxs-lookup"><span data-stu-id="6bba6-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="6bba6-115"><xref:System.Windows.Controls.InkCanvas> umožňuje uživatelům vybrat, upravit nebo odstranit existující <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="6bba6-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="6bba6-116">Pomocí jazyka XAML můžete nastavit kolekci rukopisu jako snadnou přidáním prvku **InkCanvas** do stromu.</span><span class="sxs-lookup"><span data-stu-id="6bba6-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="6bba6-117">Následující příklad přidá <xref:System.Windows.Controls.InkCanvas> do výchozího projektu WPF vytvořeného v aplikaci Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="6bba6-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="6bba6-118">Element **InkCanvas** může také obsahovat podřízené prvky, což umožňuje přidat možnosti rukopisné poznámky pro téměř jakýkoli typ elementu XAML.</span><span class="sxs-lookup"><span data-stu-id="6bba6-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="6bba6-119">Chcete-li například přidat možnosti psaní do textového prvku, stačí vytvořit podřízený objekt <xref:System.Windows.Controls.InkCanvas>:</span><span class="sxs-lookup"><span data-stu-id="6bba6-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="6bba6-120">Přidání podpory pro označení obrázku pomocí rukopisu je stejně snadné:</span><span class="sxs-lookup"><span data-stu-id="6bba6-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="6bba6-121">InkCollection režimy</span><span class="sxs-lookup"><span data-stu-id="6bba6-121">InkCollection Modes</span></span>

<span data-ttu-id="6bba6-122"><xref:System.Windows.Controls.InkCanvas> poskytuje podporu pro různé vstupní režimy prostřednictvím její vlastnosti <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bba6-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="6bba6-123">Manipulace s inkoustem</span><span class="sxs-lookup"><span data-stu-id="6bba6-123">Manipulate Ink</span></span>

<span data-ttu-id="6bba6-124"><xref:System.Windows.Controls.InkCanvas> poskytuje podporu pro mnoho operací úpravy rukopisu.</span><span class="sxs-lookup"><span data-stu-id="6bba6-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="6bba6-125">Například <xref:System.Windows.Controls.InkCanvas> podporuje mazání zezadu a k přidání funkce do prvku není potřeba žádný další kód.</span><span class="sxs-lookup"><span data-stu-id="6bba6-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="6bba6-126">Výběr</span><span class="sxs-lookup"><span data-stu-id="6bba6-126">Selection</span></span>

<span data-ttu-id="6bba6-127">Nastavení režimu výběru je jednoduché, protože nastavení vlastnosti <xref:System.Windows.Controls.InkCanvasEditingMode> na hodnotu **Vybrat**.</span><span class="sxs-lookup"><span data-stu-id="6bba6-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="6bba6-128">Následující kód nastaví režim úprav na základě hodnoty <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="6bba6-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="6bba6-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="6bba6-129">DrawingAttributes</span></span>

<span data-ttu-id="6bba6-130">Chcete-li změnit vzhled tahů perem, použijte vlastnost <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bba6-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="6bba6-131">Například člen <xref:System.Windows.Ink.DrawingAttributes.Color%2A> <xref:System.Windows.Ink.DrawingAttributes> nastavuje barvu vykresleného <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="6bba6-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="6bba6-132">Následující příklad změní barvu vybraných tahů na červenou:</span><span class="sxs-lookup"><span data-stu-id="6bba6-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="6bba6-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="6bba6-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="6bba6-134">Vlastnost <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> poskytuje přístup k vlastnostem, jako je výška, Šířka a barva tahů, které mají být vytvořeny v <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="6bba6-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="6bba6-135">Po změně <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>jsou všechny budoucí tahy zadané do <xref:System.Windows.Controls.InkCanvas> vykresleny s novými hodnotami vlastností.</span><span class="sxs-lookup"><span data-stu-id="6bba6-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="6bba6-136">Kromě změny <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> v souboru kódu na pozadí lze použít syntaxi XAML pro určení <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>ch vlastností.</span><span class="sxs-lookup"><span data-stu-id="6bba6-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="6bba6-137">Další příklad ukazuje, jak nastavit vlastnost <xref:System.Windows.Ink.DrawingAttributes.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bba6-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="6bba6-138">Chcete-li použít tento kód, vytvořte nový projekt WPF nazvaný "HelloInkCanvas" v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6bba6-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="6bba6-139">Nahraďte kód v souboru *MainWindow. XAML* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="6bba6-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="6bba6-140">Dále přidejte následující obslužné rutiny událostí tlačítka do souboru kódu na pozadí uvnitř třídy MainWindow:</span><span class="sxs-lookup"><span data-stu-id="6bba6-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="6bba6-141">Po zkopírování tohoto kódu stiskněte klávesu **F5** v aplikaci Visual Studio a spusťte program v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="6bba6-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="6bba6-142">Všimněte si, jak <xref:System.Windows.Controls.StackPanel> umístí tlačítka nad <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="6bba6-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="6bba6-143">Pokud se pokusíte použít rukopis v horní části tlačítek, <xref:System.Windows.Controls.InkCanvas> shromažďuje a vykresluje rukopis za tlačítky.</span><span class="sxs-lookup"><span data-stu-id="6bba6-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="6bba6-144">Důvodem je to, že tlačítka jsou na stejné <xref:System.Windows.Controls.InkCanvas> na rozdíl od podřízených.</span><span class="sxs-lookup"><span data-stu-id="6bba6-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="6bba6-145">Tlačítka jsou také vyšší v pořadí vykreslování, takže rukopis je vykreslen za sebou.</span><span class="sxs-lookup"><span data-stu-id="6bba6-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bba6-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bba6-146">See also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
