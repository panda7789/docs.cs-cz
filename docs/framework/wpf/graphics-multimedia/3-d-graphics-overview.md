---
title: Přehled 3D grafiky
description: Seznamte se s 3D grafikou v Windows Presentation Foundation (WPF) k vykreslování, transformaci a animování 3D grafiky v kódu i v procedurálním kódu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 51da6a1ed6d5e98b99c64ee23be52f7b2385897f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853878"
---
# <a name="3d-graphics-overview"></a>Přehled 3D grafiky
<a name="introduction"></a>3D funkce v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umožňuje vývojářům kreslit, transformovat a animovat 3D grafiku v kódu i v procedurálním kódu. Vývojáři mohou kombinovat 2D a 3D grafiku a vytvářet bohatý ovládací prvky, poskytovat komplexní ilustrace dat nebo zvyšovat uživatelské prostředí rozhraní aplikace. Prostorová podpora v nástroji není [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] navržena tak, aby poskytovala plnohodnotnou platformu pro vývoj her. V tomto tématu najdete přehled 3D funkcí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafickém systému.  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>3D v 2D kontejneru  
 obsah 3D grafiky v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je zapouzdřen v prvku, který se <xref:System.Windows.Controls.Viewport3D> může účastnit struktury dvojrozměrného prvku. Grafický systém se považuje <xref:System.Windows.Controls.Viewport3D> za dvourozměrný vizuální prvek, například mnoho dalších v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . <xref:System.Windows.Controls.Viewport3D>funguje jako okno – zobrazení – do trojrozměrné scény. Přesněji platí, že se jedná o povrch, na kterém je 3D scéna v projekci.  
  
 V konvenční 2D aplikaci použijte <xref:System.Windows.Controls.Viewport3D> jako jiný kontejnerový prvek jako Grid nebo plátno.  I když můžete použít <xref:System.Windows.Controls.Viewport3D> s jinými 2D nakreslenými objekty ve stejném grafu scény, nemůžete proniknout 2D a 3D objekty v rámci <xref:System.Windows.Controls.Viewport3D> .  Toto téma se zaměřuje na vykreslení 3D grafiky uvnitř <xref:System.Windows.Controls.Viewport3D> .  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>Prostor souřadnic 3D  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Systém souřadnic pro 2D grafiku vyhledá počátek v levém horním rohu oblasti vykreslování (obvykle obrazovky). V 2D systému budou kladné hodnoty osy x pokračovat směrem dolů a kladné hodnoty osy y.  V 3D souřadnicovém systému je však počátek umístěn ve středu oblasti vykreslování, přičemž kladné hodnoty osy x přejdou na pravé, ale kladné hodnoty osy y budou pokračovat směrem nahoru a kladné hodnoty z osy z od počátku, směrem k prohlížeči.  
  
 ![Systémy souřadnic](./media/coordsystem-1.png "CoordSystem-1")  
