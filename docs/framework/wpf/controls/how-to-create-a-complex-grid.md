---
title: "Postupy: Vytvoření komplexní mřížky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9dfb913407622f3cbd9a067a94cc6400b501e2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="aa2b1-102">Postupy: Vytvoření komplexní mřížky</span><span class="sxs-lookup"><span data-stu-id="aa2b1-102">How to: Create a Complex Grid</span></span>
<span data-ttu-id="aa2b1-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Controls.Grid> pro vytvoření rozložení, který může vypadat měsíční kalendář.</span><span class="sxs-lookup"><span data-stu-id="aa2b1-103">This example shows how to use a <xref:System.Windows.Controls.Grid> to create layout that looks like a monthly calendar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa2b1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa2b1-104">Example</span></span>  
 <span data-ttu-id="aa2b1-105">V následujícím příkladu definuje osm řádků a sloupců osm pomocí <xref:System.Windows.Controls.RowDefinition> a <xref:System.Windows.Controls.ColumnDefinition> třídy.</span><span class="sxs-lookup"><span data-stu-id="aa2b1-105">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="aa2b1-106">Použije <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> přidružené vlastnosti, společně s <xref:System.Windows.Shapes.Rectangle> prvky, které výplně pozadí různých sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="aa2b1-106">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="aa2b1-107">Tento návrh je možné, protože může existovat více než jeden element v jednotlivých buněk <xref:System.Windows.Controls.Grid>, Princip rozdíl mezi <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Documents.Table>.</span><span class="sxs-lookup"><span data-stu-id="aa2b1-107">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>  
  
 <span data-ttu-id="aa2b1-108">Tento příklad používá přechody vertikální k <xref:System.Windows.Shapes.Shape.Fill%2A> sloupců a řádků za účelem zlepšení vizuální prezentaci a čitelnost kalendáře.</span><span class="sxs-lookup"><span data-stu-id="aa2b1-108">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows in order to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="aa2b1-109">Ve <xref:System.Windows.Controls.TextBlock> elementy reprezentují kalendářních dat a dny v týdnu.</span><span class="sxs-lookup"><span data-stu-id="aa2b1-109">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="aa2b1-110"><xref:System.Windows.Controls.TextBlock>elementy jsou absolutně umístěny v rámci své buňky pomocí <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost a zarovnání vlastnosti, které jsou definovány v rámci styl pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aa2b1-110"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="aa2b1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa2b1-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [<span data-ttu-id="aa2b1-112">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="aa2b1-112">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="aa2b1-113">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="aa2b1-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="aa2b1-114">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="aa2b1-114">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
