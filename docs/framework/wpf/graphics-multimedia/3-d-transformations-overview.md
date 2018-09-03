---
title: Přehled 3D transformací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D transformations
- transformations [WPF], 3-D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
ms.openlocfilehash: d27e1bda296a153343b450c84c65fa35d55d72f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483720"
---
# <a name="3-d-transformations-overview"></a>Přehled 3D transformací
Toto téma popisuje způsob použití transformací na 3D modelů v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafiky systému. Transformace umožňuje vývojářům změnit umístění, velikost a orientaci modely beze změny základní hodnoty, které jejich definování.  
  

  
## <a name="3-d-coordinate-space"></a>3D souřadnicového prostoru  
 3D grafiky v obsahu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapouzdřena v elementu, <xref:System.Windows.Controls.Viewport3D>, který mohl podílet na struktuře dvojrozměrné elementu. Grafika systému považuje za Viewport3D dvojrozměrné vizuální prvky jako řada dalších v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Viewport3D funguje jako okno – oblast zobrazení – do 3D scény. Přesněji řečeno je povrch, na kterém je předpokládané 3D scény.  I když používáte Viewport3D s jinými objekty 2D kreslení v stejný graf scén nelze interpenetrate 2D a 3D objektů v rámci Viewport3D. V následující diskuse souřadnicového prostoru popsané obsažen v elementu Viewport3D.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Souřadnicový systém pro 2D grafika vyhledá počátek v levém horním rohu vykreslovací plochu (obvykle obrazovky). V systému 2D hodnoty na ose x kladné pokračovat na pravé straně a osy y kladné hodnoty přejděte dolů. V 3D souřadnicový systém ale původ je umístěn ve středu obrazovky, s hodnoty na ose x kladné pokračuje na pravé straně, ale hodnoty y pozitivní místo toho pokračuje směrem nahoru a osy z kladné hodnoty pokračuje směrem ven z původního zdroje, směrem k v prohlížeči.  
  
 ![Systémy souřadnic](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem-1")  
Porovnání souřadnicový systém  
  
 Místo definované tyto osy je bez pohybu rámec pro 3D objekty v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Jak vytvářet modely v tomto prostoru a vytvoření světla a jejich zobrazení bezpečnostních kamer, je užitečné k rozlišení tohoto bez pohybu referenčním rámcem nebo "místa na světě," z místní rámec, který vytvoříte pro každý model, při použití transformace. Nezapomeňte, že objekty v prostoru světa mohou vypadají úplně jinak, nebo nebude viditelné ve všech, v závislosti na světla a fotoaparát nastavení, ale pozice kamery nezmění umístění objektů v prostoru světa.  
  
## <a name="transforming-models"></a>Transformace modelů  
 Při vytváření modely mají konkrétní místě ve scéně. Tyto modely přesouvat ve scéně, jejich otočení nebo změnit jejich velikost, není praktické změnit vrcholy, které definují modelů sami. Místo toho stejně jako u 2D, při aplikování transformací na modely.  
  
 Každý objekt modelu má <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> vlastností, pomocí kterého můžete přecházet, znovu zorientovat nebo velikost modelu. Při použití transformace efektivně posun všechny body daného modelu podle libovolné vektoru nebo hodnoty určené transformace. Jinými slovy jsme transformovali souřadnicového prostoru ve kterém je model definovaný ("model místo"), ale nedošlo ke změně hodnoty, které tvoří geometrie modelu v souřadnicový systém celý scény ("místa na světě").  
  
## <a name="translation-transformations"></a>Překlad transformace  
 3D transformace dědí z abstraktní základní třída <xref:System.Windows.Media.Media3D.Transform3D>; mezi ně patří třídy afinní transformace <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D>, a <xref:System.Windows.Media.Media3D.RotateTransform3D>. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D systém také poskytuje <xref:System.Windows.Media.Media3D.MatrixTransform3D> třídu, která vám umožní určit stejné transformace v stručnější maticové operace.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D> Přesune všechny body v Model3D ve směru posunu vektoru zadáte <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>, a <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> vlastnosti. Například přiřazen jeden vrchol datovou krychlí při (2,2,2), posun vektor (0,1.6,1) by posunula tento vrchol (2,2,2) na (2,3.6,3). Vrchol datové krychle je stále místa (2,2,2) v modelu, ale nyní toto místo modelu došlo ke změně jeho vztah k místa na světě tak, aby místo (2,2,2) v modelu (2,3.6,3) v prostoru světa.  
  
 ![Obrázek překlad](../../../../docs/framework/wpf/graphics-multimedia/media/transforms-translate.png "přeložit transformace")  
Překlad s posunem  
  
 Následující příklady kódu ukazují, jak použít překlad.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Transformace měřítka  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D> Změní měřítko modelu pomocí zadaného rozsahu vektoru s odkazem na středový bod. Zadejte jednotné škálování, které se škáluje podle stejné hodnoty v OS X, Y a ke změně velikosti modelu proporcionálně modelu. Například nastavení transformace <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> vlastnosti 0,5, znamená poloviny velikostí modelu; nastavení stejných vlastností na 2 zdvojnásobuje její škálování do všech tří OS.  
  
 ![Jednotné objekt ScaleTransform3D](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Příklad ScaleVector  
  
 Zadáním nerovnoměrné škálování transformace – škálování transformace, jehož hodnoty X, Y a nejsou všechny stejné – může způsobit modelu roztažení nebo smlouvy v jedné nebo dvou dimenzích, aniž by to ovlivnilo ostatní. Například nastavení <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> na hodnotu 1, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> na 2, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> na hodnotu 1 způsobí transformovaný modelu poklikejte na výšku, ale zůstanou nezměněné podél osy X a Z.  
  
 Ve výchozím nastavení objekt ScaleTransform3D způsobí, že vrcholů můžete rozbalit nebo sbalit o původu (0,0,0). Pokud model, který chcete transformovat není vykresleno z původního zdroje, ale škálování modelu z původního zdroje nebudou se škálovat modelu "." Místo toho když vrcholů modelu se násobí škálování vektoru, operace škálování nebude mít vliv překladu modelu, stejně jako vertikální snížení jeho kapacity.  
  
 ![Tři datové krychle škálovat s středový bod zadaný](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Příklad Center škálování  
  
 Škálování modelu "místo", určete center modelu nastavením objekt ScaleTransform3D <xref:System.Windows.Media.ScaleTransform.CenterX%2A>, <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> vlastnosti. Tím se zajistí, že systém grafiky škáluje prostoru model a potom převede jej na střed na určeném <xref:System.Windows.Media.Media3D.Point3D>. Naopak pokud začlenění modelu o původu a určit různé středový bod očekávejte modelu přeložit od počátku.  
  
## <a name="rotation-transformations"></a>Transformace rotace  
 Model v 3D můžete otočit několika různými způsoby. Transformace rotace typické určuje osy a úhel otočení kolem osy. <xref:System.Windows.Media.Media3D.RotateTransform3D> Třída umožňuje definovat <xref:System.Windows.Media.Media3D.Rotation3D> s jeho <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> vlastnost. Potom zadejte <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> vlastnosti Rotation3D v tomto případě <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>, chcete-li definovat transformace. Následující příklady otočí model o 60 stupňů okolo osy Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Poznámka:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D je pravoruký systém, což znamená, že hodnotu kladný úhel otočení výsledkem proti směru hodinových ručiček otočení kolem osy.  
  
 Osa úhel otočení předpokládají otočení o původu, pokud není zadána hodnota pro <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>, a <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> vlastnosti RotateTransform3D. Stejně jako u škálování, je vhodné mít na paměti, že otočení transformuje celý souřadnicového prostoru modelu. Pokud modelu nebyla vytvořena o původu, nebo byl přeložen dříve, otočení může "otáčení" o původu místo otáčení na místě.  
  
 ![Otočení pomocí nový středový bod](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Otočení pomocí nové centrum zadat  
  
 Otočí model "na místě", zadejte skutečný center modelu jako střed otáčení. Protože geometrie modelována obvykle o původu, můžete získat očekávaný výsledek sadu transformací pro nejčastěji nejprve velikosti modelu (vertikální snížení jeho kapacity), pak nastavením jeho orientaci (otočení) a nakonec ji přesunout do požadovaného umístění ( převod je).  
  
 ![Rotaci v x 60 stupňů&#45; a y&#45;osy](../../../../docs/framework/wpf/graphics-multimedia/media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Příklad otočení  
  
 Osa – úhel otočení fungovat dobře pro statické transformace a některé animace. Zvažte však otáčení modelu 60 stupňů kolem osy X, potom 45 stupňů kolem osy Z datové krychle. Popíšete této transformace jako dva samostatné afinní transformace nebo matice. Ale může být obtížné plynulé animace otočení definované tímto způsobem. I když počáteční a koncovou pozicí počítají tak, že kterýkoliv přístup modelu jsou stejná, zprostředkující pozice provedenou na základě modelu jsou výpočetně nejistoty. Kvaternionů představují alternativní způsob pro výpočet interpolaci mezi počátečním a koncovým otočení.  
  
 Quaternion představuje osy v 3D prostoru a otočení kolem osy. Například quaternion může představovat (1,1,2) osy a otočení 50 stupňů. Napájení kvaternionů při definování rotace pochází z těchto dvou operací, které můžete provádět s nimi: složení a interpolace. Složení dvou kvaternionů použitý pro geometrii znamená "otočit geometrie kolem axis2 rotation2 a otočení kolem axis1 podle rotation1." Pomocí sestavení můžete kombinovat dva rotace na geometrii získat jednotné quaternion, která reprezentuje výsledek. Protože quaternion interpolace můžete vypočítat hladký a přiměřené cestu z jednoho osy a orientace na jiný, můžete lze interpolovat z původní pro složené quaternion zajistit hladký přechod z jednoho na druhý umožňuje animace transformace. U modelů, které má být animován, určíte cílové místo <xref:System.Windows.Media.Media3D.Quaternion> pro otočení pomocí <xref:System.Windows.Media.Media3D.QuaternionRotation3D> pro <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> vlastnost.  
  
## <a name="using-transformation-collections"></a>Pomocí kolekcí transformace  
 Při sestavování scény, je běžné použití více než jedna transformace na model. Přidat transformace na <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> kolekce <xref:System.Windows.Media.Media3D.Transform3DGroup> třídy k seskupení transformuje jednoduše použít na různé modely ve scéně. Často je vhodné pro opětovné použití transformace v několika různých skupin, podobně jako když, můžete znovu použít model s použitím jinou sadu transformací pro každou instanci. Všimněte si, že je důležité pořadí, ve kterém transformace jsou přidána do kolekce: transformace v kolekci jsou použity z první na poslední.  
  
## <a name="animating-transformations"></a>Animace transformace  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D implementace podílí na stejném systému časování a animace jako 2D grafika. Jinými slovy animace 3D scény, animujte vlastnosti z jeho modelů. Je možné pro animaci vlastnosti primitivních elementů přímo, ale je obvykle jednodušší animace transformace, které se mění pozice nebo vzhled modelů. Protože transformací lze použít u <xref:System.Windows.Media.Media3D.Model3DGroup> objekty a také jednotlivé modely, je možné použít jednu sadu animace podřízených položek Model3Dgroup a další sadu animace do skupiny objektů.  Základní informace o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] načasování a animace systému, naleznete v tématu [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Pro animaci objektu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], vytvoření časové osy, definujte animace (což je ve skutečnosti změn v některá z hodnot vlastností v průběhu času) a určete vlastnost, pro kterou chcete použít animace. Tato vlastnost musí být vlastnost FrameworkElement. Vzhledem k tomu, že všechny objekty ve 3D scéně jsou podřízené objekty daného Viewport3D, jsou vlastnosti zacílené žádné animace, který chcete použít na scénu vlastnosti z vlastností objektu Viewport3D. Je velmi důležité spolupracovat na vlastnost cesty pro animaci pečlivě, protože syntaxe může být podrobné.  
  
 Předpokládejme, že chcete k otočení objektu v místě, ale také použít houpavých zveřejnit informace o objekt, který chcete zobrazit. Můžete použít RotateTransform3D modelu a animovat osy otočení z jednoho vektor do jiného. Následující příklad kódu ukazuje použití <xref:System.Windows.Media.Animation.Vector3DAnimation> s vlastností osy Rotation3D transformaci, za předpokladu, že RotateTransform3D bude jedním z několika transformací použitá pro model s <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Podobná syntaxe umožňuje cílit na jiné vlastnosti transformace se přesunout nebo změnit velikost objektu.  Například můžete použít <xref:System.Windows.Media.Animation.Point3DAnimation> ScaleCenter vlastnosti na transformace měřítka způsobit modelu plynule narušit jeho tvar.  
  
 Ačkoli předchozí příklady transformace vlastnosti <xref:System.Windows.Media.Media3D.GeometryModel3D>, je také možné transformovat vlastnosti další modely ve scéně.  Podle animace překlady použít u objektů světla, například vytvořením přesunutí světla a efekty stínování, která můžou výrazně změnit vzhled vašich modelů.  
  
 Vzhledem k tomu kamery také modely, je možné transformovat také vlastnosti kamery.  Zatímco určitě můžete změnit vzhled scény pomocí transformace fotoaparátu umístění nebo rovině vzdálenosti – v důsledku toho transformace projekce celý scény – mějte na paměti, že mnoho účinky dosáhnout tímto způsobem nemusí mít tolik "visual smysl" do prohlížeče jako transformace použít pro umístění nebo umístění modelů ve scéně.  
  
## <a name="see-also"></a>Viz také  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Ukázka 2D transformace](https://go.microsoft.com/fwlink/?LinkID=158252)
