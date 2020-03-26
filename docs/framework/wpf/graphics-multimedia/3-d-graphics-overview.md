---
title: Přehled 3D grafiky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: e4918f7737bbe57a4f29c6c5cff1099f4f21674b
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291809"
---
# <a name="3d-graphics-overview"></a>Přehled 3D grafiky
<a name="introduction"></a>Funkce 3D umožňuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vývojářům kreslit, transformovat a animovat 3D grafiku v kódu značek i procedurálního kódu. Vývojáři mohou kombinovat 2D a 3D grafiku a vytvářet tak bohaté ovládací prvky, poskytovat složité ilustrace dat nebo vylepšovat uživatelské prostředí rozhraní aplikace. 3D podpora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v oblasti není navržena tak, aby poskytovala plnohodnotnou platformu pro vývoj her. Toto téma obsahuje přehled 3D [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcí v grafickém systému.  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>3D ve 2D kontejneru  
 Obsah 3D [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafiky v aplikaci je <xref:System.Windows.Controls.Viewport3D>zapouzdřen v elementu , který se může účastnit dvourozměrné struktury prvků. Grafický systém zachází <xref:System.Windows.Controls.Viewport3D> jako dvou-dimenzionální vizuální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]prvek, stejně jako mnoho jiných v . <xref:System.Windows.Controls.Viewport3D>funguje jako okno – výřez – do trojrozměrné scény. Přesněji řečeno, je to povrch, na kterém je promítána 3D scéna.  
  
 V konvenční 2D aplikaci použijte <xref:System.Windows.Controls.Viewport3D> jako jiný prvek kontejneru, jako je Grid nebo Canvas.  I když <xref:System.Windows.Controls.Viewport3D> můžete použít s jinými 2D nakreslenými objekty ve stejném grafu <xref:System.Windows.Controls.Viewport3D>scény, nelze interproniknout 2D a 3D objekty v rámci .  Toto téma se zaměří na to, <xref:System.Windows.Controls.Viewport3D>jak nakreslit 3D grafiku uvnitř rozhraní .  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>3D souřadný prostor  
 Souřadnicový [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém pro 2D grafiku vyhledá počátek v levém horním rohu oblasti vykreslování (obvykle na obrazovce). Ve 2D systému postupují kladné hodnoty osy x doprava a kladné hodnoty osy y postupují dolů.  Ve 3D souřadnicovém systému je však počátek umístěn ve středu oblasti vykreslování, přičemž kladné hodnoty osy x směřují doprava, ale kladné hodnoty osy y postupují nahoru a kladné hodnoty osy z postupují směrem ven od počátku, směrem k divákovi.  
  
 ![Souřadné systémy](./media/coordsystem-1.png "CoordSystem-1")  
Konvenční reprezentace 2D a 3D souřadnicových systémů  
  
 Prostor definovaný těmito osami je stacionární referenční [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]rámec pro 3D objekty v . Při vytváření modelů v tomto prostoru a vytváření světel a kamer pro jejich zobrazení je užitečné odlišit tento stacionární referenční rámec neboli "světový prostor" od místního referenčního rámce, který vytvoříte pro každý model, když na něj použijete transformace. Nezapomeňte také, že objekty ve světovém prostoru mohou vypadat úplně jinak, nebo nemusí být viditelné vůbec, v závislosti na nastavení světla a kamery, ale pozice kamery nemění umístění objektů ve světovém prostoru.  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>Kamery a projekce  
 Vývojáři, kteří pracují ve 2D, jsou zvyklí na umístění kresličových primitivů na dvourozměrné obrazovce. Když vytváříte 3D scénu, je důležité si uvědomit, že skutečně vytváříte 2D reprezentaci 3D objektů. Vzhledem k tomu, že 3D scéna vypadá odlišně v závislosti na pohledu diváka, musíte tento úhel pohledu určit. Třída <xref:System.Windows.Media.Media3D.Camera> umožňuje určit tento úhel pohledu pro 3D scénu.  
  
 Dalším způsobem, jak pochopit, jak je 3D scéna reprezentována na 2D povrchu, je popis scény jako projekce na zobrazovací plochu. Umožňuje <xref:System.Windows.Media.Media3D.ProjectionCamera> určit různé projekce a jejich vlastnosti, abyste změnili způsob, jakým divák vidí 3D modely. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> určuje projekci, která zkracuje scénu.  Jinými <xref:System.Windows.Media.Media3D.PerspectiveCamera> slovy poskytuje mizející bod perspektivy.  Můžete určit polohu kamery v souřadnicovém prostoru scény, směr a zorné pole kamery a vektor, který definuje směr "nahoru" ve scéně. Následující diagram znázorňuje <xref:System.Windows.Media.Media3D.PerspectiveCamera>'s projekce.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> Vlastnosti <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> a <xref:System.Windows.Media.Media3D.ProjectionCamera> vlastnosti omezují rozsah projekce kamery. Vzhledem k tomu, že kamery mohou být umístěny kdekoli ve scéně, je možné, že kamera je skutečně umístěna uvnitř modelu nebo velmi blízko modelu, což ztěžuje správné rozlišení objektů.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>umožňuje určit minimální vzdálenost od kamery, za kterou nebudou objekty nakresleny.  Naopak umožňuje <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> určit vzdálenost od kamery, za kterou nebudou objekty nakresleny, což zajistí, že objekty příliš daleko, aby byly rozpoznatelné, nebudou zahrnuty do scény.  
  
 ![Nastavení kamery](./media/coordsystem-6.png "CoordSystem-6")  
Poloha kamery  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>určuje ortogonu 3D modelu na 2D vizuální povrch. Stejně jako ostatní kamery určuje polohu, směr zobrazení a směr "nahoru". Na <xref:System.Windows.Media.Media3D.PerspectiveCamera>rozdíl <xref:System.Windows.Media.Media3D.OrthographicCamera> od , však popisuje projekce, která nezahrnuje perspektivní zkrácení. Jinými slovy, popisuje zobrazení box, <xref:System.Windows.Media.Media3D.OrthographicCamera> jehož strany jsou rovnoběžné, místo toho, jehož strany se setkají v bodě na kameru. Následující obrázek ukazuje stejný model <xref:System.Windows.Media.Media3D.PerspectiveCamera> <xref:System.Windows.Media.Media3D.OrthographicCamera>jako zobrazení pomocí a .  
  
 ![Ortografická a perspektivní projekce](./media/camera-projections4.png "Camera_projections4")  
Perspektivní a ortografické projekce  
  
 Následující kód ukazuje některé typické nastavení fotoaparátu.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>Základní prvky modelu a sítě  
  
 <xref:System.Windows.Media.Media3D.Model3D>je abstraktní základní třída, která představuje obecný 3D objekt. Chcete-li vytvořit 3D scénu, potřebujete některé objekty k zobrazení a <xref:System.Windows.Media.Media3D.Model3D>objekty, které tvoří graf scény, jsou odvozeny z aplikace . V současné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] době podporuje modelování <xref:System.Windows.Media.Media3D.GeometryModel3D>geometrie s . Vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> tohoto modelu trvá základní mřížky.  
  
 Chcete-li vytvořit model, začněte vytvořením primitivní nebo sítě. 3D primitiva je kolekce vrcholů, které tvoří jednu 3D entitu. Většina 3D systémů poskytuje primitiva modelovaná na nejjednodušším uzavřeném obrázku: trojúhelníku definovaném třemi vrcholy.  Vzhledem k tomu, že tři body trojúhelníku jsou koplanární, můžete pokračovat v přidávání trojúhelníků, aby bylo možné modelovat složitější tvary nazývané ok.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3D systém v současné <xref:System.Windows.Media.Media3D.MeshGeometry3D> době poskytuje třídu, která umožňuje určit libovolnou geometrii; v současné době nepodporuje předdefinovaná 3D primitiva, jako jsou koule a kubické formy. Začněte <xref:System.Windows.Media.Media3D.MeshGeometry3D> vytvářet zadáním seznamu vrcholů trojúhelníku jako jeho <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> vlastnosti. Každý vrchol je určen <xref:System.Windows.Media.Media3D.Point3D>jako .  (V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], zadejte tuto vlastnost jako seznam čísel seskupených do trojek, které představují souřadnice každého vrcholu.) V závislosti na geometrii se síť může skládat z mnoha trojúhelníků, z nichž některé sdílejí stejné rohy (vrcholy). Chcete-li síť nakreslit správně, informace o potřebách, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] které vrcholy jsou sdíleny trojúhelníky. Tyto informace zadáte zadáním seznamu indexů trojúhelníku <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> s vlastností. Tento seznam určuje pořadí, ve kterém <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> body zadané v seznamu určí trojúhelník.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 V předchozím příkladu <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznam určuje osm vrcholů pro definování sítě ve tvaru krychle. Vlastnost <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> určuje seznam dvanácti skupin tří indexů.  Každé číslo v seznamu odkazuje na <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> posun do seznamu.  Například první tři vrcholy určené <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> v seznamu jsou (1,1,0), (0,1,0) a (0,0,0). První tři indexy uvedené <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> v seznamu jsou 0, 2 a 1, které odpovídají prvnímu, třetímu a druhému <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> bodu v seznamu. V důsledku toho první trojúhelník, který tvoří model krychle, se bude skládat z (1,1,0) do (0,1,0) do (0,0,0) a zbývajících jedenáct trojúhelníků bude určeno podobně.  
  
 Můžete pokračovat v definování modelu zadáním <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> hodnot <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> pro vlastnosti a.  K vykreslení povrchu modelu potřebuje grafický systém informace o tom, kterým směrem směřuje povrch v daném trojúhelníku. Tyto informace používá k výpočtu osvětlení modelu: povrchy, které směřují přímo ke zdroji světla, vypadají jasněji než ty, které jsou nakloněny od světla. Ačkoli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] můžete určit výchozí normální vektory pomocí souřadnic polohy, můžete také určit různé normální vektory, aby se přiblížil vzhled zakřivených povrchů.  
  
 Vlastnost <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> určuje kolekci <xref:System.Windows.Point>s, která říká grafickému systému, jak mapovat souřadnice, které určují, jak je textura přitahována k vrcholům sítě. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>jsou určeny jako hodnota mezi nulou a 1 včetně.  Stejně <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> jako u vlastnosti může grafický systém vypočítat výchozí souřadnice textury, ale můžete nastavit různé souřadnice textury pro řízení mapování textury, která obsahuje například část opakujícího se vzorku. Další informace o souřadnicích textury naleznete v následujících tématech nebo v sadáčkové sadě Direct3D SDK.  
  
 Následující příklad ukazuje, jak vytvořit jednu plochu modelu datové krychle v procedurálním kódu. Můžete nakreslit celou krychli jako jeden GeometryModel3D; Tento příklad nakreslí plochu krychle jako odlišný model, aby bylo možné později aplikovat samostatné textury na každou plochu.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>Použití materiálů na model  
  
 Aby síť vypadala jako trojrozměrný objekt, musí mít aplikovanou texturu, aby pokrývala povrch definovaný jejími vrcholy a trojúhelníky, aby mohla být osvětlena a promítána kamerou. Ve 2D použijete <xref:System.Windows.Media.Brush> třídu k aplikování barev, vzorků, přechodů nebo jiného vizuálního obsahu na oblasti obrazovky.  Vzhled 3D objektů je však funkcí modelu osvětlení, nikoli pouze barvy nebo vzoru, které se na ně aplikují. Objekty reálného světa odrážejí světlo odlišně v závislosti na kvalitě jejich povrchů: lesklé a lesklé povrchy nevypadají stejně jako drsné nebo matné povrchy a zdá se, že některé objekty absorbují světlo, zatímco jiné září. Na 3D objekty můžete aplikovat všechny stejné stopy, které můžete aplikovat na 2D objekty, ale nemůžete je aplikovat přímo.  
  
 Chcete-li definovat charakteristiky povrchu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelu, používá abstraktní třídu. <xref:System.Windows.Media.Media3D.Material> Konkrétní podtřídy Materiálu určit některé charakteristiky vzhledu povrchu modelu a každý také poskytuje Brush vlastnost, do které můžete předat SolidColorBrush, TileBrush nebo VisualBrush.  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>určuje, že stopa bude použita na model, jako by byl tento model rozsvícen difuzně. Použití DiffuseMaterial nejvíce podobá použití stoppřímo na 2D modely; povrchy modelu neodrážejí světlo, jako by byly lesklé.  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>určuje, že stopa bude aplikována na model, jako by povrch modelu byl tvrdý nebo lesklý, schopný odrážet světla. Můžete nastavit stupeň, do kterého textura navrhne tuto reflexní kvalitu <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> neboli "lesk", zadáním hodnoty vlastnosti.  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>umožňuje určit, že textura bude použita, jako by model vyzařoval světlo rovnající se barvě stopy. To neznamená, že model světlo; však bude podílet jinak stínování, než by v případě textury s DiffuseMaterial nebo SpecularMaterial.  
  
 Pro lepší výkon jsou zadní <xref:System.Windows.Media.Media3D.GeometryModel3D> plochy (ty plochy, které jsou mimo dohled, protože jsou na opačné straně modelu z kamery) vyřazeny ze scény.  Chcete-li <xref:System.Windows.Media.Media3D.Material> určit, chcete-li použít zadní plochu modelu, jako <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> je rovina, nastavte vlastnost modelu.  
  
 Chcete-li dosáhnout některých vlastností povrchu, jako jsou zářící nebo reflexní efekty, můžete na model postupně aplikovat několik různých štětců. Pomocí třídy <xref:System.Windows.Media.Media3D.MaterialGroup> můžete použít a znovu použít více materiálů. Podřízené objekty MaterialGroup jsou použity jako první poslední ve více průchodech vykreslování.  
  
 Následující příklady kódu ukazují, jak aplikovat plnou barvu a kresbu jako stopy na 3D modely.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>Osvětlení scény  
 Světla ve 3D grafice dělají to, co světla dělají v reálném světě: zviditelní povrchy. Více k věci, světla určují, která část scény bude zahrnuta do projekce. Světelné objekty vytvářejí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] různé světelné a stínové efekty a jsou modelovány podle chování různých reálných světel. Zahrňte do scény alespoň jedno světlo, jinak nebudou viditelné žádné modely.  
  
 Ze základní třídy jsou <xref:System.Windows.Media.Media3D.Light>odvozena následující světla :  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: Poskytuje okolní osvětlení, které osvětluje všechny objekty rovnoměrně bez ohledu na jejich umístění nebo orientaci.  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: Svítí jako vzdálený zdroj světla.  Směrové kontroly <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> mají určené jako Vector3D, ale žádné zadané umístění.  
  
