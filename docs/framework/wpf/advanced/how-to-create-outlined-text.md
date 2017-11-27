---
title: "Postupy: Vytvoření textu osnovy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76d0dcf63f9d8a66106f4bcdc52a2bf98c75cdc4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="fa4fd-102">Postupy: Vytvoření textu osnovy</span><span class="sxs-lookup"><span data-stu-id="fa4fd-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="fa4fd-103">Ve většině případů při přidávání dekoru na textové řetězce ve vaší [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace, používáte text z hlediska kolekci diskrétní znaků nebo glyfů.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="fa4fd-104">Můžete například vytvořit lineární štětce přechodu a použijte ho k <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost <xref:System.Windows.Controls.TextBox> objektu.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="fa4fd-105">Při zobrazení nebo upravte pole, lineární štětce přechodu automaticky použita pro aktuální sadu znaků v textovém řetězci.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 <span data-ttu-id="fa4fd-106">![Text zobrazovaný štětcem lineárního přechodu](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span><span class="sxs-lookup"><span data-stu-id="fa4fd-106">![Text displayed with a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span></span>  
<span data-ttu-id="fa4fd-107">Příklad lineární štětce přechodu použít textového pole</span><span class="sxs-lookup"><span data-stu-id="fa4fd-107">Example of a linear gradient brush applied to a text box</span></span>  
  
 <span data-ttu-id="fa4fd-108">Ale můžete také převést text do <xref:System.Windows.Media.Geometry> objekty, umožňuje vytvářet jiné typy vizuálně formátovaným textem.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-108">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="fa4fd-109">Například můžete vytvořit <xref:System.Windows.Media.Geometry> objektu podle obrys textového řetězce.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-109">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 <span data-ttu-id="fa4fd-110">![Osnova text použití štětce přechodu lineární](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span><span class="sxs-lookup"><span data-stu-id="fa4fd-110">![Text outline using a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span></span>  
<span data-ttu-id="fa4fd-111">Příklad lineární štětce přechodu u geometrie osnovy textu</span><span class="sxs-lookup"><span data-stu-id="fa4fd-111">Example of a linear gradient brush applied to the outline geometry of text</span></span>  
  
 <span data-ttu-id="fa4fd-112">Když se text bude převeden na <xref:System.Windows.Media.Geometry> objektu je již kolekce znaků – nelze upravit znaků v textovém řetězci.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-112">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="fa4fd-113">Však může ovlivnit vzhled text převedený změnou vlastností tahu a výplně.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-113">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="fa4fd-114">Tahu odkazuje na obrys text převedený; výplně odkazuje na oblasti uvnitř obrys text převedený.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-114">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="fa4fd-115">Následující příklady znázorňují několika způsoby vytváření vizuálních efektů úpravou tahu a výplně převedený textu.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-115">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 <span data-ttu-id="fa4fd-116">![Text pomocí různých barev pro výplně a tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span><span class="sxs-lookup"><span data-stu-id="fa4fd-116">![Text with different colors for fill and stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span></span>  
<span data-ttu-id="fa4fd-117">Příklad nastavení tahu a vyplňte pro různé barev</span><span class="sxs-lookup"><span data-stu-id="fa4fd-117">Example of setting stroke and fill to different colors</span></span>  
  
 <span data-ttu-id="fa4fd-118">![Text s štětce bitové kopie u tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span><span class="sxs-lookup"><span data-stu-id="fa4fd-118">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span></span>  
<span data-ttu-id="fa4fd-119">Příklad štětce bitové kopie u tahu</span><span class="sxs-lookup"><span data-stu-id="fa4fd-119">Example of an image brush applied to the stroke</span></span>  
  
 <span data-ttu-id="fa4fd-120">Je také možné upravit ohraničující obdélník pole nebo zvýraznění převedený textu.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-120">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="fa4fd-121">Následující příklad ilustruje způsob, jak vytváření vizuálních efektů úpravou tahu a zvýraznění převedený textu.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-121">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 <span data-ttu-id="fa4fd-122">![Text s štětce bitové kopie u tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span><span class="sxs-lookup"><span data-stu-id="fa4fd-122">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span></span>  
<span data-ttu-id="fa4fd-123">Příklad štětce obrázku použita pro tahu a zvýraznění</span><span class="sxs-lookup"><span data-stu-id="fa4fd-123">Example of an image brush applied to the stroke and highlight</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa4fd-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa4fd-124">Example</span></span>  
 <span data-ttu-id="fa4fd-125">Klíč k převodu text, který má <xref:System.Windows.Media.Geometry> objekt, je použít <xref:System.Windows.Media.FormattedText> objektu.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-125">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="fa4fd-126">Po vytvoření tohoto objektu, můžete použít <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> a <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metody pro převod textu na <xref:System.Windows.Media.Geometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-126">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="fa4fd-127">Vrátí první metoda geometrie formátovaný text; Druhá metoda vrátí že geometrie formátovaného textu je ohraničujícího pole.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-127">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="fa4fd-128">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Media.FormattedText> objektu a k načítání geometrie formátovaného textu a jeho ohraničující pole.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-128">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="fa4fd-129">Aby bylo možné zobrazit načtený <xref:System.Windows.Media.Geometry> objekty, je třeba získat přístup <xref:System.Windows.Media.DrawingContext> objektu, který je zobrazení převedeného textového.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-129">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="fa4fd-130">V těchto příkladech, kódu se provádí tak, že vytvoříte vlastní ovládací prvek objekt, který je odvozen od třídy, která podporuje vlastní vykreslení.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-130">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="fa4fd-131">Chcete-li zobrazit <xref:System.Windows.Media.Geometry> objekty v ovládacím prvku vlastní poskytují přepsání pro <xref:System.Windows.UIElement.OnRender%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-131">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="fa4fd-132">Přepsaná metoda by měla použít <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> metoda kreslení <xref:System.Windows.Media.Geometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="fa4fd-132">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a><span data-ttu-id="fa4fd-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa4fd-133">See Also</span></span>  
 [<span data-ttu-id="fa4fd-134">Kreslení formátovaného textu</span><span class="sxs-lookup"><span data-stu-id="fa4fd-134">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
