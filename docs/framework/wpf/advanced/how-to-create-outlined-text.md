---
title: 'Postupy: Vytvoření obrysového textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: 237bdc097cd2a3fbfff6dd79bce401c2d091e211
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162225"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="53a8b-102">Postupy: Vytvoření obrysového textu</span><span class="sxs-lookup"><span data-stu-id="53a8b-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="53a8b-103">Ve většině případů při přidávání dekoru na textové řetězce do vaší [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace, používáte text z hlediska kolekce samostatných znaky nebo glyfů.</span><span class="sxs-lookup"><span data-stu-id="53a8b-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="53a8b-104">Například lze vytvořit štětec lineárního přechodu a použít ho k <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost <xref:System.Windows.Controls.TextBox> objektu.</span><span class="sxs-lookup"><span data-stu-id="53a8b-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="53a8b-105">Při zobrazení nebo upravte pole štětec lineárního přechodu se automaticky využije na aktuální sady znaků v textovém řetězci.</span><span class="sxs-lookup"><span data-stu-id="53a8b-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![Text zobrazený s štětec lineárního přechodu](./media/how-to-create-outlined-text/text-linear-gradient.jpg)    
  
 <span data-ttu-id="53a8b-107">Ale můžete také převést text do <xref:System.Windows.Media.Geometry> objektům, umožňuje vytvářet jiné druhy vizuálně formátovaný text.</span><span class="sxs-lookup"><span data-stu-id="53a8b-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="53a8b-108">Například můžete vytvořit <xref:System.Windows.Media.Geometry> objektu podle obrysu textového řetězce.</span><span class="sxs-lookup"><span data-stu-id="53a8b-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![Text osnovy pomocí štětec lineárního přechodu](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="53a8b-110">Pokud je text převést na <xref:System.Windows.Media.Geometry> objektu, není již sadu znaků – nelze upravit znaků v textovém řetězci.</span><span class="sxs-lookup"><span data-stu-id="53a8b-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="53a8b-111">Můžete však vliv na vzhled text převedený úpravou jeho vlastností tahu a výplně.</span><span class="sxs-lookup"><span data-stu-id="53a8b-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="53a8b-112">Protože byl zdvih odkazuje na osnovy převedený textu. Výplň odkazuje na oblast uvnitř osnovy text převedený.</span><span class="sxs-lookup"><span data-stu-id="53a8b-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="53a8b-113">Následující příklady znázorňují několik způsobů vytváření vizuálních efektů úpravou tahu a zadejte text převedený.</span><span class="sxs-lookup"><span data-stu-id="53a8b-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![Text mají různé barvy výplně a tahu](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Text použitý pro stroke obrázkový štětec](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="53a8b-116">Je také možné změnit ohraničující obdélník pole nebo zvýraznění převedeného textu.</span><span class="sxs-lookup"><span data-stu-id="53a8b-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="53a8b-117">Následující příklad ukazuje způsob, jak vytváření vizuálních efektů úpravou tahu a zvýraznit text převedený.</span><span class="sxs-lookup"><span data-stu-id="53a8b-117">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![Text s použita k obtažení a zvýraznit obrázkový štětec](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="53a8b-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="53a8b-119">Example</span></span>  
 <span data-ttu-id="53a8b-120">Klíč k převodu textu <xref:System.Windows.Media.Geometry> objektu je použití <xref:System.Windows.Media.FormattedText> objektu.</span><span class="sxs-lookup"><span data-stu-id="53a8b-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="53a8b-121">Po vytvoření tohoto objektu můžete použít <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> a <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metody pro převod textu na <xref:System.Windows.Media.Geometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="53a8b-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="53a8b-122">První metoda vrátí geometrie formátovaného textu. Druhá metoda vrátí geometrie formátovaný text ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="53a8b-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="53a8b-123">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Media.FormattedText> objektu a k načtení geometrie formátovaný text a jeho ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="53a8b-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="53a8b-124">Aby bylo možné zobrazit načtené <xref:System.Windows.Media.Geometry> objekty, budete potřebovat přístup k <xref:System.Windows.Media.DrawingContext> objektu, který zobrazuje text převedený.</span><span class="sxs-lookup"><span data-stu-id="53a8b-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="53a8b-125">V těchto příkladech kódu se provádí tak, že vytvoříte vlastní ovládací prvek objekt, který je odvozen ze třídy, která podporuje uživatelem definované vykreslování.</span><span class="sxs-lookup"><span data-stu-id="53a8b-125">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="53a8b-126">Chcete-li zobrazit <xref:System.Windows.Media.Geometry> objekty v ovládacím prvku vlastní poskytují přepsání pro <xref:System.Windows.UIElement.OnRender%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="53a8b-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="53a8b-127">Používejte přepsané metody <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> metody, chcete-li nakreslit <xref:System.Windows.Media.Geometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="53a8b-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="53a8b-128">Zdrojový objekt příklad vlastního uživatelského ovládacího prvku, naleznete v tématu [OutlineTextControl.cs pro C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) a [OutlineTextControl.vb v jazyce Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span><span class="sxs-lookup"><span data-stu-id="53a8b-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="53a8b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53a8b-129">See also</span></span>

- [<span data-ttu-id="53a8b-130">Kreslení formátovaného textu</span><span class="sxs-lookup"><span data-stu-id="53a8b-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
