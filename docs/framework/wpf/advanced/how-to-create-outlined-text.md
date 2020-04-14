---
title: 'Postupy: Vytvoření textu osnovy'
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
ms.openlocfilehash: 86bfa396a2aa44eb511c014687501d60e170a396
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278922"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="b3278-102">Postup: Vytvoření textu s obrysy</span><span class="sxs-lookup"><span data-stu-id="b3278-102">How to: Create outlined text</span></span>

<span data-ttu-id="b3278-103">Ve většině případů při přidávání ozdoby do textových řetězců v aplikaci [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] používáte text z hlediska kolekce samostatných znaků nebo glyfů.</span><span class="sxs-lookup"><span data-stu-id="b3278-103">In most cases, when you're adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="b3278-104">Můžete například vytvořit stopu lineárního přechodu <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.TextBox> aplikovat ji na vlastnost objektu.</span><span class="sxs-lookup"><span data-stu-id="b3278-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="b3278-105">Když zobrazíte nebo upravíte textové pole, stopa lineárního přechodu se automaticky aplikuje na aktuální sadu znaků v textovém řetězci.</span><span class="sxs-lookup"><span data-stu-id="b3278-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![Text zobrazený s lineární modře přechodem](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 <span data-ttu-id="b3278-107">Můžete však také převést text na <xref:System.Windows.Media.Geometry> objekty, což vám umožní vytvářet další typy vizuálně bohatého textu.</span><span class="sxs-lookup"><span data-stu-id="b3278-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="b3278-108">Můžete například vytvořit <xref:System.Windows.Media.Geometry> objekt založený na obrysu textového řetězce.</span><span class="sxs-lookup"><span data-stu-id="b3278-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![Obrys textu pomocí stopy lineárního přechodu](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="b3278-110">Když je text převeden <xref:System.Windows.Media.Geometry> na objekt, už se nejedná o kolekci znaků – znaky v textovém řetězci nelze měnit.</span><span class="sxs-lookup"><span data-stu-id="b3278-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="b3278-111">Vzhled převedeného textu však můžete ovlivnit úpravou jeho vlastností tahu a výplně.</span><span class="sxs-lookup"><span data-stu-id="b3278-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="b3278-112">Tah odkazuje na obrys převedeného textu; výplň odkazuje na oblast uvnitř obrysu převedeného textu.</span><span class="sxs-lookup"><span data-stu-id="b3278-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="b3278-113">Následující příklady ilustrují několik způsobů vytváření vizuálních efektů úpravou tahu a výplně převedeného textu.</span><span class="sxs-lookup"><span data-stu-id="b3278-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![Text s různými barvami pro výplň a tah](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Text s obrazovou stopou aplikovanou na tah](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="b3278-116">Je také možné upravit obdélník ohraničovacího rámečku nebo zvýraznění převedeného textu.</span><span class="sxs-lookup"><span data-stu-id="b3278-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="b3278-117">Následující příklad ilustruje způsob, jak vytvořit vizuální efekty úpravou tahu a zvýraznění převedeného textu.</span><span class="sxs-lookup"><span data-stu-id="b3278-117">The following example illustrates a way to create visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![Text s obrazovou stopou aplikovanou na tah a zvýraznění](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="b3278-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3278-119">Example</span></span>  
 <span data-ttu-id="b3278-120">Klíčem k převodu textu <xref:System.Windows.Media.Geometry> na objekt <xref:System.Windows.Media.FormattedText> je použití objektu.</span><span class="sxs-lookup"><span data-stu-id="b3278-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="b3278-121">Po vytvoření tohoto objektu můžete <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> použít <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metody a k <xref:System.Windows.Media.Geometry> převodu textu na objekty.</span><span class="sxs-lookup"><span data-stu-id="b3278-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="b3278-122">První metoda vrátí geometrii formátovaného textu; druhá metoda vrátí geometrii ohraničovacího rámečku formátovaného textu.</span><span class="sxs-lookup"><span data-stu-id="b3278-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="b3278-123">Následující příklad kódu ukazuje, <xref:System.Windows.Media.FormattedText> jak vytvořit objekt a načíst geometrie formátovaného textu a jeho ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="b3278-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="b3278-124">Chcete-li zobrazit načtené <xref:System.Windows.Media.Geometry> objekty, musíte <xref:System.Windows.Media.DrawingContext> získat přístup k objektu, který zobrazuje převedený text.</span><span class="sxs-lookup"><span data-stu-id="b3278-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that's displaying the converted text.</span></span> <span data-ttu-id="b3278-125">V těchto příkladech kódu je tento přístup dosažen vytvořením vlastního objektu ovládacího prvku, který je odvozen z třídy, která podporuje uživatelem definované vykreslování.</span><span class="sxs-lookup"><span data-stu-id="b3278-125">In these code examples, this access is achieved by creating a custom control object that's derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="b3278-126">Chcete-li zobrazit <xref:System.Windows.Media.Geometry> objekty ve vlastním ovládacím prvku, zadejte přepsání <xref:System.Windows.UIElement.OnRender%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b3278-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="b3278-127">Vaše potlačená metoda <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> by měla <xref:System.Windows.Media.Geometry> použít metodu k nakreslení objektů.</span><span class="sxs-lookup"><span data-stu-id="b3278-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="b3278-128">Zdroj ukázkového objektu vlastního uživatelského ovládacího prvku naleznete [v tématu OutlineTextControl.cs pro c#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) a [outlineTextControl.vb pro jazyk Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span><span class="sxs-lookup"><span data-stu-id="b3278-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b3278-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3278-129">See also</span></span>

- [<span data-ttu-id="b3278-130">Kreslení formátovaného textu</span><span class="sxs-lookup"><span data-stu-id="b3278-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
