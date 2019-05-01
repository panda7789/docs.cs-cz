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
ms.openlocfilehash: 79dc7a3578c395ae8cdf5933e1249441f97071a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053692"
---
# <a name="3-d-graphics-overview"></a>Přehled 3D grafiky
<a name="introduction"></a> [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Funkce v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vývojářům umožňuje nakreslit, transformaci a animace 3D grafiky v kódu a procedurální kódu. Vývojáři můžou kombinovat [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafiku, vytvořit bohaté ovládací prvky, poskytují komplexní ilustrace znázorňující data nebo vylepšit uživatel činnost rozhraní aplikace. [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] podpora v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] není určená k poskytování hru Vývojová platforma plně funkční. Toto téma obsahuje přehled [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafiky systému.  

<a name="threed_in_2d"></a>   
## <a name="3-d-in-a-2-d-container"></a>3D v kontejneru 2D  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Grafika obsahu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapouzdřena v elementu, <xref:System.Windows.Controls.Viewport3D>, který mohl podílet na struktuře dvojrozměrné elementu. Grafika systém zpracovává <xref:System.Windows.Controls.Viewport3D> jako dvojrozměrné vizuální prvky jako řada dalších v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Viewport3D> funguje jako okno – oblast zobrazení – do 3D scény. Přesněji, surface, na kterém je [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plánovaných scény.  
  
 V konvenční [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] aplikace, použijte <xref:System.Windows.Controls.Viewport3D> stejně jako jiný element kontejneru jako mřížky nebo plátna.  I když používáte <xref:System.Windows.Controls.Viewport3D> s jinými [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] vykreslení objektů v stejný graf scén, nelze interpenetrate [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objekty v rámci <xref:System.Windows.Controls.Viewport3D>.  Toto téma se zaměřuje na tom, jak nakreslit [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafiky uvnitř <xref:System.Windows.Controls.Viewport3D>.  
  
<a name="coord_space"></a>   
## <a name="3-d-coordinate-space"></a>3D souřadnicového prostoru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Souřadnicový systém pro [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafiky vyhledá původ v levém horním rohu oblasti vykreslování (obvykle obrazovky). V [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] systému, kladné hodnoty na ose x pokračovat na pravé straně a osy y kladné hodnoty postupovat směrem dolů.  V [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] souřadnicový systém, ale původ se nachází v Centru pro vykreslení oblasti s hodnoty na ose x kladné pokračuje na pravé straně, ale hodnoty y pozitivní místo toho pokračuje směrem nahoru a osy z kladné hodnoty pokračuje směrem ven. ze zdroje směrem k prohlížeči.  
  
 ![Systémy souřadnic](./media/coordsystem-1.png "CoordSystem-1")  
Reprezentace konvenční 2D a 3D souřadnicový systém  
  
 Místo definované tyto osy je bez pohybu rámec pro [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objekty v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Jak vytvářet modely v tomto prostoru a vytvoření světla a jejich zobrazení bezpečnostních kamer, je užitečné k rozlišení tohoto bez pohybu referenčním rámcem nebo "místa na světě," z místní rámec, který vytvoříte pro každý model, při použití transformace. Nezapomeňte, že objekty v prostoru světa mohou vypadají úplně jinak, nebo nebude viditelné ve všech, v závislosti na světla a fotoaparát nastavení, ale pozice kamery nezmění umístění objektů v prostoru světa.  
  
<a name="cameras"></a>   
## <a name="cameras-and-projections"></a>Kamery a projekce  
 Vývojáři, kteří pracují v [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] jsou zvyklí na umístění výkresu primitivních elementů na dvourozměrné obrazovce. Při vytváření [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény, je dobré si uvědomit, že ve skutečnosti vytváříte [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] reprezentace [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objekty. Protože [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény vypadá jinak v závislosti na tom, onlooker pohledu, je nutné zadat tohoto hlediska. <xref:System.Windows.Media.Media3D.Camera> Třída umožňuje určit tento pohled pro [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény.  
  
 Dalším způsobem, jak pochopit, jak [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény je znázorněné v [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] povrchu se zadáním popisu vašeho nového scény jako projekce na plochu zobrazení. <xref:System.Windows.Media.Media3D.ProjectionCamera> Vám umožní určit různé projekce a jejich vlastnosti a změnit, jak se zobrazí onlooker [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modely. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> specifikuje projekci, která foreshortens scény.  Jinými slovy <xref:System.Windows.Media.Media3D.PerspectiveCamera> obsahuje perspektivu zmenšovala bodu.  Pozice kamery můžete zadat v souřadnicového prostoru scény, směr a pole zobrazení pro fotoaparátu/kamery a vektor definující směr "nahoru" ve scéně. Následující diagram znázorňuje, <xref:System.Windows.Media.Media3D.PerspectiveCamera>společnosti projekce.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> a <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> vlastnosti <xref:System.Windows.Media.Media3D.ProjectionCamera> omezit rozsah kamery projekce. Protože kamery může být umístěn kdekoli ve scéně, je možné fotoaparát skutečně umístit uvnitř modelu nebo velmi v modelu, způsobuje obtížné správně odlišit objekty.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> Umožňuje určit minimální vzdálenost od fotoaparátu/kamery, jejichž překročení se vykreslit objekty.  Naopak <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> umožňuje určit vzdálenost od fotoaparátu/kamery nad rámec, který nebude nutné vykreslit objekty, které zajišťuje, že bude rozpoznatelných objektů příliš daleko nebudou zahrnuty ve scéně.  
  
 ![Nastavení fotoaparátu](./media/coordsystem-6.png "CoordSystem 6")  
Poloha kamery  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> Určuje pravoúhlý projekci [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modelu do [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] vizuální povrch. Stejně jako ostatní kamer určuje pozici zobrazení směr a směr "nahoru". Na rozdíl od <xref:System.Windows.Media.Media3D.PerspectiveCamera>, ale <xref:System.Windows.Media.Media3D.OrthographicCamera> popisuje projekci, která nezahrnuje perspektivního zkreslení perspektivy. Jinými slovy <xref:System.Windows.Media.Media3D.OrthographicCamera> popisuje zobrazení pole, jehož strany jsou paralelní místo jednoho splňovat bodě fotoaparátu/kamery, jehož strany. Následující obrázek ukazuje stejný model, jak zobrazit pomocí <xref:System.Windows.Media.Media3D.PerspectiveCamera> a <xref:System.Windows.Media.Media3D.OrthographicCamera>.  
  
 ![Pravoúhlé a perspektivní projekci](./media/camera-projections4.png "Camera_projections4")  
Perspektivy a pravoúhle projekce  
  
 Následující kód ukazuje některé typické nastavení.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## <a name="model-and-mesh-primitives"></a>Model a primitivních elementů sítě  
  
 <xref:System.Windows.Media.Media3D.Model3D> je abstraktní základní třída, která představuje obecnou [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objektu. K sestavení [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény, budete potřebovat některé objekty k zobrazení a objekty, které tvoří graf scén být odvozeny od <xref:System.Windows.Media.Media3D.Model3D>. V současné době [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje modelování geometrie s <xref:System.Windows.Media.Media3D.GeometryModel3D>. <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> Vlastnost tento model přijímá primitivní sítě.  
  
 Vytvoříte model, začněte tím, že vytváření jednoduchého typu nebo sítě. A [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] primitivní je kolekce vrcholy, které tvoří jeden [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] entity. Většina [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] systémů poskytuje primitivy vymodelován nejjednodušší uzavřený útvar: trojúhelník určené tři vrcholy.  Vzhledem k tomu tři body trojúhelník coplanar, můžete pokračovat v přidávání trojúhelníky k modelování více složitých tvarů, volá mřížky.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Systému v současné době poskytuje <xref:System.Windows.Media.Media3D.MeshGeometry3D> třídy, které můžete zadat libovolný geometrie; nepodporuje aktuálně předdefinované [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] primitivních elementů, jako jsou oblasti a kubické formuláře. Začněte vytvářet <xref:System.Windows.Media.Media3D.MeshGeometry3D> tak, že zadáte seznam vrcholů trojúhelník jako jeho <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> vlastnost. Každý vrchol je zadán jako <xref:System.Windows.Media.Media3D.Point3D>.  (V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], tuto vlastnost zadávejte jako seznam čísel seskupili po třech, které představují souřadnice každý vrchol.) V závislosti na jeho geometrie může vaše síť skládá z mnoha trojúhelníků, z nichž některé sdílet stejnou rohů (vrcholy). Chcete-li nakreslit síť správně, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] potřebuje informace o tom, které jsou sdíleny vrcholy které trojúhelníky. Tento údaj zadáte tak, že zadáte seznam trojúhelník indexy se <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> vlastnost. Tento seznam určuje pořadí, ve kterém body podle <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu určí trojúhelník.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 V předchozím příkladu <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu určuje osm vrcholů k definování datové krychle ve tvaru mřížky. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> Vlastnost určuje seznam dvanáct skupin tři indexy.  Každé číslo v seznamu odkazuje na posun do <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu.  Například první tři vrcholy, které jsou určené <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu jsou (1,1,0) (0,1,0) a (0,0,0). První tři indexy, které jsou určené <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> seznamu jsou 0, 2 a 1, které odpovídají na první třetí a druhá body v <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> seznamu. V důsledku toho první trojúhelník, který vytvoří model datové krychle se skládá z (1,1,0) na (0,1,0) na (0,0,0) a zbývající jedenáct trojúhelníky určí podobně.  
  
 Můžete pokračovat v definujete zadáním hodnoty pro model <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> a <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> vlastnosti.  K vykreslení plochy modelu, musí systém grafické informace o tom, které je otočena směrem na plochu v jakékoli dané trojúhelník. Provádět výpočty osvětlení pro model využívá tyto informace: Zobrazí světlejší než ty, které od světla v lomených površích, které přímo vůči zdroji světla pro rozpoznávání tváře. I když [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] můžete určit výchozí běžných vektorů s použitím souřadnice polohy, můžete také určit různé běžné vektory aproximace vzhled zakřivené ploch.  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> Vlastnost určuje kolekci <xref:System.Windows.Point>, které oznámit systému grafiky, jak namapovat souřadnice, které určují, jak textury linie vrcholy síť. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> jsou zadané jako hodnota mezi 0 a 1 (včetně).  Stejně jako u <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> vlastnost, systém grafiky můžete vypočítat výchozí souřadnice textury, ale můžete nastavit různé textury souřadnice řídit mapování texturu, která například obsahuje součást s opakováním vzoru. Další informace o souřadnice textury najdete v následujících tématech nebo v sadě SDK spravovaného rozhraní Direct3D.  
  
 Následující příklad ukazuje, jak vytvořit jeden obličej systému model datové krychle v kódu procedury. Všimněte si, že můžete nakreslit celé datové krychle jako jeden GeometryModel3D; v tomto příkladu kreslí datové krychle pro rozpoznávání tváře jako modelu jedinečných aby bylo možné použít samostatné textury pro každý obličej později.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## <a name="applying-materials-to-the-model"></a>Použití materiálu na modelu  
  
 Pro sítě, aby vypadala jako 3D objekt musí mít použité textury na povrchu určené jeho vrcholů a trojúhelníky tak může být lit a plánovaných pomocí fotoaparátu/kamery. V [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], je použít <xref:System.Windows.Media.Brush> třídu použít barvy, vzorů, přechody nebo jiné vizuální obsah pro oblasti obrazovky.  Vzhled [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objekty, ale funkce modelu osvětlení, ne jenom barvu nebo vzorek použije k nim. Objekty reálného světa odrážel světlo odlišně v závislosti na kvalitu svých rovin: lesklý a lesklý povrch nevypadají, stejně jako hrubý nebo matné povrchy a vypadá, že některé objekty a chránit před světlo, zatímco ostatní záře. Můžete použít stejné štětce k [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objekty, které můžete provést u [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] objekty, ale nelze použít přímo.  
  
 Chcete-li definovat vlastnosti povrchu model, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá <xref:System.Windows.Media.Media3D.Material> abstraktní třídy. Některé vlastnosti vzhledu povrchu modelu určit konkrétní podtřídy materiálu a každý také poskytuje vlastnost štětce, ke kterému lze předat SolidColorBrush, TileBrush nebo VisualBrush.  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial> Určuje, jestli štětec použité pro model, jakoby byly rozptýleně lit tento model. Pomocí DiffuseMaterial nejvíce podobá pomocí štětců přímo na [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] modely; zařízení Surface modelu neodráží světla, jako když shiny.  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial> Určuje, jestli štětec použité pro model, jakoby povrch modelu bylo obtížné nebo zářivý a schopné odrazu světla. Do jaké míry, do kterého bude navrhovat textury tohoto reflektivní kvality nebo "lesku," můžete nastavit tak, že zadáte hodnotu <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> vlastnost.  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial> Umožňuje určit, že textury se použije jako by šlo model byly generování světla rovno barvou štětce. To nepoužívá model světla; ale se bude účastnit jinak stínový provoz, než kdyby texturou DiffuseMaterial nebo SpecularMaterial.  
  
 Pro lepší výkon, zadní plochy z <xref:System.Windows.Media.Media3D.GeometryModel3D> (tváří, které jsou mimo zobrazení, protože jde na opačnou stranu modelu z fotoaparátu/kamery) jsou vyřazeny z scény.  Chcete-li určit <xref:System.Windows.Media.Media3D.Material> Pokud chcete použít pro odstranění odvrácených modelu jako rovině, nastavte modelu <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> vlastnost.  
  
 K dosažení některé surface kvality, jako je zářivých nebo reflektivní efekty, můžete použít několik různých štětce k modelu v daný okamžik. Můžete použít a opakovaně používat více materiály s použitím <xref:System.Windows.Media.Media3D.MaterialGroup> třídy. Podřízené objekty daného MaterialGroup nejprve použijí se poslední v několik průchodů za vykreslování.  
  
 Následující příklady kódu ukazují, jak použít plnou barvu a kresby jako štětce k [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modely.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## <a name="illuminating-the-scene"></a>Osvětlení scény.  
 Aktivuje v [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafiky udělat, co dělat světla v reálném světě: využívají povrchy viditelné. Do bodu, další indikátory určit, jaké části scény budou zahrnuty v projekci. Světle objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvářet nejrůznější světla a stínování efekty a jsou vytvořeny podle chování různých indikátorů reálného světa. Musí obsahovat alespoň jeden světla ve scéně, nebo se nebude zobrazovat žádné modely.  
  
 Tyto indikátory jsou odvozeny od základní třídy <xref:System.Windows.Media.Media3D.Light>:  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: Poskytuje osvětlením osvětluje všechny objekty, které jsou rovnoměrně bez ohledu na jejich umístění a orientaci.  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: Osvětluje jako vzdálené zdroje světla.  Směrové světlo mít <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> stanoveno Vector3D, ale žádné zadané umístění.  
  
- <xref:System.Windows.Media.Media3D.PointLight>: Osvětluje jako blízké světelného zdroje. PointLights polohy a přetypovat světla z této pozici. V závislosti na jejich umístění a vzdálenost s ohledem na světla jsou osvětlená objekty na scéně. <xref:System.Windows.Media.Media3D.PointLightBase> Zpřístupňuje <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> vlastnost, která určuje vzdálenost, jejichž překročení nebudou modely osvětlení světla. PointLight také poskytuje zeslabení vlastnosti, které určují, jak světla intenzita snižuje vzdálenost. Můžete určit konstantní lineární či kvadratické interpolace pro útlum světla.  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: dědí z <xref:System.Windows.Media.Media3D.PointLight>. Světelné kužele osvětlení jako PointLight a mít umístění a směrování. Microsoft Office project světla v oblasti ve tvaru kužel nastavil <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> a <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> vlastnosti, které jsou zadány ve stupních.  
  
 Světla jsou <xref:System.Windows.Media.Media3D.Model3D> objekty, dají se transformovat a animovat vlastnosti světla, včetně umístění, barvy, směr a rozsah.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## <a name="transforming-models"></a>Transformace modelů  
 Při vytváření modely mají konkrétní místě ve scéně. Tyto modely přesouvat ve scéně, jejich otočení nebo změnit jejich velikost, není praktické změnit vrcholy, které definují modelů sami.  Místo toho jenom jako v [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], použití transformací na modely.  
  
 Každý objekt modelu má <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> vlastností, pomocí kterého můžete přecházet, znovu zorientovat nebo velikost modelu.  Při použití transformace efektivně posun všechny body daného modelu libovolné vektoru nebo hodnotu zadanou pomocí transformace. Jinými slovy jsme transformovali souřadnicového prostoru ve kterém je model definovaný ("model místo"), ale nedošlo ke změně hodnoty, které tvoří geometrie modelu v souřadnicový systém celý scény ("místa na světě").  
  
 Další informace o transformaci modelů najdete v tématu [přehled 3D transformací](3-d-transformations-overview.md).  
  
<a name="animations"></a>   
## <a name="animating-models"></a>Animace modelů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Implementace podílí na stejném systému časování a animace jako [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafiky. Jinými slovy animace 3D scény, animujte vlastnosti z jeho modelů. Je možné pro animaci vlastnosti primitivních elementů přímo, ale je obvykle jednodušší animace transformace, které se mění pozice nebo vzhled modelů. Protože transformací lze použít u <xref:System.Windows.Media.Media3D.Model3DGroup> objekty a také jednotlivé modely, je možné použít jednu sadu animace podřízený Model3DGroup a další sadu animace do skupiny podřízených objektů. Animace vlastnosti osvětlení scény v můžete také dosáhnout různých vizuálních efektů. Nakonec můžete animovat projekce sama tak, že animace polohy kamery nebo pole zobrazení. Základní informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] načasování a animace systému, najdete v článku [přehled animace](animation-overview.md), [přehled scénářů](storyboards-overview.md), a [přehled Zablokovatelných objektů](../advanced/freezable-objects-overview.md)témata.  
  
 Pro animaci objektu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vytvoření časové osy, definujte animace (což je ve skutečnosti změn v některá z hodnot vlastností v průběhu času) a určete vlastnost, pro kterou chcete použít animace. Protože všechny objekty do [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scény jsou podřízené objekty daného <xref:System.Windows.Controls.Viewport3D>, zacílené žádné animace má být použita do scény vlastnosti jsou vlastnosti z vlastností objektu Viewport3D.  
  
 Předpokládejme, že má být model pravděpodobně wobble na místě. Můžete se rozhodnout pro použití <xref:System.Windows.Media.Media3D.RotateTransform3D> modelu a animovat osy otočení z jednoho vektor do jiného. Následující příklad kódu ukazuje použití Vector3DAnimation s vlastností osy Rotation3D transformaci, za předpokladu, že RotateTransform3D bude jedním z několika transformací použitá pro model s TransformGroup.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## <a name="add-3-d-content-to-the-window"></a>V okně Přidání 3D obsahu  
 Vykreslení scény, přidání modelů a indikátorů do <xref:System.Windows.Media.Media3D.Model3DGroup>, nastavte <xref:System.Windows.Media.Media3D.Model3DGroup> jako <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> z <xref:System.Windows.Media.Media3D.ModelVisual3D>. Přidat <xref:System.Windows.Media.Media3D.ModelVisual3D> k <xref:System.Windows.Controls.Viewport3D.Children%2A> kolekce <xref:System.Windows.Controls.Viewport3D>. Přidat bezpečnostních kamer <xref:System.Windows.Controls.Viewport3D> nastavením jeho <xref:System.Windows.Controls.Viewport3D.Camera%2A> vlastnost.  
  
 Nakonec přidejte <xref:System.Windows.Controls.Viewport3D> do okna. Když <xref:System.Windows.Controls.Viewport3D> je součástí obsahu prvku rozložení jako plátno, určete velikost Viewport3D nastavením jeho <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti (zděděno z <xref:System.Windows.FrameworkElement>).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [Přehled 3D transformací](3-d-transformations-overview.md)
- [Maximalizace výkonu WPF 3D](maximize-wpf-3d-performance.md)
- [Témata s postupy](3-d-graphics-how-to-topics.md)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
