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
ms.openlocfilehash: ce2097568349ad376540163f5fe05d6a3e5b0643
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348033"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a>Postupy: Vytvoření tvaru pomocí StreamGeometry
<xref:System.Windows.Media.StreamGeometry> zjednodušené alternativu, která umožňuje <xref:System.Windows.Media.PathGeometry> pro vytvoření geometrické tvary. Použití <xref:System.Windows.Media.StreamGeometry> když potřebujete k popisu komplexní geometry, ale nechcete, aby režii podporuje datové vazby, animace nebo úpravy. Například z důvodu jeho efektivitu a <xref:System.Windows.Media.StreamGeometry> třídy je dobrou volbou pro popis doplňků pro úpravy.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá syntaxi atributů k vytvoření trojúhelníkové <xref:System.Windows.Media.StreamGeometry> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Další informace o <xref:System.Windows.Media.StreamGeometry> atribut syntaxe, naleznete v tématu [syntaxe značek cesty](path-markup-syntax.md) stránky.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.StreamGeometry> k definování trojúhelník v kódu. Nejprve v příkladu se vytvoří <xref:System.Windows.Media.StreamGeometry>, pak získá <xref:System.Windows.Media.StreamGeometryContext> a použije ho k popisu trojúhelníku.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří metodu, která se používá <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.StreamGeometryContext> k definování geometrické obrazce podle zadaných parametrů.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [Vytvoření tvaru pomocí PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [Přehled geometrie](geometry-overview.md)
