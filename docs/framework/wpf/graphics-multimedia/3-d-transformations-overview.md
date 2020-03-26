---
title: Přehled 3D transformací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D transformations
- transformations [WPF], 3D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
ms.openlocfilehash: 0efd6d247f23760c878c82cc92e99f1b83c1b9d2
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112346"
---
# <a name="3d-transformations-overview"></a>Přehled 3D transformací
Toto téma popisuje, jak aplikovat transformace na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D modely v grafickém systému. Transformace umožňují vývojáři změnit umístění, změnit velikost a změnit orientaci modelů beze změny základních hodnot, které je definují.  

## <a name="3d-coordinate-space"></a>3D souřadný prostor  
 Obsah 3D [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafiky v aplikaci je <xref:System.Windows.Controls.Viewport3D>zapouzdřen v elementu , který se může účastnit dvourozměrné struktury prvků. Grafický systém zachází Viewport3D jako dvou-dimenzionální [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]vizuální prvek, stejně jako mnoho jiných v . Viewport3D funguje jako okno – výřez – do trojrozměrné scény. Přesněji řečeno, je to povrch, na kterém je promítána 3D scéna.  I když můžete viewport3D používat s jinými 2D nakreslenými objekty ve stejném grafu scény, nemůžete v rámci Výřezu3D prolínat 2D a 3D objekty. V následující diskusi je popisovaný souřadnicový prostor obsažen v elementu Viewport3D.  
  
 Souřadnicový [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systém pro 2D grafiku vyhledá počátek v levém horním rohu vykreslovacího povrchu (obvykle na obrazovce). Ve 2D systému postupují kladné hodnoty osy x doprava a kladné hodnoty osy y postupují dolů. V 3D souřadnicovém systému je však počátek umístěn ve středu obrazovky, přičemž kladné hodnoty osy x postupují doprava, ale kladné hodnoty osy y postupují nahoru a kladné hodnoty osy z postupují směrem od počátku směrem ven diváka.  
  
 ![Souřadné systémy](./media/coordsystem-1.png "CoordSystem-1")  
Porovnání souřadnicových systémů  
  
 Prostor definovaný těmito osami je stacionární referenční [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]rámec pro 3D objekty v . Při vytváření modelů v tomto prostoru a vytváření světel a kamer pro jejich zobrazení je užitečné odlišit tento stacionární referenční rámec neboli "světový prostor" od místního referenčního rámce, který vytvoříte pro každý model, když na něj použijete transformace. Nezapomeňte také, že objekty ve světovém prostoru mohou vypadat úplně jinak, nebo nemusí být viditelné vůbec, v závislosti na nastavení světla a kamery, ale pozice kamery nemění umístění objektů ve světovém prostoru.  
  
## <a name="transforming-models"></a>Transformace modelů  
 Když vytváříte modely, mají určité umístění ve scéně. Chcete-li tyto modely přesunout ve scéně, otočit je nebo změnit jejich velikost, není praktické měnit vrcholy, které definují samotné modely. Místo toho, stejně jako ve 2D, použijete transformace na modely.  
  
 Každý objekt modelu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> má vlastnost, se kterou můžete přesunout, přeorientovat nebo změnit velikost modelu. Když aplikujete transformaci, efektivně odsadíte všechny body modelu podle jakéhokoli vektoru nebo hodnoty určené transformací. Jinými slovy jste transformovali souřadnicový prostor, ve kterém je definován model ("modelový prostor"), ale nezměnili jste hodnoty, které tvoří geometrii modelu v souřadnicovém systému celé scény ("světový prostor").  
  
## <a name="translation-transformations"></a>Transformace překladu  
 3D transformace dědí z <xref:System.Windows.Media.Media3D.Transform3D>abstraktní základní třídy ; patří mezi ně podobné <xref:System.Windows.Media.Media3D.TranslateTransform3D> <xref:System.Windows.Media.Media3D.ScaleTransform3D>třídy <xref:System.Windows.Media.Media3D.RotateTransform3D>transformace , a . [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D systém také <xref:System.Windows.Media.Media3D.MatrixTransform3D> poskytuje třídu, která umožňuje zadat stejné transformace v stručnější matice operace.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D>přesune všechny body v Modelu3D ve směru vektoru odsazení, který určíte pomocí vlastností <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>a. <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> Například vzhledem k jednomu vrcholu krychle na (2,2,2), posun vektor (0,1,6,1) by přesunout tento vrchol (2,2,2) na (2,3.6,3). Vrchol krychle je stále (2,2,2) v modelovém prostoru, ale nyní, když modelový prostor změnil svůj vztah ke světovému prostoru tak, aby (2,2,2) v modelovém prostoru byl (2,3.6,3) ve světovém prostoru.  
  
 ![Číslo překladu](./media/transforms-translate.png "Transformace-Přeložit")  
Překlad s posunem  
  
 Následující příklady kódu ukazují, jak použít překlad.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Škálování transformace  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D>změní měřítko modelu o určený vektor měřítka s odkazem na středový bod. Určete jednotné měřítko, které změní měřítko modelu podle stejné hodnoty v osách X, Y a Z, chcete-li proporcionálně změnit velikost modelu. Například nastavení transformace <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> a vlastnosti 0,5 poloviny velikost modelu; nastavení stejných vlastností na 2 zdvojnásobí měřítko ve všech třech osách.  
  
 ![Jednotná scaletransform3D](./media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Příklad scalevectoru  
  
 Určením nerovnoměrné transformace měřítka – transformace měřítka, jejíž hodnoty X, Y a Z nejsou všechny stejné – můžete způsobit roztažení modelu nebo smrštění v jedné nebo dvou dimenzích, aniž by to ovlivnilo ostatní. Například nastavení <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> na <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 1, na <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 2 a na 1 způsobí, že transformovaný model zdvojnásobí výšku, ale zůstane nezměněn podél os X a Z.  
  
 Ve výchozím nastavení ScaleTransform3D způsobí, že vrcholy rozbalit nebo smlouvy o počátku (0,0,0). Pokud model, který chcete transformovat není čerpána z počátku, ale měřítko modelu z počátku nebude měřítko modelu "na místě.". Místo toho, když jsou vrcholy modelu vynásobeny vektorem měřítka, operace měřítka bude mít za následek překlad modelu a jeho změnu měřítka.  
  
 ![Měřítko tří krychlí se zadaným středovým bodem](./media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Příklad středu měřítka  
  
 Chcete-li změnit měřítko modelu "na místě", určete střed modelu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>nastavením <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> vlastností ScaleTransform3D , a. Tím zajistíte, že grafický systém změní velikost modelového prostoru a <xref:System.Windows.Media.Media3D.Point3D>převede jej do středu na určeném . Naopak pokud jste vytvořili model o počátku a zadejte jiný středový bod, očekávejte, že model bude přeložen mimo počátek.  
  
## <a name="rotation-transformations"></a>Transformace otočení  
 Model můžete otáčet ve 3D několika různými způsoby. Typická transformace otočení určuje osu a úhel natočení kolem této osy. Třída <xref:System.Windows.Media.Media3D.RotateTransform3D> umožňuje definovat <xref:System.Windows.Media.Media3D.Rotation3D> s jeho <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> vlastnost. Potom zadáte <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> a vlastnosti na Rotation3D, <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>v tomto případě , definovat transformaci. Následující příklady otáčejí model o 60 stupňů kolem osy Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Poznámka:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D je pravotočivá soustava, což znamená, že kladná hodnota úhlu pro otočení má za následek otáčení proti směru hodinových ručiček kolem osy.  
  
 Otočení osy předpokládají otočení o <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>počátek, pokud pro <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>vlastnosti , a <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> vlastnosti na RotateTransform3D není zadána hodnota. Stejně jako u změny měřítka je užitečné si uvědomit, že otočení transformuje celý souřadnicový prostor modelu. Pokud model nebyl vytvořen o počátku nebo byl přeložen dříve, rotace může "pivot" o počátku namísto otáčení na místě.  
  
 ![Otočení s novým středovým bodem](./media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Otočení s novým určeným středem  
  
 Chcete-li model otočit "na místě", určete skutečný střed modelu jako střed otáčení. Vzhledem k tomu, že geometrie je obvykle modelována podle počátku, můžete nejčastěji získat očekávaný výsledek sady transformací tak, že nejprve uvažujete model (škálování), pak nastavíte jeho orientaci (otočení) a nakonec ji přesunete na požadované místo ( překládání).  
  
 ![Otočení o 60 stupňů v x&#45; a y&#45;osách](./media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Příklad otočení  
  
 Otočení s osovým úhlem fungují dobře pro statické transformace a některé animace. Zvažte však otočení modelu krychle o 60 stupňů kolem osy X a pak o 45 stupňů kolem osy Z. Tuto transformaci můžete popsat jako dvě diskrétní podobné transformace nebo jako matice. Může však být obtížné plynule animovat otočení definované tímto způsobem. Přestože počáteční a koncové pozice modelu vypočítané podle obou přístupů jsou stejné, mezilehlé pozice přijaté modelem jsou výpočetně nejisté. Quaternions představují alternativní způsob výpočtu interpolace mezi začátkem a koncem rotace.  
  
 Quaternion představuje osu ve 3D prostoru a otáčení kolem této osy. Například kvinoúhelník může představovat (1,1,2) osu a otočení o 50 stupňů. Kvarminomiony 'moc při definování rotace pochází ze dvou operací, které můžete provádět na nich: složení a interpolace. Složení dvou quaternions aplikovaných na geometrii znamená "otočit geometrii kolem osy2 otočením2 a pak ji otočit kolem osy1 otočením1." Pomocí kompozice můžete kombinovat dvě otočení na geometrii získat jeden quaternion, který představuje výsledek. Vzhledem k tomu, že interpolace kvaternu může vypočítat hladkou a přiměřenou cestu z jedné osy a orientace do druhé, můžete interpolovat z původního na složený kvarternion, abyste dosáhli hladkého přechodu z jedné na druhou, což vám umožní animovat Transformace. Pro modely, které chcete animovat, <xref:System.Windows.Media.Media3D.Quaternion> můžete určit cíl <xref:System.Windows.Media.Media3D.QuaternionRotation3D> pro <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> otočení pomocí vlastnosti.  
  
## <a name="using-transformation-collections"></a>Použití kolekcí transformace  
 Při vytváření scény je běžné použít více než jednu transformaci na model. Přidejte transformace <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> do kolekce <xref:System.Windows.Media.Media3D.Transform3DGroup> třídy do skupiny transformace pohodlně použít pro různé modely ve scéně. Často je vhodné znovu použít transformaci v několika různých skupinách, podobně tak, že můžete znovu použít model použitím jiné sady transformací pro každou instanci. Všimněte si, že pořadí, ve kterém jsou přidány transformace do kolekce je významný: transformace v kolekci jsou použity od prvního k poslednímu.  
  
## <a name="animating-transformations"></a>Animace transformací  
 3D [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implementace se účastní stejného časování a animačního systému jako 2D grafika. Jinými slovy, animovat 3D scénu, animovat vlastnosti svých modelů. Je možné animovat vlastnosti primitiv přímo, ale je obvykle jednodušší animovat transformace, které mění pozici nebo vzhled modelů. Vzhledem k tomu, <xref:System.Windows.Media.Media3D.Model3DGroup> že transformace lze použít na objekty i jednotlivé modely, je možné použít jednu sadu animací na podřízené model3Dgroup a jinou sadu animací na skupinu objektů.  Základní informace o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systému časování a animace naleznete v [tématu Přehled animací](animation-overview.md) a [přehled scénářů](storyboards-overview.md).  
  
 Chcete-li animovat objekt v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]aplikaci , vytvořte časovou osu, definujte animaci (což je ve skutečnosti změna hodnoty některé vlastnosti v čase) a určete vlastnost, na kterou se má animace použít. Tato vlastnost musí být vlastnost frameworkelement. Vzhledem k tomu, že všechny objekty ve 3D scéně jsou podřízenými objekty Viewport3D, vlastnosti, na které se zaměřují všechny animace, které chcete na scénu aplikovat, jsou vlastnosti Viewport3D. Je důležité pečlivě vypracovat cestu vlastnosti pro animaci, protože syntaxe může být podrobné.  
  
 Předpokládejme, že chcete objekt otočit na místě, ale také použít kyvný pohyb, abyste vystavili více objektu k zobrazení. Můžete použít RotateTransform3D na model a animovat osu jeho otočení z jednoho vektoru do druhého. Následující příklad kódu ukazuje <xref:System.Windows.Media.Animation.Vector3DAnimation> použití a na Axis vlastnost transformace Rotation3D, za předpokladu, že RotateTransform3D být <xref:System.Windows.Media.TransformGroup>jedním z několika transformací aplikovaných na model s .  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Použijte podobnou syntaxi k cílení na jiné vlastnosti transformace k přesunutí nebo zmenšení velikosti objektu.  Můžete například použít <xref:System.Windows.Media.Animation.Point3DAnimation> vlastnost ScaleCenter v transformaci měřítka, která způsobí, že model bude hladce deformovat svůj tvar.  
  
 Přestože předchozí příklady transformovat <xref:System.Windows.Media.Media3D.GeometryModel3D>vlastnosti , je také možné transformovat vlastnosti jiných modelů ve scéně.  Například animací překladů použitých na světelné objekty můžete vytvářet pohyblivé světelné a stínové efekty, které mohou dramaticky změnit vzhled vašich modelů.  
  
 Vzhledem k tomu, že kamery jsou také modely, je možné transformovat i vlastnosti kamery.  I když můžete určitě změnit vzhled scény transformací umístění kamery nebo vzdálenosti roviny - ve skutečnosti transformuje celou projekci scény - všimněte si, že mnoho efektů, kterých tímto způsobem dosáhnete, nemusí mít pro diváka tolik "vizuálního smyslu" jako transformace aplikované na umístění nebo umístění modelů ve scéně.  
  
## <a name="see-also"></a>Viz také

- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Přehled transformace](transforms-overview.md)
- [Ukázka 2D transformací](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