- <xref:System.Windows.Media.Media3D.PointLight>: Svítí jako blízký světelný zdroj. PointLights mají pozici a vrhají světlo z této polohy. Objekty ve scéně jsou osvětleny v závislosti na jejich poloze a vzdálenosti vzhledem ke světlu. <xref:System.Windows.Media.Media3D.PointLightBase>vystavuje <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> vlastnost, která určuje vzdálenost, za kterou modely nebudou osvětleny světlem. PointLight také odhaluje vlastnosti útlumu, které určují, jak se intenzita světla snižuje na vzdálenost. Můžete určit konstantní, lineární nebo kvadratické interpolace pro útlum světla.  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: Dědí <xref:System.Windows.Media.Media3D.PointLight>z . Reflektory se rozsvítí jako PointLight a mají polohu i směr. Promítají světlo v kuželovité <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> oblasti <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> nastavené a vlastnosti, určené ve stupních.  
  
 Světla <xref:System.Windows.Media.Media3D.Model3D> jsou objekty, takže můžete transformovat a animovat vlastnosti světla, včetně polohy, barvy, směru a rozsahu.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>Transformace modelů  
 Když vytváříte modely, mají určité umístění ve scéně. Chcete-li tyto modely přesunout ve scéně, otočit je nebo změnit jejich velikost, není praktické měnit vrcholy, které definují samotné modely.  Místo toho, stejně jako ve 2D, použijete transformace na modely.  
  
 Každý objekt modelu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> má vlastnost, se kterou můžete přesunout, přeorientovat nebo změnit velikost modelu.  Když aplikujete transformaci, efektivně odsadíte všechny body modelu podle jakéhokoli vektoru nebo hodnoty určené transformací. Jinými slovy jste transformovali souřadnicový prostor, ve kterém je definován model ("modelový prostor"), ale nezměnili jste hodnoty, které tvoří geometrii modelu v souřadnicovém systému celé scény ("světový prostor").  
  
 Další informace o transformaci modelů naleznete v [tématu Přehled 3D transformací](3-d-transformations-overview.md).  
  
