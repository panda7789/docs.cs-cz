---
title: Přehled malování plnými barvami a přechody
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- painting with gradients [WPF]
- gradients [WPF], painting with
- brushes [WPF], painting with solid colors
- brushes [WPF], painting with gradients
- painting with solid colors [WPF]
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
ms.openlocfilehash: 5ba8127d5be24a9fdcccf0bebcc08e5699d98033
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238391"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Přehled malování plnými barvami a přechody
Toto téma popisuje způsob použití <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.LinearGradientBrush>, a <xref:System.Windows.Media.RadialGradientBrush> objekty pro malování plnými barvami, lineární přechody a radiálními přechody.  

<a name="solidcolor"></a>   
## <a name="painting-an-area-with-a-solid-color"></a>Malování oblasti plnou barvou  
 Jedním z nejběžnějších operací v libovolné platformě je vykreslení oblasti ucelený <xref:System.Windows.Media.Color>. Tento úkol provést [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje <xref:System.Windows.Media.SolidColorBrush> třídy. Následující části popisují různé způsoby, jak Malování <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="solidcolorinxaml"></a>   
### <a name="using-a-solidcolorbrush-in-xaml"></a>Použití štětce SolidColorBrush v "XAML"  
 K vykreslení oblasti plnou barvou v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte jednu z následujících možností.  
  
- Vyberte předdefinované barvy štětce podle názvu.  Například můžete nastavit tlačítka <xref:System.Windows.Controls.Control.Background%2A> "Red" nebo "Středně modrá".  Seznam dalších předdefinovaných plnobarevné štětce, najdete v části statické vlastnosti <xref:System.Windows.Media.Brushes> třídy. Následuje příklad.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]  
  
- Zvolte barvu z palety barev 32-bit zadáním množství červené, zelené a modré zkombinovat do jedné plnou barvu.  Formát pro zadávání barvu z palety 32 bitů je " *#rrggbb*", kde *rr* je dvoumístné šestnáctkové číslo určující relativní červené, *gg* Určuje dobu, zelenou a *bb* určuje množství modrá.  Kromě toho lze zadat barvu jako "#*aarrggbb*" kde *aa* Určuje *alfa* hodnotu nebo průhlednost barvy. Tento přístup umožňuje vytvářet barvy, které jsou částečně transparentní.  V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> je nastavena na hodnotu red úplně neprůhledné pomocí šestnáctkové soustavě.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]  
  
- Syntaxe značek vlastnost použít k podrobnému popisu <xref:System.Windows.Media.SolidColorBrush>. Tato syntaxe je podrobnější ale umožňuje určit další nastavení, jako je například neprůhlednost štětce. V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> vlastnosti dvou <xref:System.Windows.Controls.Button> prvky jsou nastaveny na hodnotu red úplně neprůhledné. Barva štětce první je popsána pomocí názvu předdefinované barvy. Barva štětce druhý je popsána pomocí šestnáctkové soustavě.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]  
  
<a name="solidcolorsincode"></a>   
### <a name="painting-with-a-solidcolorbrush-in-code"></a>Kreslení pomocí štětce SolidColorBrush v kódu  
 K vykreslení oblasti plnou barvou v kódu, použijte jednu z následujících možností.  
  
- Použijte jednu z předdefinovaných štětce poskytované <xref:System.Windows.Media.Brushes> třídy. V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> je nastavena na <xref:System.Windows.Media.Brushes.Red%2A>.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]  
  
