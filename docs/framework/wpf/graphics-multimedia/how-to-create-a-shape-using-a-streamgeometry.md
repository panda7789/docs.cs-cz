---
title: 'Postupy: Vytvoření tvaru pomocí StreamGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: fd191e4cfdfa33c144389d4871a9641e9c811ed3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108599"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a><span data-ttu-id="55333-102">Postupy: Vytvoření tvaru pomocí StreamGeometry</span><span class="sxs-lookup"><span data-stu-id="55333-102">How to: Create a Shape Using a StreamGeometry</span></span>
<xref:System.Windows.Media.StreamGeometry> <span data-ttu-id="55333-103">odlehčené alternativu, která umožňuje <xref:System.Windows.Media.PathGeometry> pro vytvoření geometrické tvary.</span><span class="sxs-lookup"><span data-stu-id="55333-103">is light-weight alternative to <xref:System.Windows.Media.PathGeometry> for creating geometric shapes.</span></span> <span data-ttu-id="55333-104">Použití <xref:System.Windows.Media.StreamGeometry> když potřebujete k popisu komplexní geometry, ale nechcete, aby režii podporuje datové vazby, animace nebo úpravy.</span><span class="sxs-lookup"><span data-stu-id="55333-104">Use a <xref:System.Windows.Media.StreamGeometry> when you need to describe a complex geometry but do not want the overhead of supporting data binding, animation, or modification.</span></span> <span data-ttu-id="55333-105">Například z důvodu jeho efektivitu a <xref:System.Windows.Media.StreamGeometry> třídy je dobrou volbou pro popis doplňků pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="55333-105">For example, because of its efficiency, the <xref:System.Windows.Media.StreamGeometry> class is a good choice for describing adorners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55333-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="55333-106">Example</span></span>  
 <span data-ttu-id="55333-107">Následující příklad používá syntaxi atributů k vytvoření trojúhelníkové <xref:System.Windows.Media.StreamGeometry> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55333-107">The following example uses attribute syntax to create a triangular <xref:System.Windows.Media.StreamGeometry> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <span data-ttu-id="55333-108">Další informace o <xref:System.Windows.Media.StreamGeometry> atribut syntaxe, naleznete v tématu [syntaxe značek cesty](path-markup-syntax.md) stránky.</span><span class="sxs-lookup"><span data-stu-id="55333-108">For more information about <xref:System.Windows.Media.StreamGeometry> attribute syntax, see the [Path Markup Syntax](path-markup-syntax.md) page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55333-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="55333-109">Example</span></span>  
 <span data-ttu-id="55333-110">Následující příklad používá <xref:System.Windows.Media.StreamGeometry> k definování trojúhelník v kódu.</span><span class="sxs-lookup"><span data-stu-id="55333-110">The next example uses a <xref:System.Windows.Media.StreamGeometry> to define a triangle in code.</span></span> <span data-ttu-id="55333-111">Nejprve v příkladu se vytvoří <xref:System.Windows.Media.StreamGeometry>, pak získá <xref:System.Windows.Media.StreamGeometryContext> a použije ho k popisu trojúhelníku.</span><span class="sxs-lookup"><span data-stu-id="55333-111">First, the example creates a <xref:System.Windows.Media.StreamGeometry>, then obtains a <xref:System.Windows.Media.StreamGeometryContext> and uses it to describe the triangle.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="55333-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="55333-112">Example</span></span>  
 <span data-ttu-id="55333-113">Následující příklad vytvoří metodu, která se používá <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.StreamGeometryContext> k definování geometrické obrazce podle zadaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="55333-113">The next example creates a method that uses a <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.StreamGeometryContext> to define a geometric shape based on specified parameters.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="55333-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55333-114">See also</span></span>

- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [<span data-ttu-id="55333-115">Vytvoření tvaru pomocí PathGeometry</span><span class="sxs-lookup"><span data-stu-id="55333-115">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [<span data-ttu-id="55333-116">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="55333-116">Geometry Overview</span></span>](geometry-overview.md)
