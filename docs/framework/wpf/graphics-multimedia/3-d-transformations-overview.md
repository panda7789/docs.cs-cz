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
ms.openlocfilehash: 983ae51fb74255b3331237825755449a00c9f95c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453140"
---
# <a name="3-d-transformations-overview"></a>Přehled 3D transformací
Toto téma popisuje, jak použít transformace na 3D modely v systému [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Graphics. Transformace umožňují vývojáři změnit umístění, změnu velikosti a přeorientovat modely, aniž by museli měnit základní hodnoty, které je definují.  

## <a name="3-d-coordinate-space"></a>prostorový souřadnicový prostor  
 prostorový grafický obsah v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je zapouzdřený v elementu, <xref:System.Windows.Controls.Viewport3D>, který se může účastnit struktury dvojrozměrného prvku. Systém grafiky zpracovává objektu Viewport3D jako dvourozměrný vizuální prvek, například mnoho dalších v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Objektu Viewport3D funkce jako okno – zobrazení – do trojrozměrné scény. Přesněji platí, že se jedná o povrch, na kterém je 3D scéna založená na projektu.  I když můžete použít objektu Viewport3D s ostatními 2D nakreslenými objekty ve stejném grafu scény, nemůžete proniknout 2D a 3D objekty v rámci objektu Viewport3D. V následující diskuzi je popsaný prostor souřadnic obsažený v elementu objektu Viewport3D.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] souřadnicový systém pro 2D grafiku vyhledá počátek v levém horním rohu plochy vykreslování (obvykle na obrazovce). V dvojrozměrném systému se kladné hodnoty osy x přesměrují na pravé a kladné hodnoty osy y směrem dolů. V 3D souřadnicovém systému je však počátek umístěný uprostřed obrazovky, přičemž kladné hodnoty osy x přejdou na pravé, ale kladné hodnoty osy y se blíží směrem nahoru, ale hodnoty z osy na ose z směrem nahoru od počátku až do prohlížeč.  
  
 ![Systémy souřadnic](./media/coordsystem-1.png "CoordSystem-1")  
Porovnání systémových souřadnic  
  
 Prostor definovaný těmito osami je stacionární rámec odkazů pro 3D objekty v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Při sestavování modelů v tomto prostoru a vytváření světel a fotoaparátů k jejich zobrazení je užitečné rozlišovat tento stacionární rámec odkazů nebo "světové místo" z místního rámce odkazu, který vytvoříte pro každý model při použití transformací. Mějte na paměti, že objekty ve světě můžou vypadat úplně jinak nebo vůbec nemusejí být viditelné, v závislosti na nastaveních světla a kamery, ale poloha kamery nemění umístění objektů v prostoru světa.  
  
## <a name="transforming-models"></a>Transformace modelů  
 Při vytváření modelů mají příslušné umístění na scéně. Chcete-li přesunout tyto modely v rámci scény, pro jejich otočení nebo změnu velikosti, není praktické měnit vrcholy, které definují samotné modely. Místo toho můžete použít transformace na modely, stejně jako v 2D.  
  
 Každý objekt modelu má vlastnost <xref:System.Windows.Media.Media3D.Model3D.Transform%2A>, se kterou můžete model přesunout, změnit jeho orientaci nebo změnit jeho velikost. Když použijete transformaci, efektivně posunete všechny body modelu podle jakéhokoliv vektoru nebo hodnoty, které jsou určeny transformací. Jinými slovy jste převedli souřadnicový prostor, ve kterém je model definován ("prostor modelu"), ale nezměnili jste hodnoty, které tvoří geometrii modelu v souřadnicovém systému celé scény ("World Space").  
  
## <a name="translation-transformations"></a>Transformace překladu  
 3-D transformace dědí z abstraktní základní třídy <xref:System.Windows.Media.Media3D.Transform3D>; patří mezi ně transformační třídy spřažení <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D>a <xref:System.Windows.Media.Media3D.RotateTransform3D>. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D systém poskytuje také třídu <xref:System.Windows.Media.Media3D.MatrixTransform3D>, která umožňuje určit stejné transformace v dalších stručných maticových operacích.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D> přesouvá všechny body v Model3D ve směru vektoru posunu, který zadáte pomocí vlastností <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>a <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A>. Například vzhledem k tomu, že jeden vrchol krychle na pozici (2, 2, 2), má posunutí vektoru (0, 1.6, 1) přesunout tento vrchol (2, 2, 2) na (2, 3.6, 3). Vrchol datové krychle je stále (2, 2, 2) v modelovém prostoru, ale nyní se změnil jeho vztah na světový prostor tak, aby (2, 2, 2) v prostoru modelu byl (2, 3.6, 3) v celém prostoru.  
  
 ![Obrázek překladu](./media/transforms-translate.png "Transformes – překlady")  
