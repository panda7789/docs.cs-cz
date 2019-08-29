---
title: Maximalizace výkonu WPF 3D
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: e1a90406423e36dd10b8b108e076fe73f99947f0
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133851"
---
# <a name="maximize-wpf-3d-performance"></a>Maximalizace výkonu WPF 3D
Při použití [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nástroje k sestavení 3D ovládacích prvků a zahrnutí 3D scén do aplikací je důležité zvážit optimalizaci výkonu. Toto téma obsahuje seznam 3D tříd a vlastností, které mají vliv na výkon aplikace, spolu s doporučeními pro optimalizaci výkonu při jejich použití.  
  
 Toto téma předpokládá pokročilé porozumění [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcím 3D. Návrhy v tomto dokumentu se vztahují na vrstvu vykreslování 2, která je přibližně definovaná jako hardware, který podporuje pixel shader verze 2,0 a vertex shader verze 2,0. Další podrobnosti najdete v tématu [vrstvy vykreslování grafiky](../advanced/graphics-rendering-tiers.md).  
  
## <a name="performance-impact-high"></a>Dopad na výkon: Vysoká  
  
|Vlastnost|Doporučení|  
|-|-|  
|<xref:System.Windows.Media.Brush>|Rychlost štětce (nejrychlejší až nejpomalejší):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>ukládán<br /><br /> <xref:System.Windows.Media.VisualBrush>ukládán<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>bez<br /><br /> <xref:System.Windows.Media.VisualBrush>bez|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|Nastavte `Viewport3D.ClipToBounds` na hodnotu false, kdykoli nemusíte [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vystřihnout obsah a <xref:System.Windows.Controls.Viewport3D> k obdélníku Viewport3D's. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oříznutí antialiasu může být velmi pomalé a `ClipToBounds` ve <xref:System.Windows.Controls.Viewport3D>výchozím nastavení je zapnuto (pomalé).|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|Nastavte `Viewport3D.IsHitTestVisible` na hodnotu false, kdykoli při provádění [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] testování myši nepotřebujete <xref:System.Windows.Controls.Viewport3D> vzít v úvahu obsah.  Testování přístupů 3D obsahu se provádí v softwaru a může být pomalé s velkými oky. <xref:System.Windows.UIElement.IsHitTestVisible%2A>je ve výchozím nastavení <xref:System.Windows.Controls.Viewport3D>zapnuté (pomalé).|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|Vytvořte různé modely pouze v případě, že vyžadují různé materiály nebo transformace.  V opačném případě se pokuste <xref:System.Windows.Media.Media3D.GeometryModel3D> o sloučení velkého počtu instancí se stejnými materiály a Transformujte je <xref:System.Windows.Media.Media3D.GeometryModel3D> do <xref:System.Windows.Media.Media3D.MeshGeometry3D> několika větších a instancí.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Animace snímků – Změna jednotlivých vrcholů sítě na základě jednotlivých snímků – není vždy efektivní v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Chcete-li minimalizovat dopad na výkon oznámení o změně při změně každého vrcholu, odpojte síť od vizuálního stromu před provedením úpravy podle vrcholu.  Po úpravě sítě ji znovu připojte ke vizuálnímu stromu.  Také se pokuste minimalizovat velikost sítí, které budou tímto způsobem animovány.|  
|3D antialiasing|Chcete-li zvýšit rychlost vykreslování, zakažte u <xref:System.Windows.Controls.Viewport3D> nástroje více vzorkování nastavením připojené <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> vlastnosti `Aliased`na.  Ve výchozím nastavení je ve Windows s 4 ukázkami na pixel povolený prostorový antialiasing.|  
|Text|Živý text ve 3D scéně (živý, protože je v <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush>) může být pomalý. Místo toho zkuste použít obrázky textu (přes <xref:System.Windows.Media.Imaging.RenderTargetBitmap>), pokud se text nemění.|  
|<xref:System.Windows.Media.TileBrush>|<xref:System.Windows.Media.VisualBrush> Pokud je nutné použít <xref:System.Windows.Media.DrawingBrush> nebo ve 3D scéně, protože obsah štětce není statický, zkuste stopu štětce (nastavení připojené vlastnosti <xref:System.Windows.Media.RenderOptions.CachingHint%2A> na `Cache`) do mezipaměti.  Nastavte prahové hodnoty minimálního a maximálního počtu neplatných pro horizontální <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> navýšení kapacity (s připojenými vlastnostmi a <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>), aby se štětce v mezipaměti znovu negenerovaly příliš často, a přitom udržují požadovanou úroveň kvality.  Ve výchozím nastavení <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush> nejsou ukládány do mezipaměti, což znamená, že pokaždé, když se vykreslí se štětcem, musí být nejprve znovu vykreslen celý obsah štětce na mezilehlého povrchu.|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect>vynutí vygenerování veškerého ovlivněného obsahu bez hardwarové akcelerace.  Nejlepšího výkonu dosáhnete, když <xref:System.Windows.Media.Effects.BitmapEffect>nepoužíváte.|  
  
## <a name="performance-impact-medium"></a>Dopad na výkon: Střední  
  
|Vlastnost|Doporučení|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Když je síť definovaná jako sousedící trojúhelníky se sdílenými vrcholy a tyto vrcholy mají stejné souřadnice pozice, normální a textury, definujte každý sdílený vrchol jenom jednou a pak definujte trojúhelníky podle indexu pomocí <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>.|  
|<xref:System.Windows.Media.ImageBrush>|Zkuste minimalizovat velikosti textury, když máte explicitní kontrolu nad velikostí (Pokud používáte <xref:System.Windows.Media.Imaging.RenderTargetBitmap> a/ <xref:System.Windows.Media.ImageBrush>nebo).  Všimněte si, že nižší textury rozlišení můžou snížit kvalitu vizuálů, takže se snažte najít správnou rovnováhu mezi kvalitou a výkonem.|  
|Míra průhlednosti|Při vykreslování průsvitného 3D obsahu (například reflektování) použijte vlastnosti neprůhlednosti na štětce nebo materiálech <xref:System.Windows.Media.Brush.Opacity%2A> ( <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>prostřednictvím nebo) místo vytvoření samostatného <xref:System.Windows.Controls.Viewport3D> průsvitného `Viewport3D.Opacity` nastavením na hodnotu menší než 1.|  
|<xref:System.Windows.Controls.Viewport3D>|Minimalizujte počet <xref:System.Windows.Controls.Viewport3D> objektů, které používáte ve scéně.  Místo vytváření samostatných instancí objektu Viewport3D pro každý model vložte mnoho 3D modelů do stejného objektu Viewport3D.|  
|<xref:System.Windows.Freezable>|Obvykle je výhodné znovu použít <xref:System.Windows.Media.Media3D.MeshGeometry3D>, <xref:System.Windows.Media.Media3D.GeometryModel3D>štětce a materiály.  Všechny mají více nadřazených objektů, protože jsou odvozeny z `Freezable`.|  
|<xref:System.Windows.Freezable>|<xref:System.Windows.Freezable.Freeze%2A> Volejte metodu na zablokovatelné, když jejich vlastnosti zůstanou ve vaší aplikaci beze změny.  Zmrazení může snížit pracovní sadu a zvýšit rychlost.|  
|<xref:System.Windows.Media.Brush>|Použijte <xref:System.Windows.Media.ImageBrush> místonebo<xref:System.Windows.Media.DrawingBrush>, Pokud se obsah štětce nezmění. <xref:System.Windows.Media.VisualBrush>  2D obsah se dá převést na <xref:System.Windows.Controls.Image> Via <xref:System.Windows.Media.Imaging.RenderTargetBitmap> <xref:System.Windows.Media.ImageBrush>a pak se použije v.|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|Nepoužívejte <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> , pokud skutečně nepotřebujete vidět zadní plošky vašeho <xref:System.Windows.Media.Media3D.GeometryModel3D>.|  
|<xref:System.Windows.Media.Media3D.Light>|Rychlost světla (nejrychlejší až nejpomalejší):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Snažte se zachovat velikost ok v těchto mezích:<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: instance <xref:System.Windows.Media.Media3D.Point3D> 20 001<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: instance <xref:System.Int32> 60 003|  
|<xref:System.Windows.Media.Media3D.Material>|Rychlost materiálu (nejrychlejší až nejpomalejší):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D nesouhlasí s neviditelnými štětci (černé okolní štětce, jasné štětce atd.) konzistentním způsobem.  Zvažte jejich vynechání z scény.|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|<xref:System.Windows.Media.Media3D.Material> Každá<xref:System.Windows.Media.Media3D.MaterialGroup> z těchto příčin způsobí další vykreslování, takže včetně mnoha materiálů, dokonce i jednoduchých materiálů, může výrazně zvýšit nároky na procesor GPU.  Minimalizujte počet materiálů v <xref:System.Windows.Media.Media3D.MaterialGroup>.|  
  
## <a name="performance-impact-low"></a>Dopad na výkon: Nízká  
  
|Vlastnost|Doporučení|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|Pokud nepotřebujete animaci nebo datovou vazbu, namísto použití skupiny transformace obsahující více transformací, použijte jeden <xref:System.Windows.Media.Media3D.MatrixTransform3D>, který nastaví jako součin všech transformací, které by jinak existovaly nezávisle ve skupině transformací.|  
|<xref:System.Windows.Media.Media3D.Light>|Minimalizujte počet světel ve scéně. Příliš mnoho světel ve scéně vynutí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vrácení softwaru k vykreslování.  Limity jsou zhruba 110 <xref:System.Windows.Media.Media3D.DirectionalLight> objekty, 70 <xref:System.Windows.Media.Media3D.PointLight> objekty nebo 40 <xref:System.Windows.Media.Media3D.SpotLight> objekty.|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|Oddělte přesunutí objektů ze statických objektů jejich vložením <xref:System.Windows.Media.Media3D.ModelVisual3D> do samostatných instancí.  ModelVisual3D je "těžší" <xref:System.Windows.Media.Media3D.GeometryModel3D> , protože ukládá do mezipaměti transformované meze.  GeometryModel3D je optimalizovaná tak, aby byla modelem; ModelVisual3D je optimalizovaná tak, aby byla uzlem scény.  Pomocí ModelVisual3D umístěte sdílené instance GeometryModel3D do scény.|  
|<xref:System.Windows.Media.Media3D.Light>|Minimalizujte počet světel na scéně.  Každá změna počtu světla vynutí vygenerování a rekompilaci shaderu, pokud tato konfigurace ještě nebyla dříve (a proto má shader uložený v mezipaměti).|  
|Hlediska|Černé indikátory nebudou viditelné, ale budou přidány do času vykreslování; Zvažte jejich vynechání.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Chcete-li minimalizovat dobu vytváření velkých kolekcí v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]nástroji, jako je například <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>MeshGeometry3D's <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>,, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>a, před naplnění hodnot kolekcí předem velikost kolekce. Pokud je to možné, předejte konstruktory Collections předem vyplněné datové struktury, jako jsou pole nebo seznamy.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled 3D grafiky](3-d-graphics-overview.md)
