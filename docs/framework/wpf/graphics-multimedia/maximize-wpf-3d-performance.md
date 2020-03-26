---
title: Maximalizace 3D výkonu
ms.date: 03/30/2017
helpviewer_keywords:
- 3D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 3825ea8e57c6863e2ee654072efda623db21c2a8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111995"
---
# <a name="maximize-wpf-3d-performance"></a>Maximalizace výkonu WPF 3D
Při vytváření [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D ovládacích prvků a zahrnutí 3D scén do aplikací je důležité zvážit optimalizaci výkonu. Toto téma obsahuje seznam 3D tříd a vlastností, které mají vliv na výkon pro vaši aplikaci, spolu s doporučeními pro optimalizaci výkonu při jejich použití.  
  
 Toto téma předpokládá pokročilé [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pochopení 3D funkcí. Návrhy v tomto dokumentu platí pro "vykreslovací úroveň 2" – zhruba definované jako hardware, který podporuje pixel shader verze 2.0 a vertex shader verze 2.0. Další podrobnosti naleznete [v tématu Úrovně vykreslování grafiky](../advanced/graphics-rendering-tiers.md).  
  
## <a name="performance-impact-high"></a>Dopad na výkon: Vysoká  
  
|Vlastnost|Doporučení|  
|-|-|  
|<xref:System.Windows.Media.Brush>|Rychlost štětce (nejrychlejší až nejpomalejší):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>(uloženo v mezipaměti)<br /><br /> <xref:System.Windows.Media.VisualBrush>(uloženo v mezipaměti)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>(bez mezipaměti)<br /><br /> <xref:System.Windows.Media.VisualBrush>(bez mezipaměti)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|Nastavte `Viewport3D.ClipToBounds` na hodnotu false vždy, když nepotřebujete explicitně [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oříznout obsah a <xref:System.Windows.Controls.Viewport3D> do obdélníku Viewport3D. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ořezvek vyhlazeného může být `ClipToBounds` velmi pomalý a je <xref:System.Windows.Controls.Viewport3D>ve výchozím nastavení povolen (pomalý) na .|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|Nastavte `Viewport3D.IsHitTestVisible` na false vždy, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] když není nutné <xref:System.Windows.Controls.Viewport3D> zvážit obsah při provádění testování přístupů myší.  Hit testování 3D obsahu se provádí v softwaru a může být pomalé s velkými sítěmi. <xref:System.Windows.UIElement.IsHitTestVisible%2A>je ve výchozím nastavení <xref:System.Windows.Controls.Viewport3D>zapnuta (pomalu) zapnutá .|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|Různé modely můžete vytvářet pouze v případě, že vyžadují různé materiály nebo transformace.  V opačném případě se pokuste sloužovat mnoho <xref:System.Windows.Media.Media3D.GeometryModel3D> instancí <xref:System.Windows.Media.Media3D.GeometryModel3D> se <xref:System.Windows.Media.Media3D.MeshGeometry3D> stejnými materiály a transformuje do několika větších a instancí.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Animace sítě – změna jednotlivých vrcholů sítě na základě jednotlivých snímků [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]– není vždy efektivní .  Chcete-li minimalizovat dopad oznámení o změně při změně každého vrcholu, odpojte síť od vizuálního stromu před provedením úpravy na vrchol.  Po úpravě sítě ji znovu připojte ke vizuálnímu stromu.  Také se snaží minimalizovat velikost ok, které budou animovány tímto způsobem.|  
|3D vyhlazení|Chcete-li zvýšit rychlost vykreslování, zakažte vícenásobné vzorkování na a <xref:System.Windows.Controls.Viewport3D> nastavením připojené vlastnosti <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> na `Aliased`.  Ve výchozím nastavení je 3D vymýšlé zprávy v systému Windows povoleny se 4 vzorky na pixel.|  
|Text|Živý text ve 3D scéně (živý, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>protože je v nebo ) může být pomalý. Zkuste místo toho použít obrázky <xref:System.Windows.Media.Imaging.RenderTargetBitmap>textu (přes) , pokud se text nezmění.|  
|<xref:System.Windows.Media.TileBrush>|Pokud musíte použít <xref:System.Windows.Media.VisualBrush> a <xref:System.Windows.Media.DrawingBrush> nebo a ve 3D scéně, protože obsah stopy není statický, zkuste <xref:System.Windows.Media.RenderOptions.CachingHint%2A> `Cache`štětec uložit do mezipaměti (nastavení připojené vlastnosti).  Nastavte minimální a maximální prahové hodnoty zneplatnění měřítka (s připojenými vlastnostmi <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> a <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>) tak, aby stopy štětce uložené v mezipaměti nebyly regenerovány příliš často a přitom si zachovaly požadovanou úroveň kvality.  Ve výchozím <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush> nastavení a nejsou uloženy do mezipaměti, což znamená, že pokaždé, když něco malované s štětcem musí být re-rendered, celý obsah stopy musí být nejprve re-rendered na mezilehlý povrch.|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect>vynutí vykreslení veškerého ovlivněného obsahu bez hardwarové akcelerace.  Chcete-li dosáhnout nejlepšího výkonu, nepoužívejte <xref:System.Windows.Media.Effects.BitmapEffect>.|  
  
## <a name="performance-impact-medium"></a>Dopad na výkon: Střední  
  
|Vlastnost|Doporučení|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Pokud je síť definována jako sousedící trojúhelníky se sdílenými vrcholy a tyto vrcholy mají stejnou polohu, normální a souřadnice textury, definujte každý sdílený vrchol pouze jednou a pak definujte trojúhelníky podle indexu pomocí . <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>|  
|<xref:System.Windows.Media.ImageBrush>|Pokuste se minimalizovat velikosti textur, pokud máte explicitní kontrolu <xref:System.Windows.Media.Imaging.RenderTargetBitmap> nad velikostí <xref:System.Windows.Media.ImageBrush>(při použití a/nebo).  Všimněte si, že textury s nižším rozlišením mohou snížit vizuální kvalitu, proto se pokuste najít správnou rovnováhu mezi kvalitou a výkonem.|  
|Krytí|Při vykreslování průsvitného 3D obsahu (například odrazů) <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>použijte vlastnosti krytí na <xref:System.Windows.Controls.Viewport3D> stopách nebo materiálech (přes <xref:System.Windows.Media.Brush.Opacity%2A> nebo ) namísto vytvoření samostatného průsvitného nastavením `Viewport3D.Opacity` na hodnotu menší než 1.|  
|<xref:System.Windows.Controls.Viewport3D>|Minimalizujte počet <xref:System.Windows.Controls.Viewport3D> objektů, které ve scéně používáte.  Místo vytváření samostatných instancí Viewport3D pro každý model vložte mnoho 3D modelů do stejného viewportu3D.|  
|<xref:System.Windows.Freezable>|Obvykle je výhodné znovu použít <xref:System.Windows.Media.Media3D.MeshGeometry3D> <xref:System.Windows.Media.Media3D.GeometryModel3D>, , kartáče a materiály.  Všechny jsou multiparentable, protože jsou `Freezable`odvozeny z .|  
|<xref:System.Windows.Freezable>|Volání <xref:System.Windows.Freezable.Freeze%2A> metody freezables při jejich vlastnosti zůstanou beze změny ve vaší aplikaci.  Zmrazení může snížit pracovní sadu a zvýšit rychlost.|  
|<xref:System.Windows.Media.Brush>|Použijte <xref:System.Windows.Media.ImageBrush> místo <xref:System.Windows.Media.VisualBrush> <xref:System.Windows.Media.DrawingBrush> nebo když se obsah stopy nezmění.  2D obsah lze převést <xref:System.Windows.Controls.Image> <xref:System.Windows.Media.Imaging.RenderTargetBitmap> na via a <xref:System.Windows.Media.ImageBrush>poté použít v .|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|Nepoužívejte, <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> pokud skutečně potřebujete vidět zadní tváře <xref:System.Windows.Media.Media3D.GeometryModel3D>vašeho .|  
|<xref:System.Windows.Media.Media3D.Light>|Rychlost světla (nejrychlejší až nejpomalejší):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Snažte se zachovat velikosti sítí pod těmito omezeními:<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20 001 <xref:System.Windows.Media.Media3D.Point3D> instancí<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60 003 <xref:System.Int32> instancí|  
|<xref:System.Windows.Media.Media3D.Material>|Rychlost materiálu (nejrychlejší až nejpomalejší):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D neodhlásí neviditelné štětce (černé okolní kartáče, čiré kartáče atd.) konzistentním způsobem.  Zvažte vynechání těchto z vaší scény.|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|Každý <xref:System.Windows.Media.Media3D.Material> v <xref:System.Windows.Media.Media3D.MaterialGroup> důsledku způsobuje další renderovací průchod, takže včetně mnoha materiálů, dokonce i jednoduchých materiálů, může dramaticky zvýšit požadavky na plnění vašeho GPU.  Minimalizujte počet materiálů <xref:System.Windows.Media.Media3D.MaterialGroup>ve vašem .|  
  
## <a name="performance-impact-low"></a>Dopad na výkon: Nízká  
  
|Vlastnost|Doporučení|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|Pokud nepotřebujete animaci nebo datovou vazbu, namísto použití skupiny <xref:System.Windows.Media.Media3D.MatrixTransform3D>transformace obsahující více transformací použijte jednu , nastavíte ji tak, aby byla součinem všech transformací, které by jinak existovaly nezávisle ve skupině transformace.|  
|<xref:System.Windows.Media.Media3D.Light>|Minimalizujte počet světel ve scéně. Příliš mnoho světel ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] scéně bude nutit k pádu zpět do vykreslování softwaru.  Omezení jsou zhruba 110 <xref:System.Windows.Media.Media3D.DirectionalLight> objektů, 70 <xref:System.Windows.Media.Media3D.PointLight> <xref:System.Windows.Media.Media3D.SpotLight> objektů nebo 40 objektů.|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|Oddělte pohybující se objekty <xref:System.Windows.Media.Media3D.ModelVisual3D> od statických objektů jejich umístěním do samostatných instancí.  ModelVisual3D je "těžší", <xref:System.Windows.Media.Media3D.GeometryModel3D> než proto, že ukládá transformované hranice.  GeometryModel3D je optimalizován a model; ModelVisual3D je optimalizován tak, aby byl uzel scény.  ModelVisual3D slouží k tomu, aby sdílené instance GeometryModel3D do scény.|  
|<xref:System.Windows.Media.Media3D.Light>|Minimalizujte počet změn počtu světel ve scéně.  Každá změna počtu světla vynutí regeneraci a rekompilaci shaderu, pokud tato konfigurace neexistovala dříve (a tedy měla svůj shader uložen v mezipaměti).|  
|Světlý|Černá světla nebudou viditelná, ale zvýší čas vykreslení; zvážit jejich vynechání.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Chcete-li minimalizovat dobu výstavby velkých kolekcí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]v , <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>jako <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>je <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>například MeshGeometry3D , , a , pre-size kolekce před hodnotou plnění. Pokud je to možné, předajte předem vyplněné datové struktury kolekcí, jako jsou pole nebo Seznamy.|  
  
## <a name="see-also"></a>Viz také

- [Přehled 3D grafiky](3-d-graphics-overview.md)