Konvenční reprezentace 2D a 3D souřadnic systému  
  
 Prostor definovaný těmito osami je stacionární rámec reference pro 3D objekty v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Při sestavování modelů v tomto prostoru a vytváření světel a fotoaparátů k jejich zobrazení je užitečné rozlišovat tento stacionární rámec odkazů nebo "světové místo" z místního rámce odkazu, který vytvoříte pro každý model při použití transformací. Mějte na paměti, že objekty ve světě můžou vypadat úplně jinak nebo vůbec nemusejí být viditelné, v závislosti na nastaveních světla a kamery, ale poloha kamery nemění umístění objektů v prostoru světa.  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>Kamery a projekce  
 Vývojáři, kteří pracují v 2D, jsou zvyklí umístit primitivní prvky vykreslování na dvojrozměrné obrazovce. Při vytváření 3D scény je důležité si uvědomit, že opravdu vytváříte 2D reprezentace 3D objektů. Vzhledem k tomu, že se 3D scéna liší v závislosti na místě zobrazení onlooker, musíte určit, že se jedná o daný bod zobrazení. <xref:System.Windows.Media.Media3D.Camera>Třída umožňuje zadat tento pohled na 3D scénu.  
  
 Dalším způsobem, jak porozumět tomu, jak se 3D scéna znázorňuje na 2D povrchu, je popisem scény jako projekce na zobrazovací plochu. <xref:System.Windows.Media.Media3D.ProjectionCamera>Umožňuje zadat různé projekce a jejich vlastnosti, abyste změnili způsob, jakým se onlooker uvidí 3D modely. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> Určuje projekci, která foreshortens scénu.  Jinými slovy, <xref:System.Windows.Media.Media3D.PerspectiveCamera> nabízí perspektivu pro Úběžný bod.  Můžete určit polohu kamery v prostoru souřadnic scény, směru a poli zobrazení kamery a vektor, který definuje směr "nahoru" ve scéně. Následující diagram znázorňuje <xref:System.Windows.Media.Media3D.PerspectiveCamera> projekci.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>Vlastnosti a <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> <xref:System.Windows.Media.Media3D.ProjectionCamera> omezují rozsah projekce kamery. Vzhledem k tomu, že kamery můžou být umístěné kdekoli na scéně, je možné, že fotoaparát bude ve skutečnosti umístěný v modelu nebo v blízkosti modelu a tím je obtížné odlišit objekty správně.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>umožňuje zadat minimální vzdálenost od fotoaparátu, po které se objekty nebudou vykreslovat.  V opačném případě <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> vám umožní určit vzdálenost od kamery, po které se objekty nebudou vykreslovat, což zajistí, že se do scény nezahrne objekty příliš daleko, které by bylo možné rozpoznat.  
  
 ![Nastavení kamery](./media/coordsystem-6.png "CoordSystem – 6")  
Pozice kamery  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>Určuje kolmou projekci 3D model na 2D vizuální povrch. Podobně jako jiné kamery Určuje polohu, směr zobrazení a směr směrem nahoru. Na rozdíl od <xref:System.Windows.Media.Media3D.PerspectiveCamera> , ale <xref:System.Windows.Media.Media3D.OrthographicCamera> popisuje projekci, která nezahrnuje perspektivy foreshortening. Jinými slovy, <xref:System.Windows.Media.Media3D.OrthographicCamera> popisuje zobrazované pole, jehož strany jsou rovnoběžné, místo toho, jehož strany jsou v určitém bodě kamery. Následující obrázek znázorňuje stejný model jako při prohlížení pomocí <xref:System.Windows.Media.Media3D.PerspectiveCamera> a <xref:System.Windows.Media.Media3D.OrthographicCamera> .  
  
 ![Pravoúhle a perspektiva – projekce](./media/camera-projections4.png "Camera_projections4")  
