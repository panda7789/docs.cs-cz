---
title: "Přehled 3D transformací"
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
- 3-D transformations
- transformations [WPF], 3-D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 431f4abd55da3b8c4e348d3abbd107e2f6344d5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="3-d-transformations-overview"></a>Přehled 3D transformací
Toto téma popisuje postup použití transformace na 3D modely v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafika systému. Transformace umožňuje vývojářům změnit umístění, změnit velikost a orientaci modely beze změny základní hodnoty, které je definovat.  
  

  
## <a name="3-d-coordinate-space"></a>3D souřadnicového prostoru  
 3D grafický obsahu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je zapouzdřené v elementu, <xref:System.Windows.Controls.Viewport3D>, který mohl účastnit strukturu dvourozměrná element. Grafika systému považuje za dvourozměrná vizuální prvek jako mnoho dalších v Viewport3D [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Viewport3D funguje jako okno – zobrazení – do 3D scény. Přesněji řečeno je prostor, na kterém se promítá 3D scény.  I když používáte Viewport3D s jinými 2-D kreslení objekty ve stejném grafu scény nelze interpenetrate 2D a 3D objektů v rámci Viewport3D. V následující diskusi souřadnicového prostoru popsané je obsažený v prvku Viewport3D.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Souřadnicový systém pro 2D grafiky vyhledá počátek v levém horním rohu na povrch vykreslování (obvykle na obrazovce). V systému 2-D hodnoty osy x kladné pokračovat doprava a osy y kladné hodnoty pokračovat směrem dolů. V 3D souřadnicový systém ale počátek nachází v centru na obrazovce s hodnotami kladné osy x vpravo budete pokračovat, ale budete pokračovat směrem nahoru místo hodnoty osy y kladné a kladné osy z hodnoty budete i pokračovat z tohoto počátku směrem k v prohlížeči.  
  
 ![Systémy souřadnic](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem-1")  
Porovnání souřadnicový systém  
  
 Místo definované tyto osy je stojící rámec pro 3D objekty v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Jak vytvářet modely z tohoto prostoru a vytvořit indikátory a kamery k jejich zobrazení, je užitečné k rozlišení tento stojící rámec nebo "world prostor," z místní rámec, který vytvoříte pro každý model, při použití transformace. Nezapomeňte také, že objekty v prostoru world pravděpodobně zcela liší, nebo není viditelná vůbec, v závislosti na světlým a fotoaparát nastavení, ale pozice kamery nezmění umístění objekty v prostoru world.  
  
## <a name="transforming-models"></a>Transformace modely  
 Při vytváření modelů mají konkrétního umístění v scény. Pohyb tyto modely v scény, pro jejich otočení nebo změnit jejich velikost není praktické, chcete-li změnit vrcholy, které definují modely sami. Místo toho jako v případě 2-D, použijete transformace modelů.  
  
 Každý objekt modelu má <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> vlastností, pomocí kterého můžete přesunout, znovu orientaci nebo změnit velikost modelu. Při použití transformace můžete efektivně posunut všechny body modelu ať vektoru nebo hodnota je zadána pro transformaci. Jinými slovy, jste transformovat souřadnicového prostoru, ve kterém je model definované ("model místo"), ale nedošlo ke změně hodnoty, které tvoří geometrie modelu v souřadnicový systém celý scény ("world prostor").  
  
## <a name="translation-transformations"></a>Překlad transformace  
 3D transformace dědí z abstraktní základní třída <xref:System.Windows.Media.Media3D.Transform3D>; zahrnují tříd afinní transformace <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D>, a <xref:System.Windows.Media.Media3D.RotateTransform3D>. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D systém také poskytuje <xref:System.Windows.Media.Media3D.MatrixTransform3D> třídu, která vám umožní zadat stejné transformace v operacích přesnější matice.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D>Přesune všechny body v Model3D ve směru posunutí vektoru zadáte pomocí <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>, a <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> vlastnosti. Například uveden jednoho vrcholu datovou krychli na (2,2,2), je posunutí vektor (0,1.6,1) by přesuňte této vrchol (2,2,2) (2,3.6,3). Vrchol datové krychle je stále místa (2,2,2) v modelu, ale nyní toto místo modelu došlo ke změně jeho relaci místa na světě tak, aby místo (2,2,2) v modelu (2,3.6,3) v prostoru world.  
  
 ![Obrázek překlad](../../../../docs/framework/wpf/graphics-multimedia/media/transforms-translate.png "převede transformací")  
Překlad s posunem  
  
 Následující příklady kódu ukazují, jak použít překlad.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Škálování transformace  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D>Změní měřítko modelu pomocí zadaného škálování vektoru nese odkaz centrálního bodu. Zadejte uniform škálování, které se stejnou hodnotou v osy X, Y a chcete-li změnit velikost modelu úměrně škáluje modelu. Například nastavení pro transformaci <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> vlastnosti 0,5 poloviny velikost modelu; nastavení stejné vlastnosti 2 zdvojnásobí jeho měřítka ve všechny tři osy.  
  
 ![Uniform objekt ScaleTransform3D](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Příklad ScaleVector  
  
 Zadáním neuniformní škálování transformaci – škálování transformace, jejichž hodnoty X, Y a nejsou všechny stejné – může způsobit modelu k roztažení nebo stlačení v jedné nebo dvou dimenzí bez vlivu jiné. Například nastavení <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> hodnotu 1, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> na 2, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> na hodnotu 1 způsobí transformovaných modelu poklikejte na výšku, ale zůstanou nezměněny podél OS X a Z.  
  
 Ve výchozím nastavení objekt ScaleTransform3D způsobí, že vrcholy k roztažení nebo stlačení o zdroji (0,0,0). Pokud model, který má být transformace není vykreslován z tohoto počátku, ale škálování modelu z tohoto počátku nelze škálovat modelu "v umístění." Místo toho když vrcholy modelu se násobí vektoru škálování, operace škálování bude mít vliv překladu modelu, stejně jako jeho škálování.  
  
 ![Tři datové krychle změněna pomocí Zadaný bod center](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Příklad Center škálování  
  
 Škálování model "v umístění", zadejte center modelu nastavením objekt ScaleTransform3D <xref:System.Windows.Media.ScaleTransform.CenterX%2A>, <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> vlastnosti. To zajišťuje, že systém grafiky škáluje místo modelu a potom převede jej na střed na určeném <xref:System.Windows.Media.Media3D.Point3D>. Pokud jste vytvořili model o zdroji a zadáte jiný centrálního bodu, a naopak, měli vidět modelu přeložit od počátku.  
  
## <a name="rotation-transformations"></a>Otočení transformace  
 Model v 3D můžete otáčet několika různými způsoby. Typické otočení transformace určuje osy a úhel otočení okolo této osy. <xref:System.Windows.Media.Media3D.RotateTransform3D> Třída umožňuje definovat <xref:System.Windows.Media.Media3D.Rotation3D> s jeho <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> vlastnost. Potom zadejte <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> vlastnosti Rotation3D, v tomto případě <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>, pro definici transformace. Následující příklady otočení model o 60 stupňů okolo osy Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Poznámka:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D je pravou rukou systém, což znamená, že úhel kladnou hodnotu pro rotaci kolem výsledkem proti směru hodinových ručiček otočení osy.  
  
 Osa úhel otočení předpokládá otočení o původu, pokud není zadána hodnota pro <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>, a <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> vlastnosti RotateTransform3D. Stejně jako u škálování, je vhodné mít na paměti, že je oběh transformuje celý souřadnicového prostoru modelu. Pokud model nebyl vytvořen o zdroji, nebo byl přeložen dříve, je oběh může "kontingenční" o počátek místo otáčení na místě.  
  
 ![Otočení s novým středem](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Otočení s nové centrum zadaný  
  
 Otočit model "místo", zadejte jako střed otáčení skutečné center modelu. Protože geometry je obvykle modelován o původu, nejčastěji získáte očekávaný výsledek sadu transformace tak, že první změna velikosti modelu (škálování ji), potom nastavení její orientace (otáčení ho) a nakonec ani ji přesunout do požadovaného umístění ( Převod ji).  
  
 ![Rotaci kolem 60 stupňů v x & č. 45; a y & č. 45; osy](../../../../docs/framework/wpf/graphics-multimedia/media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Příklad otočení  
  
 Osy úhel otočení fungovat i pro statické transformace a některé animace. Zvažte však otáčení model 60 stupňů okolo osy X, potom 45 stupňů kolem osy Z datové krychle. Můžete popsat Tato transformace jako dva samostatné afinní transformace nebo matice. Však může být obtížné plynule animace rotaci kolem definované tímto způsobem. I když počáteční a koncová pozice modelu vypočítávají podle buď přístup jsou stejné, jsou u neví zprostředkující pozic provedenou modelu. Quaternions představují alternativní způsob výpočetní interpolace mezi počáteční a koncová rotaci kolem.  
  
 Quaternion představuje osy v 3D místa a rotaci kolem osy. Například quaternion může představovat (1,1,2) osy a rotaci kolem 50 stupňů. Napájení quaternions' k definování otočení pochází z těchto dvou operací, které můžete provádět s nimi: složení a interpolace. Složení dvě quaternions u geometry znamená "otočit geometrie kolem axis2 podle rotation2, a otočit kolem axis1 podle rotation1." Pomocí složení můžete kombinovat dvě otočení na geometrie získat jeden quaternion, který představuje výsledek. Protože quaternion interpolace můžete vypočítat smooth a přiměřené cestu z jedné osy a orientaci na jiný, můžete můžete interpolovat z původního do složený quaternion k dosažení plynulý přechod z jednoho na druhý umožňuje animace transformace. Pro modely, které chcete animace, můžete zadat cíl <xref:System.Windows.Media.Media3D.Quaternion> pro otáčení pomocí <xref:System.Windows.Media.Media3D.QuaternionRotation3D> pro <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> vlastnost.  
  
## <a name="using-transformation-collections"></a>Pomocí kolekcí transformace  
 Při sestavování scény, je běžné použít více než jeden transformace k modelu. Přidat transformace na <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> kolekce <xref:System.Windows.Media.Media3D.Transform3DGroup> třída k seskupení transformuje pohodlně Pokud chcete použít pro různé modely v scény. Často je vhodnější použít transformaci v několika různých skupinách mnohem způsobem, že můžete opakovaně použít model použitím jinou sadu transformace na každou instanci. Všimněte si, že je důležité pořadí, ve kterém jsou transformace přidat do kolekce: soubory v kolekci použije z první poslední.  
  
## <a name="animating-transformations"></a>Animace transformace  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D implementace účastní na stejném načasování a animace systému jako 2D grafiky. Jinými slovy použije animaci 3D scény, použije animaci vlastnosti její modely. Je možné přímo animace vlastnosti primitivních elementů, ale je obvykle jednodušší animace transformace, které se změny umístění nebo vzhled modelů. Protože transformace je možné použít k <xref:System.Windows.Media.Media3D.Model3DGroup> objekty a také jednotlivé modely, je možné použít jednu sadu animací podřízené objekty daného Model3Dgroup a další sadu animace do skupiny objektů.  Základní informace o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] načasování a animace systému, najdete v části [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Pro objekt v animaci [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], vytvoření časové osy, definovat animace (což je ve skutečnosti změnu v hodnotě některé vlastnosti v čase) a určete vlastnost na kterou budou používány animace. Tato vlastnost musí být vlastnost Objekt FrameworkElement. Protože všechny objekty v 3D scény jsou podřízené Viewport3D, jsou vlastnosti cílem žádné animace, kterou chcete použít pro scény vlastnosti vlastnosti Viewport3D. Je důležité pro práci se cesta k vlastnosti pro animaci pečlivě, protože syntaxe může být verbose.  
  
 Předpokládejme, že chcete otočení objektu na místě, ale také použít houpavých vystavit další objekt, který chcete zobrazit. Je možné použít RotateTransform3D do modelu a použije animaci ose otočení z jednoho vektor do jiného. Následující příklad kódu ukazuje použití <xref:System.Windows.Media.Animation.Vector3DAnimation> k vlastnosti osy transformaci Rotation3D, za předpokladu, že RotateTransform3D být jedním z několika transformací použitá pro model s <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Použijte podobné syntaxi pro ostatní vlastnosti transformace chcete přesunout nebo změnit velikost objektu.  Například může použít <xref:System.Windows.Media.Animation.Point3DAnimation> pro vlastnost ScaleCenter na škálování transformace způsobí model plynule narušit jeho tvaru.  
  
 I když v předchozích příkladech transformace vlastnosti <xref:System.Windows.Media.Media3D.GeometryModel3D>, je také možné vlastnosti jinými modely v scény transformace.  Pomocí animace překlady u světla objekty, například vytvoříte přesunutí světlým a stínové účinky, které můžete výrazně změnit vzhled modely.  
  
 Protože kamery jsou také modely, je možné transformovat také fotoaparátu vlastnosti.  Zatímco můžete určitě změnit vzhled scény transformace fotoaparát umístění nebo roviny vzdálenosti – ve skutečnosti transformace projekce celý scény – Všimněte si, že mnoho o důsledcích dosáhnout tímto způsobem nemusí mít tolik "visual smysl" do prohlížeče jako transformace použít pro umístění nebo umístění modely v scény.  
  
## <a name="see-also"></a>Viz také  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Transformuje – přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Ukázka 2-D transformací](http://go.microsoft.com/fwlink/?LinkID=158252)
