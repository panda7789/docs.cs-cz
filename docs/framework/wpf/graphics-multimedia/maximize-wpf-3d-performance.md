---
title: Maximalizace 3D výkonu
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 414a4677a1e05cd69c382e35194328d6ce1bddf9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744594"
---
# <a name="maximize-wpf-3d-performance"></a>Maximalizace výkonu WPF 3D
Při použití [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] k sestavování 3D ovládacích prvků a zahrnutí 3D scén do aplikací je důležité zvážit optimalizaci výkonu. Toto téma obsahuje seznam 3D tříd a vlastností, které mají vliv na výkon aplikace, spolu s doporučeními pro optimalizaci výkonu při jejich použití.  
  
 Toto téma předpokládá pokročilé porozumění funkcím [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D. Návrhy v tomto dokumentu se vztahují na vrstvu vykreslování 2, která je přibližně definovaná jako hardware, který podporuje pixel shader verze 2,0 a vertex shader verze 2,0. Další podrobnosti najdete v tématu [vrstvy vykreslování grafiky](../advanced/graphics-rendering-tiers.md).  
  
## <a name="performance-impact-high"></a>Dopad na výkon: vysoký  
  
|Vlastnost|Doporučení|  
|-|-|  
|<xref:System.Windows.Media.Brush>|Rychlost štětce (nejrychlejší až nejpomalejší):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> (Uloženo v mezipaměti)<br /><br /> <xref:System.Windows.Media.VisualBrush> (Uloženo v mezipaměti)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> (neuložené do mezipaměti)<br /><br /> <xref:System.Windows.Media.VisualBrush> (neuložené do mezipaměti)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|Nastavte `Viewport3D.ClipToBounds` na hodnotu false, pokud nepotřebujete [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] výslovně vystřihnout obsah <xref:System.Windows.Controls.Viewport3D> k obdélníku Viewport3D's. oříznutí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] antialiasů může být velmi pomalé a ve výchozím nastavení je povolená `ClipToBounds` (pomalé) na <xref:System.Windows.Controls.Viewport3D>.|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|Nastavte `Viewport3D.IsHitTestVisible` na hodnotu false, kdykoli nepotřebujete [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] při provádění testování úspěšnosti myši zvážit obsah <xref:System.Windows.Controls.Viewport3D>.  Testování přístupů 3D obsahu se provádí v softwaru a může být pomalé s velkými oky. ve výchozím nastavení je ve <xref:System.Windows.Controls.Viewport3D>povolená <xref:System.Windows.UIElement.IsHitTestVisible%2A> (pomalé).|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|Vytvořte různé modely pouze v případě, že vyžadují různé materiály nebo transformace.  V opačném případě se snažte přidružit mnoho instancí <xref:System.Windows.Media.Media3D.GeometryModel3D> ke stejným materiálům a transformovat je do několika větších <xref:System.Windows.Media.Media3D.GeometryModel3D> a instancí <xref:System.Windows.Media.Media3D.MeshGeometry3D>.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Animace snímků – Změna jednotlivých vrcholů sítě na základě jednotlivých snímků – není vždy efektivní v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Chcete-li minimalizovat dopad na výkon oznámení o změně při změně každého vrcholu, odpojte síť od vizuálního stromu před provedením úpravy podle vrcholu.  Po úpravě sítě ji znovu připojte ke vizuálnímu stromu.  Také se pokuste minimalizovat velikost sítí, které budou tímto způsobem animovány.|  
|3D antialiasing|Chcete-li zvýšit rychlost vykreslování, zakažte více vzorkování na <xref:System.Windows.Controls.Viewport3D> nastavením vlastnosti připojené <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> na `Aliased`.  Ve výchozím nastavení je ve Windows s 4 ukázkami na pixel povolený prostorový antialiasing.|  
|Text|Živý text ve 3D scéně (živě, protože je v <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush>) může být pomalý. Místo toho zkuste použít obrázky textu (prostřednictvím <xref:System.Windows.Media.Imaging.RenderTargetBitmap>), pokud se text nemění.|  
|<xref:System.Windows.Media.TileBrush>|Pokud je nutné použít <xref:System.Windows.Media.VisualBrush> nebo <xref:System.Windows.Media.DrawingBrush> ve 3D scéně, protože obsah štětce není statický, zkuste stopu štětce (nastavení připojené vlastnosti <xref:System.Windows.Media.RenderOptions.CachingHint%2A> na `Cache`).  Nastavte minimální a maximální prahové hodnoty pro neplatné škálování (s připojenými vlastnostmi <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> a <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>) tak, aby se štětce v mezipaměti negenerovaly příliš často, a přitom udržují požadovanou úroveň kvality.  Ve výchozím nastavení se <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush> neukládají do mezipaměti, což znamená, že pokaždé, když se vykreslí se štětcem, musí se nejdřív znovu vykreslovat celý obsah štětce na mezilehlou plochu.|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect> vynutí vygenerování veškerého ovlivněného obsahu bez hardwarové akcelerace.  Pro nejlepší výkon nepoužívejte <xref:System.Windows.Media.Effects.BitmapEffect>.|  
  
## <a name="performance-impact-medium"></a>Dopad na výkon: střední  
  
|Vlastnost|Doporučení|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Když je síť definovaná jako sousedící trojúhelníky se sdílenými vrcholy a tyto vrcholy mají stejné souřadnice pozice, normální a textury, definujte každý sdílený vrchol jenom jednou a pak definujte trojúhelníky podle indexu s <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>.|  
|<xref:System.Windows.Media.ImageBrush>|Snažte se minimalizovat velikosti textury, když máte explicitní kontrolu nad velikostí (Pokud používáte <xref:System.Windows.Media.Imaging.RenderTargetBitmap> a/nebo <xref:System.Windows.Media.ImageBrush>).  Všimněte si, že nižší textury rozlišení můžou snížit kvalitu vizuálů, takže se snažte najít správnou rovnováhu mezi kvalitou a výkonem.|  
|Míra průhlednosti|Při vykreslování průsvitného 3D obsahu (například reflektování) použijte vlastnosti neprůhlednosti na štětce nebo materiálech (prostřednictvím <xref:System.Windows.Media.Brush.Opacity%2A> nebo <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>) místo vytvoření samostatného průsvitného <xref:System.Windows.Controls.Viewport3D> nastavením `Viewport3D.Opacity` na hodnotu menší než 1.|  
|<xref:System.Windows.Controls.Viewport3D>|Minimalizujte počet <xref:System.Windows.Controls.Viewport3D> objektů, které používáte ve scéně.  Místo vytváření samostatných instancí objektu Viewport3D pro každý model vložte mnoho 3D modelů do stejného objektu Viewport3D.|  
|<xref:System.Windows.Freezable>|Obvykle je výhodné znovu použít <xref:System.Windows.Media.Media3D.MeshGeometry3D>, <xref:System.Windows.Media.Media3D.GeometryModel3D>, štětce a materiály.  Všechny mají více nadřazených objektů, protože jsou odvozeny z `Freezable`.|  
|<xref:System.Windows.Freezable>|Volání metody <xref:System.Windows.Freezable.Freeze%2A> v Zablokovatelné, pokud jejich vlastnosti zůstanou ve vaší aplikaci beze změny.  Zmrazení může snížit pracovní sadu a zvýšit rychlost.|  
|<xref:System.Windows.Media.Brush>|Pokud se obsah štětce nezmění, použijte místo <xref:System.Windows.Media.VisualBrush> nebo <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.ImageBrush>.  2D obsah se dá převést na <xref:System.Windows.Controls.Image> přes <xref:System.Windows.Media.Imaging.RenderTargetBitmap> a pak se používá v <xref:System.Windows.Media.ImageBrush>.|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|Nepoužívejte <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>, pokud skutečně nepotřebujete vidět zadní plošky vašeho <xref:System.Windows.Media.Media3D.GeometryModel3D>.|  
|<xref:System.Windows.Media.Media3D.Light>|Rychlost světla (nejrychlejší až nejpomalejší):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Snažte se zachovat velikost ok v těchto mezích:<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20 001 <xref:System.Windows.Media.Media3D.Point3D> instancí<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60 003 <xref:System.Int32> instancí|  
|<xref:System.Windows.Media.Media3D.Material>|Rychlost materiálu (nejrychlejší až nejpomalejší):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D neodkazují na neviditelné štětce (černé okolní štětce, Clear štětce atd.) konzistentním způsobem.  Zvažte jejich vynechání z scény.|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|Každý <xref:System.Windows.Media.Media3D.Material> v <xref:System.Windows.Media.Media3D.MaterialGroup> způsobuje další průchod vykreslování, takže včetně mnoha materiálů, dokonce i jednoduchých materiálů, může výrazně zvýšit nároky na výplň GPU.  Minimalizujte počet materiálů v <xref:System.Windows.Media.Media3D.MaterialGroup>.|  
  
## <a name="performance-impact-low"></a>Dopad na výkon: nízká  
  
|Vlastnost|Doporučení|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|Pokud nepotřebujete animaci nebo datovou vazbu, místo použití skupiny transformace obsahující více transformací, použijte jeden <xref:System.Windows.Media.Media3D.MatrixTransform3D>, nastavení této vlastnosti na produkt pro všechny transformace, které by jinak existovaly nezávisle ve skupině transformací.|  
|<xref:System.Windows.Media.Media3D.Light>|Minimalizujte počet světel ve scéně. Příliš mnoho světel ve scéně vynutí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vrátit se k softwarovému vykreslování.  Limity jsou zhruba 110 <xref:System.Windows.Media.Media3D.DirectionalLight> objektů, 70 <xref:System.Windows.Media.Media3D.PointLight> objektů nebo 40 <xref:System.Windows.Media.Media3D.SpotLight> objektů.|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|Oddělte objekty ze statických objektů jejich vložením do samostatných instancí <xref:System.Windows.Media.Media3D.ModelVisual3D>.  ModelVisual3D je "těžší" než <xref:System.Windows.Media.Media3D.GeometryModel3D>, protože ukládá do mezipaměti transformované meze.  GeometryModel3D je optimalizovaná tak, aby byla modelem; ModelVisual3D je optimalizovaná tak, aby byla uzlem scény.  Pomocí ModelVisual3D umístěte sdílené instance GeometryModel3D do scény.|  
|<xref:System.Windows.Media.Media3D.Light>|Minimalizujte počet světel na scéně.  Každá změna počtu světla vynutí vygenerování a rekompilaci shaderu, pokud tato konfigurace ještě nebyla dříve (a proto má shader uložený v mezipaměti).|  
|Hlediska|Černé indikátory nebudou viditelné, ale budou přidány do času vykreslování; Zvažte jejich vynechání.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Aby se minimalizovala doba vytváření velkých kolekcí v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], jako je například MeshGeometry3D's <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>a <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>, před naplnění hodnot kolekcí před hodnotou. Pokud je to možné, předejte konstruktory Collections předem vyplněné datové struktury, jako jsou pole nebo seznamy.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled 3D grafiky](3-d-graphics-overview.md)
