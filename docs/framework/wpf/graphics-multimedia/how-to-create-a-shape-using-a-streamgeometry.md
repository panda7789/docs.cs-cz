---
title: "Postupy: Vytvoření tvaru použitím StreamGeometry"
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
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a333fd6c1906eaea2c8eaf2c3b07502b5a9c4d40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a>Postupy: Vytvoření tvaru použitím StreamGeometry
<xref:System.Windows.Media.StreamGeometry>šedé – alternativu, která umožňuje <xref:System.Windows.Media.PathGeometry> pro vytvoření geometrické obrazce. Použití <xref:System.Windows.Media.StreamGeometry> když potřebujete popisují komplexní geometry, ale nechcete, aby nároky na podporu vazby dat, animace nebo úpravy. Například z důvodu jeho efektivitu <xref:System.Windows.Media.StreamGeometry> třída je vhodná pro popisující ozdobného prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá syntaxi atributů k vytvoření trojúhelníkovou <xref:System.Windows.Media.StreamGeometry> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Další informace o <xref:System.Windows.Media.StreamGeometry> atribut syntaxi najdete [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.  
  
## <a name="example"></a>Příklad  
 Další příklad používá <xref:System.Windows.Media.StreamGeometry> k definování trojúhelník v kódu. Nejprve v příkladu se vytváří <xref:System.Windows.Media.StreamGeometry>, pak získává <xref:System.Windows.Media.StreamGeometryContext> a používá ho k popisu trojúhelníku.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Další příklad vytvoří metodu, která používá <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.StreamGeometryContext> k definování geometrické obrazce podle zadaných parametrů.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.StreamGeometryContext>  
 [Vytvoření tvaru pomocí PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