- Vytvoření <xref:System.Windows.Media.SolidColorBrush> a nastavte jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> pomocí vlastnosti <xref:System.Windows.Media.Color> struktury. Můžete použít předdefinované barvy z <xref:System.Windows.Media.Colors> třídy nebo můžete vytvořit <xref:System.Windows.Media.Color> pomocí statické <xref:System.Windows.Media.Color.FromArgb%2A> metody.  
  
     Následující příklad ukazuje, jak nastavit <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush> použití předdefinované barvy.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]  
  
 Statické <xref:System.Windows.Media.Color.FromArgb%2A> vám umožní zadat hodnoty alfa, červené, zelené a modré barvy. Typický rozsah pro každou z těchto hodnot je 0-255. Například alfa hodnotu 0 označuje, že je barvu zcela transparentní, zatímco hodnota 255 znamená, že barva se stane zcela neprůhledný. Obdobně red hodnota 0 znamená, že barvu nemá žádné red, zatímco hodnota 255 znamená, že barvu má maximální množství red je to možné.  V následujícím příkladu je popsána barvy štětce zadáním hodnoty alfa, červené, zelené a modré.  
  
 [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]  
  
 Další způsoby, jak zadat barvu, najdete v článku <xref:System.Windows.Media.Color> téma referenčních informací.  
  
<a name="gradient"></a>   
## <a name="painting-an-area-with-a-gradient"></a>Vykreslování v oblasti gradientu  
 Štětec přechodu jsou vykreslovány oblast, která má více barvy, které se navzájem prolínají společně osu. Můžete využít k vytvoření dojmy světla a stínové, poskytuje trojrozměrný vzhled ovládacích prvků. Můžete také využít k simulaci skla, chrome, vody a jiné technologie smooth plochy.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje dva typy štětce přechodu: <xref:System.Windows.Media.LinearGradientBrush> a <xref:System.Windows.Media.RadialGradientBrush>.  
  
<a name="lineargradientbrush"></a>   
## <a name="linear-gradients"></a>Lineární přechody  
 A <xref:System.Windows.Media.LinearGradientBrush> jsou vykreslovány oblasti definované podél řádku, přechodem *Osa přechodu*.  Zadat barvy přechodu a jejich umístění podél osy přechodu použitím <xref:System.Windows.Media.GradientStop> objekty.  Můžete také upravit Osa přechodu, který vám umožní vytvořit vodorovné a svislé barevné přechody a obrátit směr stupnice. Osa přechodu je popsané v další části. Ve výchozím nastavení je vytvořen diagonální přechod.  
  
 Následující příklad ukazuje kód, který vytvoří čtyři barvy lineárního přechodu.  
  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Tento kód vytvoří následující přechodu:  
  
 ![Úhlopříčný lineárního přechodu](./media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")  
  
 **Poznámka:** Přechodu příklady v tomto tématu použijte výchozí souřadnicový systém pro nastavení bodů počáteční a koncové body. Systém souřadnic výchozí je relativní vzhledem k ohraničujícího rámečku: Hodnota 0 označuje procento 0 ohraničující rámeček a 1 značí 100 procent ohraničujícího rámečku. Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> k hodnotě <xref:System.Windows.Media.BrushMappingMode.Absolute>. Absolutní souřadnicový systém není vzhledem k ohraničujícího rámečku. Hodnoty jsou interpretovány přímo v místním prostoru.  
  
 <xref:System.Windows.Media.GradientStop> Je základním stavebním blokem štětce přechodu.  Určuje Přechodové zarážky <xref:System.Windows.Media.GradientStop.Color%2A> na <xref:System.Windows.Media.GradientStop.Offset%2A> společně osu přechodu.  
  
- Ukončení přechodu <xref:System.Windows.Media.GradientStop.Color%2A> vlastnost určuje barvy ukončení přechodu. Může nastavit barvu pomocí předdefinované barvy (poskytované <xref:System.Windows.Media.Colors> třídy), nebo zadáním ScRGB nebo ARGB hodnot. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], šestnáctkové soustavě můžete také použít k popisu barvu. Další informace najdete v tématu <xref:System.Windows.Media.Color> struktury.  
  