Překlad s posunem  
  
 Následující příklady kódu ukazují, jak použít překlad.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Transformace měřítka  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D> mění měřítko modelu podle zadaného vektoru měřítka s odkazem na středový bod. Zadejte jednotnou škálu, která škáluje model podle stejné hodnoty v osách X, Y a Z, aby se poměrná velikost modelu změnila. Například nastavení <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>transformace, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>a vlastností <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> na 0,5 se zmenší na polovinu velikosti modelu; nastavení stejných vlastností na 2 zdvojnásobí jeho měřítko ve všech třech osách.  
  
 ![Uniform ScaleTransform3D](./media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Příklad ScaleVector  
  
 Zadáte-li transformaci s nejednotným škálováním, transformaci, jejíž hodnoty X, Y a Z nejsou stejné, můžete způsobit roztažení modelu nebo kontraktu v jedné nebo dvou dimenzích, aniž by to ovlivnilo ostatní. Například nastavení <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> na 1, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> na 2 a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> na hodnotu 1 způsobí, že transformovaný model bude dvojnásobnou výškou, ale zůstane beze změny podél osy X a Z.  
  
 Ve výchozím nastavení ScaleTransform3D způsobuje, že se vrcholy rozšiřují nebo mají na původ (0, 0, 0). Pokud model, který chcete transformovat, není nakreslený od počátku, ale škálování modelu z původního zdroje nebude škálovat model "" na místě ". Místo toho, když jsou vrcholy modelu vynásobeny vektorem škálování, operace škálování bude mít vliv na převod modelu i na jeho změnu.  
  
 ![Tři datové krychle škálované se zadaným středovým bodem](./media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Škálovat na střed – příklad  
  
 Pokud chcete škálovat model "" na místě ", zadejte střed modelu nastavením vlastností ScaleTransform3D's <xref:System.Windows.Media.ScaleTransform.CenterX%2A>, <xref:System.Windows.Media.ScaleTransform.CenterY%2A>a <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A>. Tím se zajistí, že systém grafiky škáluje prostor modelu a pak je přeloží na střed zadaného <xref:System.Windows.Media.Media3D.Point3D>. Naopak, pokud jste sestavili model o původu a určili jiný středový bod, očekává se, že se model přeloží od počátku.  
  
## <a name="rotation-transformations"></a>Transformace rotace  
 Model můžete v 3D 3D otáčet několika různými způsoby. Typická transformace rotace Určuje osu a úhel otočení kolem dané osy. Třída <xref:System.Windows.Media.Media3D.RotateTransform3D> umožňuje definovat <xref:System.Windows.Media.Media3D.Rotation3D> s vlastností <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>. Pak zadáte <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> a vlastnosti <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> v Rotation3D, v tomto případě <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>pro definování transformace. Následující příklady otočí model o 60 stupňů kolem osy Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Poznámka:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-D je pravý systém, což znamená, že hodnota kladného úhlu pro otočení má za následek otočení po směru hodinových ručiček o ose.  
  
 Rotace úhlu osy předpokládají otočení o původu, pokud není zadána hodnota pro vlastnosti <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>a <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> v RotateTransform3D. Stejně jako u škálování je užitečné si uvědomit, že rotace transformuje celý prostor souřadnic modelu. Pokud model nebyl vytvořen o původu, nebo byl již dříve přeložen, rotace může být "Pivot" (zdroj), místo aby bylo provedeno otočení.  
  
 ![Rotace s novým středovým bodem](./media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Otočení pomocí zadaného nového centra  
  
 Chcete-li otočit model "" na místě ", zadejte skutečné centrum modelu jako střed otočení. Vzhledem k tomu, že geometrie je obvykle modelována o původu, můžete většinu často získat očekávaný výsledek sady transformací, a to tak, že nejprve naměníte velikost modelu (jeho škálování), pak nastavíte jeho orientaci (otočením) a nakonec ho přesunete do požadovaného umístění ( překladu).  
  
 ![Rotace o 60 stupňů v&#45; osách x&#45;a y](./media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Příklad rotace  
  
 Rotace úhlu osy fungují dobře pro statické transformace a některé animace. Zvažte však otočení modelu datové krychle 60 stupňů kolem osy X a potom 45 stupňů kolem osy Z. Tuto transformaci můžete popsat jako dvě samostatné transformace vztahů nebo jako matici. Nicméně může být obtížné plynule animovat rotaci, která je tímto způsobem definována. I když počáteční a koncová pozice modelu vypočítaného buď přístupem jsou stejné, mezilehlé pozice prováděné modelem jsou bez určitých výpočtů. Kvaternionů představuje alternativní způsob, jak vypočítat interpolaci mezi začátkem a koncem otáčení.  
  
 Quaternion představuje osu v trojrozměrném prostoru a otočení kolem osy. Například Quaternion může představovat osu (1, 1, 2) a rotaci 50 stupňů. Kvaternionů "výkon při definování rotací pochází ze dvou operací, které můžete v nich provádět: složení a interpolace. Složení dvou kvaternionů použitých na geometrii znamená "otočení geometrie kolem axis2y rotation2 a jejich otočení kolem axis1 pomocí rotation1." Pomocí kompozice můžete kombinovat dvě otočení v geometrii a získat tak jeden Quaternion, který představuje výsledek. Vzhledem k tomu, že Quaternion interpolace může vypočítat hladkou a rozumnou cestu z jedné osy a orientace na jinou, můžete interpolovat od originálu k složenému Quaternion a dosáhnout tak hladkého přechodu z jednoho na druhý, což vám umožní animovat Transformation. U modelů, které chcete animovat, můžete určit cílovou <xref:System.Windows.Media.Media3D.Quaternion> pro otočení pomocí <xref:System.Windows.Media.Media3D.QuaternionRotation3D> pro vlastnost <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>.  
  
## <a name="using-transformation-collections"></a>Používání kolekcí transformací  
 Při sestavování scény je běžné použít více než jednu transformaci na model. Přidejte transformace do kolekce <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> <xref:System.Windows.Media.Media3D.Transform3DGroup> třídy, aby byly transformované do skupin vhodné, aby se projevily na různých modelech scény. Často je vhodné znovu použít transformaci v několika různých skupinách, a to v podstatě způsob, jakým můžete model opakovaně použít pomocí jiné sady transformací pro každou instanci. Všimněte si, že pořadí, ve kterém jsou transformace přidány do kolekce, jsou významné: transformace v kolekci jsou aplikovány od začátku až po poslední.  
  
## <a name="animating-transformations"></a>Animace transformací  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-D implementace se účastní stejného časového a animačního systému jako 2D grafika. Jinými slovy, pokud chcete animovat 3D scénu, animovat vlastnosti svých modelů. Je možné animovat vlastnosti primitivních primitiv přímo, ale obvykle je snazší animovat transformace, které mění polohu nebo vzhled modelů. Vzhledem k tomu, že transformace lze použít pro <xref:System.Windows.Media.Media3D.Model3DGroup> objektů a také pro jednotlivé modely, je možné použít jednu sadu animací na podřízené objekty Model3Dgroup a další sadu animací na skupinu objektů.  Základní informace o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] časování a animačním systému najdete v tématu Přehled [animace](animation-overview.md) a [Přehled scénářů](storyboards-overview.md).  
  
 Chcete-li animovat objekt v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], vytvořte časovou osu, definujte animaci (což je skutečně Změna v určité hodnotě vlastnosti v čase) a určete vlastnost, pro kterou chcete animaci použít. Tato vlastnost musí být vlastnost FrameworkElement. Vzhledem k tomu, že všechny objekty ve 3D scéně jsou podřízenými položkami objektu Viewport3D, jsou vlastnosti, které jsou cílem jakékoli animace, kterou chcete použít u scény, vlastnostmi vlastností objektu Viewport3D. Je důležité, abyste pečlivě vypracovali cestu vlastnosti pro animaci, protože syntaxe může být podrobná.  
  
 Předpokládejme, že chcete otočit objekt na místě, ale také pro použití pohybu, který vystaví další objekt k zobrazení. Můžete se rozhodnout použít pro model RotateTransform3D a animovat osu jeho rotace z jednoho vektoru na druhý. Následující příklad kódu ukazuje použití <xref:System.Windows.Media.Animation.Vector3DAnimation> na vlastnost Axis Rotation3D transformace, za předpokladu, že RotateTransform3D je jednou z několika transformací použitých pro model s <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Použijte podobnou syntaxi k zacílení na jiné vlastnosti transformace pro přesun nebo škálování objektu.  Můžete například použít <xref:System.Windows.Media.Animation.Point3DAnimation> k vlastnosti ScaleCenter v transformaci měřítka, aby model mohl hladce derušit jeho tvar.  
  
 Přestože předchozí příklady transformují vlastnosti <xref:System.Windows.Media.Media3D.GeometryModel3D>, je také možné transformovat vlastnosti jiných modelů ve scéně.  Animováním překladů aplikovaných na světlé objekty můžete například vytvořit efekty přechodu mezi světlými a stíny, které mohou významně měnit vzhled modelů.  
  
 Vzhledem k tomu, že kamery jsou také modely, je možné také transformovat vlastnosti kamery.  I když můžete změnit vzhled scény tím, že transformují polohu kamery nebo roviny, a přitom transformuje celou scénu, pamatujte na to, že mnohé z efektů, které tímto způsobem provedete, nemusí mít tolik "vizuální smysl". jako transformace použité pro umístění nebo umístění modelů na scéně.  
  
## <a name="see-also"></a>Viz také

- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Přehled transformace](transforms-overview.md)
- [Ukázka dvou D transformací](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