<a name="animations"></a>
## <a name="animating-models"></a>Animace modelů  
 3D [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace se účastní stejného časování a animačního systému jako 2D grafika. Jinými slovy, animovat 3D scénu, animovat vlastnosti svých modelů. Je možné animovat vlastnosti primitiv přímo, ale je obvykle jednodušší animovat transformace, které mění pozici nebo vzhled modelů. Vzhledem k tomu, <xref:System.Windows.Media.Media3D.Model3DGroup> že transformace lze použít na objekty i jednotlivé modely, je možné použít jednu sadu animací na podřízenou model3DGroup a jinou sadu animací na skupinu podřízených objektů. Animací vlastností osvětlení scény můžete také dosáhnout různých vizuálních efektů. Nakonec se můžete rozhodnout animovat samotnou projekci animací polohy kamery nebo zorného pole. Základní informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému časování a animace naleznete v tématech [Přehled animací](animation-overview.md), [Přehled scénářů](storyboards-overview.md)a [Přehled mrazivých objektů.](../advanced/freezable-objects-overview.md)  
  
 Chcete-li animovat objekt v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikaci , vytvořte časovou osu, definujte animaci (což je opravdu změna hodnoty některé vlastnosti v čase) a určete vlastnost, na kterou se má animace použít. Vzhledem k tomu, že všechny <xref:System.Windows.Controls.Viewport3D>objekty ve 3D scéně jsou podřízené objekty , vlastnosti, na které se zaměřují všechny animace, které chcete na scénu aplikovat, jsou vlastnosti Funkce Viewport3D.  
  
 Předpokládejme, že chcete, aby se model zachvěl na místě. Můžete použít a <xref:System.Windows.Media.Media3D.RotateTransform3D> na model a animovat osu jeho natočení z jednoho vektoru do druhého. Následující příklad kódu ukazuje použití Vector3DAnimation na Axis vlastnost transformace Rotation3D, za předpokladu, že RotateTransform3D být jedním z několika transformací aplikovaných na model s TransformGroup.  
  
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
 Chcete-li vykreslení scény, <xref:System.Windows.Media.Media3D.Model3DGroup>přidejte modely <xref:System.Windows.Media.Media3D.Model3DGroup> a <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> světla <xref:System.Windows.Media.Media3D.ModelVisual3D>do a , pak nastavte jako . Přidejte <xref:System.Windows.Media.Media3D.ModelVisual3D> do <xref:System.Windows.Controls.Viewport3D.Children%2A> kolekce <xref:System.Windows.Controls.Viewport3D>. Přidejte kamery <xref:System.Windows.Controls.Viewport3D> nastavením jeho vlastnosti. <xref:System.Windows.Controls.Viewport3D.Camera%2A>  
  
 Nakonec přidejte <xref:System.Windows.Controls.Viewport3D> do okna. Pokud <xref:System.Windows.Controls.Viewport3D> je zahrnuta jako obsah prvku rozložení, jako je plátno, zadejte <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> velikost Viewport3D nastavením jeho a vlastnosti (zděděné z <xref:System.Windows.FrameworkElement>).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [Přehled 3D transformací](3-d-transformations-overview.md)
- [Maximalizace výkonu WPF 3D](maximize-wpf-3d-performance.md)
- [Témata s postupy](3-d-graphics-how-to-topics.md)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