- Ukončení přechodu <xref:System.Windows.Media.GradientStop.Offset%2A> vlastnost určuje pozici barvy ukončení přechodu na ose přechodu. Posun je <xref:System.Double> , od 0 do 1. Užší hodnotu posunu ukončení přechodu je 0, čím blíž je barva na začátek přechodu. Užší hodnotu posunu přechodu je 1, čím blíž je barva na konci přechodu.  
  
 Barva jednotlivých bodů mezi Přechodové zarážky se lineárně interpolované jako kombinace barvu uvedené ve dvou funkcí ohraničování Přechodové zarážky. Následujícím obrázku jsou zvýrazněny ukončení přechodu v předchozím příkladu. Kruhy označení umístění Přechodové zarážky a přerušovaná čára ukazuje Osa přechodu.  
  
 ![Přechodové zarážky v lineárním přechodem](./media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")  
  
 První přechodové určuje barvy žlutý na posun `0.0`.  Určuje druhý ukončení přechodu na posun červenou barvu `0.25`.  Body mezi těmito dvěma zastaví postupně měnit z žlutá na červenou při přesunu zleva doprava na ose přechodu.  Určuje třetí ukončení přechodu na posun modrou barvu `0.75`.  Body mezi druhý a třetí přechodové z red blue postupně měnit. Čtvrtý přechodové Určuje barvu Limetkově zeleného na posun `1.0`. Body mezi třetí a čtvrtá přechodové z modré Limetkově zelená postupně měnit.  
  
<a name="gradientaxis"></a>   
### <a name="the-gradient-axis"></a>Osa přechodu  
 Jak už jsme zmínili Přechodové zarážky lineárního přechodu štětce umístěné podél řádku Osa přechodu. Můžete změnit orientaci a velikost řádku pomocí stopy <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> vlastnosti. Manipulací stopy <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, můžete vytvořit vodorovné a svislé přechody obrátit směr stupnice, zúžit gradientu rozšíření a další.  
  
 Ve výchozím nastavení, štětec lineárního přechodu od <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> jsou relativní k oblasti se překreslit. Levém horním rohu oblasti se malovaného a (1,1) představuje pravém dolním rohu oblasti se překreslit představuje bod (0; 0). Výchozí <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> je (0; 0) a jeho výchozí <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> (1,1), se vytváří diagonální přechod od levého horního rohu a rozšíření do pravého dolního rohu oblasti se překreslit. Následující obrázek znázorňuje přechodu osy štětec lineárního přechodu s výchozí <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>.  
  
 ![Osa přechodu pro Úhlopříčný lineární přechod](./media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")  
  
 Následující příklad ukazuje postup vytvoření vodorovnou přechodu zadáním stopy <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>. Všimněte si, že Přechodové zarážky jsou stejné jako v předchozích příkladech; jednoduše změnou <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, přechodu se změnil z diagonálních na vodorovné.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu, který je vytvořen. Osa přechodu je označené na přerušovanou čáru a Přechodové zarážky jsou označené kruzích.  
  
 ![Osa přechodu pro vodorovné lineární přechod](./media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")  
  
 Následující příklad ukazuje, jak vytvořit svislý přechod.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu, který je vytvořen. Osa přechodu je označené na přerušovanou čáru a Přechodové zarážky jsou označené kruzích.  
  
 ![Osa přechodu pro svislý přechod](./media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")  
  
<a name="radialgradients"></a>   
## <a name="radial-gradients"></a>Radiálními přechody  
 Podobně jako <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush> jsou vykreslovány v oblasti barev, které mísí společně osu. V předchozích příkladech jsme si ukázali, jak se rovné čáry osy lineárního přechodu štětce. Paprskového přechodu štětce osy je definován kruh; jeho barvy "radiate" ven z původu.  
  
 V následujícím příkladu se používá štětec paprskového přechodu k vyplnění vnitřku obdélníku.  
  
 [!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu vytvořili v předchozím příkladu. Zdůraznily stopy Přechodové zarážky. Všimněte si, že i když jsou různé výsledky, ukončení přechodu v tomto příkladu jsou stejné jako ukončení přechodu v předchozích příkladech štětec lineárního přechodu.  
  
 ![Přechodové zarážky v paprskového přechodu](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> Určuje počáteční bod osa paprskového přechodu štětce přechodu. Osa přechodu vychází ze přechodu počátek přechodu kruh. Je definován štětce přechodu kruh jeho <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, a <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> vlastnosti.  
  
 Následující obrázek znázorňuje několik radiálními přechody s různými <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>, <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, a <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> nastavení.  
  
 ![Nastavení RadialGradientBrush –](./media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii")  
RadialGradientBrushes s různými nastaveními GradientOrigin, System Center, RadiusX a RadiusY.  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Určení průhledného nebo částečně Přechodové zarážky  
 Protože Přechodové zarážky se neposkytuje na vlastnost krytí, je nutné zadat alfa kanál pomocí ARGB šestnáctkové soustavě v kódu nebo použití barev <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> metodu pro vytvoření Přechodové zarážky, které jsou průhledného nebo částečně. Následující části popisují, jak vytvořit částečně transparentní Přechodové zarážky v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a kódu.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Určení barvy krytí v "XAML"  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], se používá k určení krytí jednotlivé barvy ARGB šestnáctkové soustavě. Šestnáctkové soustavě ARGB používá následující syntaxi:  
  
 `#` **aa** *rrggbb*  
  
 *Aa* v předchozí řádek představuje dvěma číslicemi šestnáctková hodnota používá k určení krytí barvu. *Rr*, *gg*, a *bb* každý představují dvě číslice šestnáctková hodnota používá k určení množství červené, zelené a modré v barvu. Každý šestnáctková číslice může mít hodnotu od 0 – 9 nebo A – F. nejmenší hodnota je 0 a F je nejvyšší. Alfa hodnotu 00 určuje barvu, která je zcela transparentní, zatímco alfa hodnotu FF vytvoří barvu, která je úplně neprůhledná.  V následujícím příkladu šestnáctkové soustavě ARGB slouží k určení dvěma barvami. První je částečně transparentní (má hodnotu alfa x20), zatímco druhá je úplně neprůhledná.  
  
 [!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]  
  
<a name="fromscrgbsyntax"></a>   
### <a name="specifying-color-opacity-in-code"></a>Určení krytí barvy v kódu  
 Při použití kódu, statické <xref:System.Windows.Media.Color.FromArgb%2A> metoda vám umožňuje určit hodnotu alfa při vytváření barvu. Tato metoda přebírá čtyři parametry typu <xref:System.Byte>. První parametr určuje alfa kanál barvu. tři parametry zadejte červené, zelené a modré hodnoty barvy. Každá hodnota by měla být mezi 0 až 255. Alfa hodnota 0 určuje, zda barva zcela transparentní, zatímco alfa hodnotu 255 Určuje, že barva se stane zcela neprůhledný. V následujícím příkladu <xref:System.Windows.Media.Color.FromArgb%2A> metoda se používá k vytvoření dvou barev. První barva je částečně transparentní (má alfa hodnotu 32), zatímco druhá je úplně neprůhledná.  
  
 [!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]  
  
 Alternativně můžete použít <xref:System.Windows.Media.Color.FromScRgb%2A> metodu, která vám umožní použít ScRGB hodnoty pro vytvoření barvy.  
  
<a name="otherbrushes"></a>   
## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Malování pomocí obrázků, kreseb, Vizuály a vzory  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, a <xref:System.Windows.Media.VisualBrush> třídy umožňují vykreslení oblasti obrázků, kreseb nebo vizuály. Informace o Malování pomocí obrázků, kreseb a vzory najdete v tématu [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled transformace štětce](brush-transformation-overview.md)
- [Vrstvy vykreslování grafiky](../advanced/graphics-rendering-tiers.md)
