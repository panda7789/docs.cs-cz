---
title: Vytvoření komplexní mřížky
description: Příklad, jak používat ovládací prvek mřížky vytvořit rozložení, který vypadá jako měsíční kalendář.
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: e2356113457e8c9a6737132e9779e49c05a23d77
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149780"
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="7b1d9-103">Vytvoření komplexní mřížky</span><span class="sxs-lookup"><span data-stu-id="7b1d9-103">How to create a complex Grid</span></span>

<span data-ttu-id="7b1d9-104">Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.Grid> ovládacího prvku k vytvoření rozložení, který vypadá jako měsíční kalendář.</span><span class="sxs-lookup"><span data-stu-id="7b1d9-104">This example shows how to use a <xref:System.Windows.Controls.Grid> control to create a layout that looks like a monthly calendar.</span></span>

## <a name="example"></a><span data-ttu-id="7b1d9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b1d9-105">Example</span></span>

<span data-ttu-id="7b1d9-106">Následující příklad definuje osm řádků a sloupců osm pomocí <xref:System.Windows.Controls.RowDefinition> a <xref:System.Windows.Controls.ColumnDefinition> třídy.</span><span class="sxs-lookup"><span data-stu-id="7b1d9-106">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="7b1d9-107">Používá <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> připojených vlastností, spolu s <xref:System.Windows.Shapes.Rectangle> elementy, které vyplnit pozadí různých sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="7b1d9-107">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="7b1d9-108">Tento návrh je možné, protože v každá buňka může existovat více než jeden prvek <xref:System.Windows.Controls.Grid>, hlavní rozdíl mezi <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Documents.Table>.</span><span class="sxs-lookup"><span data-stu-id="7b1d9-108">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>

<span data-ttu-id="7b1d9-109">V příkladu je použit svislá přechody do <xref:System.Windows.Shapes.Shape.Fill%2A> sloupců a řádků ke zlepšení čitelnosti kalendáře a vizuální prezentace.</span><span class="sxs-lookup"><span data-stu-id="7b1d9-109">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="7b1d9-110">Styl <xref:System.Windows.Controls.TextBlock> elementy reprezentují data a dny v týdnu.</span><span class="sxs-lookup"><span data-stu-id="7b1d9-110">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="7b1d9-111"><xref:System.Windows.Controls.TextBlock> prvky jsou absolutně umístěné v rámci jejich buňky pomocí <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti a vlastnosti zarovnání, které jsou definované ve stylu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7b1d9-111"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>

[!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

<span data-ttu-id="7b1d9-112">Následující obrázek ukazuje výsledný ovládací prvek, přizpůsobitelné kalendáře:</span><span class="sxs-lookup"><span data-stu-id="7b1d9-112">The following image shows the resulting control, a customizable calendar:</span></span>

![Snímek obrazovky výsledný ovládací prvek](./media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a><span data-ttu-id="7b1d9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b1d9-114">See also</span></span>

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [<span data-ttu-id="7b1d9-115">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="7b1d9-115">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="7b1d9-116">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="7b1d9-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="7b1d9-117">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="7b1d9-117">Table Overview</span></span>](../advanced/table-overview.md)