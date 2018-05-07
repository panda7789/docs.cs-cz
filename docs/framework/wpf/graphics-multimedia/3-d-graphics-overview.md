---
title: Přehled 3D grafiky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D graphics [WPF]
- graphics [WPF], 3-D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 6d44f27ccd82d535436be03092c3864e3155d1d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="3-d-graphics-overview"></a>Přehled 3D grafiky
<a name="introduction"></a> [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Funkce v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umožňuje vývojářům kreslení, transformace a použije animaci 3D grafický v značek a procedurální kódu. Mohou vývojáři kombinovat [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafické vytvořit bohaté ovládací prvky, poskytují komplexní ilustrace dat nebo vylepšit uživatele prostředí rozhraní aplikace. [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] podpora v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] není určená k poskytnutí herní vývojové platformy plně funkční. Toto téma obsahuje přehled [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] funkce v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafika systému.  
 
  
<a name="threed_in_2d"></a>   
## <a name="3-d-in-a-2-d-container"></a>3D v kontejneru 2-D  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Grafika obsahu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je zapouzdřené v elementu, <xref:System.Windows.Controls.Viewport3D>, který mohl účastnit strukturu dvourozměrná element. Grafika systém zpracovává <xref:System.Windows.Controls.Viewport3D> jako element dvourozměrná visual jako mnoho dalších v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Viewport3D> funguje jako okno – zobrazení – do 3D scény. Přesněji řečeno, surface, na kterém je [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] se promítá scény.  
  
 V konvenční [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] aplikace, použijte <xref:System.Windows.Controls.Viewport3D> stejně jako jiný element kontejneru jako plátno nebo mřížky.  Přestože je možné použít <xref:System.Windows.Controls.Viewport3D> s jinými [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] kreslení objektů v jednom scény grafu, nelze interpenetrate [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objekty v rámci <xref:System.Windows.Controls.Viewport3D>.  Toto téma zaměřuje na postup kreslení [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafiky uvnitř <xref:System.Windows.Controls.Viewport3D>.  
  
<a name="coord_space"></a>   
## <a name="3-d-coordinate-space"></a>3D souřadnicového prostoru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Souřadnicový systém pro [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafiky vyhledá počátek v levé horní části oblasti vykreslování (obvykle na obrazovce). V [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] systému, kladné hodnoty osy x pokračovat doprava a dolů pokračovat osy y kladné hodnoty.  V [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] souřadnicový systém, ale počátek se nachází v centru oblasti vykreslování s hodnotami kladné osy x vpravo budete pokračovat, ale budete pokračovat směrem nahoru místo hodnoty osy y kladné a kladné osy z hodnoty budete pokračovat i z tohoto počátku směrem k prohlížeči.  
  
 ![Systémy souřadnic](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem-1")  
Reprezentace konvenční 2D a 3D souřadnicový systém  
  
 Místo definované tyto osy je stojící rámec pro [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objekty v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Jak vytvářet modely z tohoto prostoru a vytvořit indikátory a kamery k jejich zobrazení, je užitečné k rozlišení tento stojící rámec nebo "world prostor," z místní rámec, který vytvoříte pro každý model, při použití transformace. Nezapomeňte také, že objekty v prostoru world pravděpodobně zcela liší, nebo není viditelná vůbec, v závislosti na světlým a fotoaparát nastavení, ale pozice kamery nezmění umístění objekty v prostoru world.  
  
<a name="cameras"></a>   
## <a name="cameras-and-projections"></a>Kamery a projekce  
 Vývojáři, kteří pracují v [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] jsou uzpůsobené pro umístění kreslení primitiv na dvourozměrné obrazovce. Při vytváření [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény, je důležité si pamatovat, že skutečně vytváříte [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] reprezentace [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objekty. Protože [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény vypadá liší v závislosti na onlooker hlediska, je nutné zadat tohoto hlediska. <xref:System.Windows.Media.Media3D.Camera> Třída umožňuje zadat Tento bod pohledu pro [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény.  
  
 Jiný způsob, jak pochopit, jak [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény je reprezentována na [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] prostor je popisující scény jako projekce na plochu zobrazení. <xref:System.Windows.Media.Media3D.ProjectionCamera> Můžete zadat různé projekce a jejich vlastnosti chcete změnit, jak se zobrazí onlooker [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modelů. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> určuje projekce, které foreshortens scény.  Jinými slovy <xref:System.Windows.Media.Media3D.PerspectiveCamera> poskytuje ú bod perspektivy.  Pozice kamery můžete zadat v prostoru souřadnic scény, směr a zobrazovanou kamera a vektor, který definuje směr "nahoru" v scény. Následující diagram znázorňuje <xref:System.Windows.Media.Media3D.PerspectiveCamera>na projekce.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> a <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> vlastnosti <xref:System.Windows.Media.Media3D.ProjectionCamera> omezit rozsah kamery projekce. Protože kamery mohou být umístěny kdekoli v scény, je možné kamera se ve skutečnosti umístí uvnitř modelu nebo velmi téměř modelu, že se k rozlišení objekty správně.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> Umožňuje zadat minimální vzdálenost od fotoaparát, jejichž překročení nebude vykreslovat objekty.  Naopak <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> umožňuje určit vzdálenost od kamera nad rámec, který nebude vykreslovat objekty, které zajišťuje, že objekty příliš daleko být rozpoznatelném nebude součástí scény.  
  
 ![Instalační program fotoaparát](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-6.png "CoordSystem 6")  
Pozice fotoaparát  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> Určuje kolmého průmětu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modelu do [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] visual prostor. Jako další kamery určuje pozici, zobrazení směr a směr "nahoru". Na rozdíl od <xref:System.Windows.Media.Media3D.PerspectiveCamera>, ale <xref:System.Windows.Media.Media3D.OrthographicCamera> popisuje projekce, které nepředstavují perspektivního zkreslení perspektivy. Jinými slovy <xref:System.Windows.Media.Media3D.OrthographicCamera> popisuje zobrazení pole, jehož strany jsou paralelní místo jedné strany, jejichž splnění v bodě fotoaparát. Následující obrázek ukazuje stejného modelu, jak zobrazit pomocí <xref:System.Windows.Media.Media3D.PerspectiveCamera> a <xref:System.Windows.Media.Media3D.OrthographicCamera>.  
  
 ![Pravoúhlé a perspektivní promítání](../../../../docs/framework/wpf/graphics-multimedia/media/camera-projections4.png "Camera_projections4")  
Perspektivy a pravoúhlé projekce  
  
 Následující kód ukazuje některé typické fotoaparát nastavení.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## <a name="model-and-mesh-primitives"></a>Model a OK primitiv  
  
 <xref:System.Windows.Media.Media3D.Model3D> je abstraktní základní třída, která reprezentuje obecný [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objektu. K vytvoření [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény, je nutné zobrazit některé objekty a objekty, které tvoří grafu scény odvozena od <xref:System.Windows.Media.Media3D.Model3D>. V současné době [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje modelování geometrie s <xref:System.Windows.Media.Media3D.GeometryModel3D>. <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> Vlastnosti tohoto modelu trvá primitivní mřížku.  
  
 Pokud chcete vytvořit model, začněte tím, že vytváření primitivní nebo OK sítě. A [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] primitivní je kolekce vrcholy, které vytvářejí jedné [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] entity. Většina [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] systémy poskytují primitiv vymodelován nejjednodušší uzavřený útvar: trojúhelník definované tři vrcholy.  Protože jsou tři body trojúhelníku coplanar, můžete pokračovat v přidání trojúhelníčky Chcete-li model více komplexní tvarů, názvem skupiny uzlů.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Systém aktuálně poskytuje <xref:System.Windows.Media.Media3D.MeshGeometry3D> třída, která umožňuje určit všechny geometrie; nepodporuje aktuálně předdefinované [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] primitiv jako oblasti a krychlový forms. Začněte vytvářet <xref:System.Windows.Media.Media3D.MeshGeometry3D> zadáním seznam trojúhelníček vrcholy jako jeho <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> vlastnost. Každý vrchol je zadán jako <xref:System.Windows.Media.Media3D.Point3D>.  (V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], tuto vlastnost lze zadat jako seznam čísel, které jsou seskupené do po třech, které představují souřadnice každý vrcholu.) V závislosti na jeho geometry může vaše OK skládá z mnoha trojúhelníky, z nichž některé sdílet stejnou rozích (vrcholy). Kreslení OK správně, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] potřebuje informace o tom, které sdílí vrcholy které trojúhelníčky. Zadání těchto informací tak, že zadáte seznam trojúhelníček indexy, které se <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> vlastnost. Určuje pořadí, ve kterém body uvedené v tomto seznamu <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu určí trojúhelník.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 V předchozím příkladu <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu určuje osm vrcholy k definování mřížky ve tvaru datové krychle. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> Vlastnost určuje seznam dvanáct skupin tři indexy.  Posun do všech čísel v seznamu odkazuje <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu.  Například první tři vrcholy určeného <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu jsou (1,1,0), (0,1,0) a (0,0,0). První tři indexy určeného <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> seznamu jsou 0, 2 a 1, která odpovídají na první třetí a druhé body v <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu. V důsledku toho první trojúhelníček, která vytváří model datové krychle se skládá z (1,1,0) na (0,1,0) na (0,0,0) a zbývající 11 trojúhelníčky určí podobně.  
  
 Můžete pokračovat zadáním hodnot pro definování modelu <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> a <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> vlastnosti.  Grafika systému k vykreslení prostor modelu, musí informace o tom, které je směr povrchu směřující na jakékoli dané trojúhelníku. Tyto informace se použijí pro vytvoření osvětlení výpočtů pro model: Zobrazí světlejší než ty, které šikmo od světlým povrchy směřujících přímo ke zdroji světla. I když [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] můžete určit výchozí běžné vektory pomocí souřadnice polohy, můžete také určit různé běžné vektory sblížit vzhled zakřivené ploch.  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> Vlastnost určuje kolekci <xref:System.Windows.Point>s, který odezvu grafika systému pro mapování souřadnice, které určují, jak je texturou vykreslovány vrcholy OK. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> nejsou zadány jako hodnotu mezi 0 a 1 (včetně).  Stejně jako u <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> vlastnost grafika systému můžete vypočítat výchozí texture souřadnice, ale můžete nastavit různé texture souřadnice k řízení mapování texture, která obsahuje součást opakující se vzorek, například. Další informace o texture souřadnice naleznete v následujících tématech nebo v sadě SDK Direct3D – spravované.  
  
 Následující příklad ukazuje, jak vytvořit jeden řez modelu datové krychle v procedurální kódu. Všimněte si, že při kreslení na celou datovou krychli jako jeden GeometryModel3D; Tento příklad nevykresluje vzhled datové krychle jako odlišné model Chcete-li použít samostatné textury pro každý řez později.  
  
 [!code-csharp[3doverview#3DOverview3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## <a name="applying-materials-to-the-model"></a>Použití materiály do modelu  
  
 Pro mřížku, aby vypadala jako 3D objektu musí mít použité texture tak, aby pokrývalo plochy definované svým vrcholy a trojúhelníčky tak, aby ho lit a podle fotoaparát k projekci. V [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], můžete použít <xref:System.Windows.Media.Brush> třída použít barvy, vzory, přechody nebo jiný vizuální obsah do oblastí obrazovky.  Vzhled [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objekty, je však funkce osvětlení modelu, ne jenom z barvu nebo vzorek na ně použity. Skutečné objekty podle light odlišně v závislosti na kvalitu jejich plochy: lesklý a lesklý povrchy nevypadají, stejně jako hrubý nebo podklad ploch a některé objekty se zdá, že pojmout světlý, zatímco ostatní záře. Můžete použít stejné štětce k [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objekty, které můžete použít pro [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] objektů, ale nelze je přímo použít.  
  
 Definovat vlastnosti modelu prostor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá <xref:System.Windows.Media.Media3D.Material> abstraktní třídy. Konkrétní podtřídy materiálu určit některé charakteristiky vzhled povrchu modelu, a každou také poskytuje štětce vlastnost, do které můžete předat SolidColorBrush –, TileBrush nebo VisualBrush.  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial> Určuje, že stopy použité pro model, jako kdyby byly diffusely lit tento model. Pomocí DiffuseMaterial nejvíce podobá použití štětce přímo na [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] modely; proveďte povrchy modelu nemusí odpovídat světla, jako když lesklý.  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial> Určuje, že stopy použité pro model, jako by byl modelu prostor pevné nebo lesklý, schopná odrážející označuje. Úroveň, do které bude textury navrhovat tento odrážející kvality, nebo "nám," můžete nastavit tak, že zadáte hodnotu <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> vlastnost.  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial> Umožňuje zadat, že textury se použije jako by se model měla generování světla rovno barvu štětce. To nebyly provedeny model light; však se bude účastnit jinak stínový provoz, než kdyby texturou s DiffuseMaterial nebo SpecularMaterial.  
  
 Pro lepší výkon zadní plochy z <xref:System.Windows.Media.Media3D.GeometryModel3D> (řezy, které jsou mimo zobrazení, protože jsou na opačné straně modelu z kamery) jsou vyřazeny z scény.  Chcete-li určit <xref:System.Windows.Media.Media3D.Material> aplikovat na backface modelu jako rovině, nastavení modelu <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> vlastnost.  
  
 K dosažení některé prostor vlastností, jako Zářící nebo reflexivní důsledky, můžete použít několik různých štětce k modelu za sebou. Můžete použít a znovu použít více materiály pomocí <xref:System.Windows.Media.Media3D.MaterialGroup> třídy. Podřízené objekty daného MaterialGroup se použije první na poslední v několika předává vykreslování.  
  
 Následující příklady kódu ukazují, jak použít plnou barvou a kreslení jako štětce k [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modelů.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## <a name="illuminating-the-scene"></a>Osvětlení scény  
 Světel v [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafiky udělat, co dělat indikátory v praxi: jejich zviditelnit ploch. Do bodu, více indikátory určit, jaká část scény zahrnuta v projekci. Light objekty v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvořit různé světlým a Stínové efekty a jsou modelována podle chování různých indikátorů reálného. Je nutné zahrnout alespoň jeden light vaší scény nebo žádné modely se nebude zobrazovat.  
  
 Tyto indikátory odvozeny od základní třídy <xref:System.Windows.Media.Media3D.Light>:  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight>: Poskytuje osvětlení okolí, který osvětluje všechny objekty jednotně bez ohledu na jejich umístění nebo orientace.  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight>: Osvětluje jako vzdáleným zdroje světla.  Mít směrová světla <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> zadaný jako Vector3D, ale není zadané umístění.  
  
-   <xref:System.Windows.Media.Media3D.PointLight>: Osvětluje jako blízkým zdroje světla. PointLights polohy a převést light z této pozice. Objekty v scény jsou osvětleny v závislosti na jejich umístění a vzdálenost s ohledem na světla. <xref:System.Windows.Media.Media3D.PointLightBase> zpřístupní <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> vlastnosti, která určuje vzdálenost, jejichž překročení nebudou modely osvětlení světla. PointLight také zpřístupní oslabení vlastnosti, které určují, jak intenzitou světla snižuje vzdálenost. Můžete zadat konstantní, lineární nebo kvadratické interpolace pro oslabení světla.  
  
-   <xref:System.Windows.Media.Media3D.SpotLight>: Dědí z <xref:System.Windows.Media.Media3D.PointLight>. Světelné kužele osvětlení jako PointLight a mít pozice a směr. Jejich projektu light v oblasti kuželovitá nastaven <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> a <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> vlastnosti, zadaný ve stupních.  
  
 Indikátory <xref:System.Windows.Media.Media3D.Model3D> objekty, abyste mohli transformovat a použije animaci světla vlastnosti, včetně umístění, barvy, směr a rozsah.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## <a name="transforming-models"></a>Transformace modely  
 Při vytváření modelů mají konkrétního umístění v scény. Pohyb tyto modely v scény, pro jejich otočení nebo změnit jejich velikost není praktické, chcete-li změnit vrcholy, které definují modely sami.  Místo toho právě jako v [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], použijete pro modely transformace.  
  
 Každý objekt modelu má <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> vlastností, pomocí kterého můžete přesunout, znovu orientaci nebo změnit velikost modelu.  Při použití transformace efektivně posunu všechny body modelu ať vektoru nebo hodnoty určené pro transformaci. Jinými slovy, jste transformovat souřadnicového prostoru, ve kterém je model definované ("model místo"), ale nedošlo ke změně hodnoty, které tvoří geometrie modelu v souřadnicový systém celý scény ("world prostor").  
  
 Další informace o transformaci modelů najdete v tématu [3D transformace přehled](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md).  
  
<a name="animations"></a>   
## <a name="animating-models"></a>Animace modely  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Implementace účastní na stejném načasování a animace systému jako [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafiky. Jinými slovy použije animaci 3D scény, použije animaci vlastnosti její modely. Je možné přímo animace vlastnosti primitivních elementů, ale je obvykle jednodušší animace transformace, které se změny umístění nebo vzhled modelů. Protože transformace je možné použít k <xref:System.Windows.Media.Media3D.Model3DGroup> objekty a také jednotlivé modely, je možné použít jednu sadu animací podřízenou Model3DGroup a další sadu animace do skupiny podřízených objektů. Můžete také dosáhnout různých vizuálních efektů animace vlastnosti vaší scény osvětlení. Nakonec můžete zvolit podle animace fotoaparát pozici nebo zobrazovanou použije animaci projekce sám sebe. Základní informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] načasování a animace systému, najdete v článku [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md), [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md), a [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)témata.  
  
 Pro objekt v animaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vytvoření časové osy, definovat animace (což je ve skutečnosti změnu v hodnotě některé vlastnosti v čase) a zadejte vlastnosti, na kterou budou používány animace. Protože všechny objekty v [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény jsou podřízené <xref:System.Windows.Controls.Viewport3D>, vlastnosti cílem žádné animace, kterou chcete použít k scény jsou vlastnosti vlastnosti Viewport3D.  
  
 Předpokládejme, že má být model pravděpodobně wobble na místě. Můžete použít <xref:System.Windows.Media.Media3D.RotateTransform3D> do modelu a použije animaci ose otočení z jednoho vektor do jiného. Následující příklad kódu ukazuje, použití Vector3DAnimation vlastnost osy transformaci Rotation3D, za předpokladu, že RotateTransform3D být jedním z několika transformací použitá pro model s TransformGroup.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## <a name="add-3-d-content-to-the-window"></a>Přidat 3D obsah do okna  
 K vykreslení scény, přidejte modely a světla k <xref:System.Windows.Media.Media3D.Model3DGroup>, nastavte <xref:System.Windows.Media.Media3D.Model3DGroup> jako <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> z <xref:System.Windows.Media.Media3D.ModelVisual3D>. Přidat <xref:System.Windows.Media.Media3D.ModelVisual3D> k <xref:System.Windows.Controls.Viewport3D.Children%2A> kolekce <xref:System.Windows.Controls.Viewport3D>. Přidat kamery k <xref:System.Windows.Controls.Viewport3D> nastavením jeho <xref:System.Windows.Controls.Viewport3D.Camera%2A> vlastnost.  
  
 Nakonec přidejte <xref:System.Windows.Controls.Viewport3D> do okna. Když <xref:System.Windows.Controls.Viewport3D> je součástí, jako je obsah elementu rozložení jako plátno, zadejte velikost Viewport3D nastavením jeho <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti (zděděno z <xref:System.Windows.FrameworkElement>).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Viewport3D>  
 <xref:System.Windows.Media.Media3D.PerspectiveCamera>  
 <xref:System.Windows.Media.Media3D.DirectionalLight>  
 <xref:System.Windows.Media.Media3D.Material>  
 [Přehled 3D transformací](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md)  
 [Maximalizace výkonu WPF 3D](../../../../docs/framework/wpf/graphics-multimedia/maximize-wpf-3d-performance.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-how-to-topics.md)  
 [Přehled objektů Shape a základního kreslení ve WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