Perspektivy a pravoúhle projekce  
  
 Následující kód ukazuje několik typických nastavení kamery.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>Primitivní modely a sítě  
  
 <xref:System.Windows.Media.Media3D.Model3D>je abstraktní základní třída, která představuje obecný 3D objekt. Chcete-li vytvořit 3D scénu, potřebujete některé objekty zobrazit a objekty, které tvoří graf scény, jsou odvozeny z <xref:System.Windows.Media.Media3D.Model3D> . V současné době [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje modelování geometrií s <xref:System.Windows.Media.Media3D.GeometryModel3D> . <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>Vlastnost tohoto modelu používá primitivní mřížku.  
  
 Chcete-li vytvořit model, Začněte vytvořením primitivní neboli sítě. Trojrozměrné primitivum je kolekce vrcholů, které tvoří jednu 3D entitu. Většina 3D systémů poskytuje primitivní modely modelované na nejjednodušším uzavřeném obrázku: trojúhelník definovaný třemi vrcholy.  Vzhledem k tomu, že se tři body trojúhelníku coplanar, můžete pokračovat v přidávání trojúhelníků, aby bylo možné modelovat složitější tvary s názvem sítě.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Prostorový systém v současné době poskytuje <xref:System.Windows.Media.Media3D.MeshGeometry3D> třídu, která umožňuje určit libovolnou geometrii. aktuálně nepodporuje předdefinované trojrozměrné primitivní prvky, jako jsou koule a krychlové formuláře. Začněte vytvářet <xref:System.Windows.Media.Media3D.MeshGeometry3D> pomocí zadáním seznamu trojúhelníkových vrcholů jako své <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> Vlastnosti. Každý vrchol je určen jako <xref:System.Windows.Media.Media3D.Point3D> .  (V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] zadejte tuto vlastnost jako seznam čísel seskupených ve třech, které reprezentují souřadnice každého vrcholu.) V závislosti na jeho geometrii může být vaše síť tvořená mnoha trojúhelníky, některé z nich sdílejí stejné rohy (vrcholy). Aby bylo možné správně vykreslit síť, jsou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] potřebné informace o tom, které vrcholy sdílí trojúhelníky. Tyto informace zadáte tak, že zadáte seznam trojúhelníkových indexů s <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> vlastností. Tento seznam určuje pořadí, ve kterém budou body zadané v <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu určovat trojúhelník.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 V předchozím příkladu obsahuje <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznam osm vrcholů pro definování sítě ve tvaru krychle. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>Vlastnost určuje seznam dvanáct skupin tří indexů.  Každé číslo v seznamu odkazuje na posun do <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu.  Například první tři vrcholy zadané v <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu jsou (1, 1, 0), (0, 1, 0) a (0, 0, 0). První tři indexy zadané v <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> seznamu jsou 0, 2 a 1, které odpovídají prvnímu, třetímu a druhému bodu v <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu. V důsledku toho se první trojúhelník, který tvoří model datové krychle, skládá z (1, 1, 0) na (0, 1, 0) do (0, 0, 0) a zbývající jedenácté trojúhelníky budou určeny podobně.  
  
 Můžete pokračovat v definování modelu zadáním hodnot <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> vlastností a.  Aby bylo možné vykreslit plochu modelu, grafický systém potřebuje informace o tom, jaký směr je na Surface na daném trojúhelníku. Tyto informace používá k provedení výpočtů světla pro model: povrchy, které čelí přímému zdroji světla, se jeví jako jasnější, než jsou šikmé od světla. I když [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lze určit výchozí normální vektory pomocí souřadnic pozice, můžete také zadat jiné normální vektory, aby bylo možné přibližně navýšit vzhled zakřivených ploch.  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>Vlastnost určuje kolekci <xref:System.Windows.Point> s, která sděluje grafickému systému, jak namapovat souřadnice, které určují, jak se textura vykresluje na vrcholy sítě. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>jsou zadány jako hodnota mezi 0 a 1 včetně.  Stejně jako u <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> vlastnosti může systém grafiky vypočítat výchozí souřadnice textury, ale můžete zvolit, aby bylo možné nastavit jiné souřadnice textury pro řízení mapování textury, která obsahuje část opakujícího se vzoru, například. Další informace o souřadnicích textury najdete v následujících tématech nebo ve spravované sadě Direct3D SDK.  
  
 Následující příklad ukazuje, jak vytvořit jednu plošku modelu datové krychle v procedurálním kódu. Celou datovou krychli můžete vykreslit jako jeden GeometryModel3D; Tento příklad nakreslí vzhled datové krychle jako odlišný model, aby bylo možné použít samostatné textury na každou plošku později.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>Použití materiálů pro model  
  
 Aby síť vypadala jako trojrozměrného objektu, musí mít použitou texturu pro pokrytí povrchu definovaného jeho vrcholy a trojúhelníky, aby bylo možné je rozsvítit a promítnout fotoaparátem. V 2D použijete <xref:System.Windows.Media.Brush> třídu pro Aplikování barev, vzorů, přechodů nebo jiných vizuálních obsahu na oblasti obrazovky.  Vzhled 3D objektů je však funkce modelu osvětlení, nikoli pouze barva nebo vzor aplikovaný na ně. Reálné objekty odrážejí světlo odlišně v závislosti na kvalitě jejich povrchu: lesklé a lesklé povrchy se neshodují stejně jako hrubou nebo podkladovou rovinu a některé objekty se jeví jako absorbované, zatímco jiné záři. Můžete použít všechny stejné štětce na 3D objekty, které lze použít na 2D objekty, ale nemůžete je přímo použít.  
  
 Chcete-li definovat charakteristiky povrchu modelu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá <xref:System.Windows.Media.Media3D.Material> abstraktní třídu. Konkrétní podtřídy materiálu určují některé charakteristiky vzhledu povrchu modelu a každá z nich také poskytuje vlastnost štětce, ke které můžete předat SolidColorBrush, TileBrush nebo VisualBrush.  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>Určuje, že se má v modelu použít štětec, jako kdyby byl model osvětlen difúzně. Použití DiffuseMaterial se podobá použití štětců přímo na 2D modelech; modelové povrchy nereflektují světlo, i když je lesklý.  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>Určuje, že se má v modelu použít štětec, jako kdyby byl povrch modelu pevný nebo lesklý, schopný odrážet světla. Můžete nastavit míru, pro kterou bude textura navrhovat tuto reflektování kvality, nebo "září" zadáním hodnoty <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> Vlastnosti.  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>umožňuje určit, že textura bude použita, jako kdyby model vygeneroval světlo, který se rovná barvě štětce. To nevede k tomu, že model má světlo; bude se ale podílet odlišně při stínování, než by bylo v případě textury s DiffuseMaterial nebo SpecularMaterial.  
  
 Pro zajištění lepšího výkonu <xref:System.Windows.Media.Media3D.GeometryModel3D> se z scény odfiltrují zadní plochy a (tyto plošky, které jsou mimo zobrazení, protože jsou na protější straně modelu z kamery).  Chcete-li určit, že se má <xref:System.Windows.Media.Media3D.Material> použít pro zadní plochu modelu, jako je rovina, nastavte <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> vlastnost modelu.  
  
 Chcete-li dosáhnout některé kvality povrchu, například záři nebo odrazný efekt, můžete použít několik různých štětců na model po sobě. Můžete použít a znovu použít více materiálů pomocí <xref:System.Windows.Media.Media3D.MaterialGroup> třídy. Podřízené objekty ve vlastnictví se aplikují nejdříve na poslední v několika průchodech vykreslování.  
  
 Následující příklady kódu ukazují, jak použít jednobarevné barvy a kresby jako štětce na 3D modely.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>Osvětlení scény  
 Světla v 3D grafice působí v reálném světě, kde jsou indikátory ve skutečném světě: vytvářejí povrchy. Čím více je bod, světla určí, jaká část scény bude součástí projekce. Světlé objekty v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytváření nejrůznějších efektů světla a stínu a jsou modelovány po chování různých indikátorů reálného světa. Do scény zahrňte aspoň jedno světlo, jinak se nezobrazí žádné modely.  
  
 Následující světla jsou odvozena ze základní třídy <xref:System.Windows.Media.Media3D.Light> :  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: Poskytuje okolní osvětlení, které rozsvítí všechny objekty jednotně bez ohledu na jejich umístění nebo orientaci.  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: Osvětlení jako u vzdáleného světelného zdroje.  Směrové světla mají <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> zadanou hodnotu Vector3D, ale žádné zadané umístění.  
  
- <xref:System.Windows.Media.Media3D.PointLight>: Osvětlení jako okolní zdroj světla. PointLights má z této pozice světlo pozice a přetypování. Objekty ve scéně jsou osvětlené v závislosti na poloze a vzdálenosti vzhledem k světlosti. <xref:System.Windows.Media.Media3D.PointLightBase>zpřístupňuje <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> vlastnost, která určuje vzdálenost nad tím, které modely nebudou osvětleny světlo. PointLight také zpřístupňuje vlastnosti pro zeslabení, které určují, jak se intenzita světla v průběhu vzdálenosti sníží. Pro zeslabení světla můžete zadat konstantní, lineární nebo kvadratické interpolace.  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: Dědí z <xref:System.Windows.Media.Media3D.PointLight> . Svítí světla jako PointLight a mají jak polohu, tak směr. Vysvětlují projektové světlo v oblasti nastavené na kužele <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> a <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> vlastnosti určené ve stupních.  
  
 Světla jsou <xref:System.Windows.Media.Media3D.Model3D> objekty, takže můžete transformovat a animovat světlé vlastnosti, včetně pozice, barvy, směru a rozsahu.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>Transformace modelů  
 Při vytváření modelů mají příslušné umístění na scéně. Chcete-li přesunout tyto modely v rámci scény, pro jejich otočení nebo změnu velikosti, není praktické měnit vrcholy, které definují samotné modely.  Místo toho můžete použít transformace na modely, stejně jako v 2D.  
  
 Každý objekt modelu má <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> vlastnost, která umožňuje přesunout, změnit orientaci nebo změnit velikost modelu.  Když aplikujete transformaci, efektivně posunete všechny body modelu podle libovolného vektoru nebo hodnoty určené transformací. Jinými slovy jste převedli souřadnicový prostor, ve kterém je model definován ("prostor modelu"), ale nezměnili jste hodnoty, které tvoří geometrii modelu v souřadnicovém systému celé scény ("World Space").  
  
 Další informace o transformaci modelů najdete v tématu [Přehled 3D transformací](3-d-transformations-overview.md).  
  
<a name="animations"></a>
## <a name="animating-models"></a>Animace modelů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3D implementace se účastní stejného časového a animačního systému jako 2D grafika. Jinými slovy, pokud chcete animovat 3D scénu, animovat vlastnosti svých modelů. Je možné animovat vlastnosti primitivních primitiv přímo, ale obvykle je snazší animovat transformace, které mění polohu nebo vzhled modelů. Vzhledem k tomu, že transformace lze použít na <xref:System.Windows.Media.Media3D.Model3DGroup> objekty a také na jednotlivé modely, je možné použít jednu sadu animací na podřízenou položku Model3DGroup a další sadu animací na skupinu podřízených objektů. Pomocí animovaných vlastností osvětlení scény můžete také dosáhnout nejrůznějších vizuálních efektů. Nakonec můžete zvolit animaci samotné projekce tím, že animujete polohu kamery nebo pole zobrazení. Základní informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] časových a animačních systémech najdete v tématech [Přehled animace](animation-overview.md), [Přehled scénářů](storyboards-overview.md)a [Freezable objektů – přehled](../advanced/freezable-objects-overview.md) .  
  
 Chcete-li animovat objekt v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , vytvořte časovou osu, definujte animaci (což je skutečně Změna v určité hodnotě vlastnosti v čase) a určete vlastnost, pro kterou chcete animaci použít. Vzhledem k tomu, že všechny objekty ve 3D scéně jsou podřízenými položkami <xref:System.Windows.Controls.Viewport3D> , jsou vlastnosti, které jsou cílem jakékoli animace, kterou chcete použít na scénu, vlastnosti objektu Viewport3D.  
  
 Předpokládejme, že chcete vytvořit model, který se Wobble na místě. Můžete se rozhodnout použít <xref:System.Windows.Media.Media3D.RotateTransform3D> pro model a animovat osu jeho rotace z jednoho vektoru na druhý. Následující příklad kódu ukazuje použití Vector3DAnimation na vlastnost Axis Rotation3D transformace, za předpokladu, že RotateTransform3D je jedním z několika transformací aplikovaných na model s transformací.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3d-content-to-the-window"></a>Přidání 3D obsahu do okna  
 Pro vykreslení scény přidejte modely a světla do a <xref:System.Windows.Media.Media3D.Model3DGroup> pak nastavte <xref:System.Windows.Media.Media3D.Model3DGroup> jako <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> <xref:System.Windows.Media.Media3D.ModelVisual3D> . Přidejte <xref:System.Windows.Media.Media3D.ModelVisual3D> do <xref:System.Windows.Controls.Viewport3D.Children%2A> kolekce <xref:System.Windows.Controls.Viewport3D> . Přidejte kamery do rozhraní <xref:System.Windows.Controls.Viewport3D> nastavením jeho <xref:System.Windows.Controls.Viewport3D.Camera%2A> Vlastnosti.  
  
 Nakonec přidejte <xref:System.Windows.Controls.Viewport3D> do okna. Když <xref:System.Windows.Controls.Viewport3D> je zahrnutý jako obsah prvku rozložení, jako je plátno, určete velikost objektu Viewport3D nastavením <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> vlastností a vlastností (zděděných z <xref:System.Windows.FrameworkElement> ).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [Přehled 3D transformací](3-d-transformations-overview.md)
- [Maximalizace výkonu WPF 3D](maximize-wpf-3d-performance.md)
- [– postupy](3-d-graphics-how-to-topics.md)
- [Tvary a základní kresby v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Kreslení pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
