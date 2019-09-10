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
ms.openlocfilehash: fb6b7da4be46f361b263c573339b1a6b73ef24bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855887"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Přehled malování plnými barvami a přechody

Toto téma popisuje, jak používat <xref:System.Windows.Media.SolidColorBrush>objekty <xref:System.Windows.Media.LinearGradientBrush>, a <xref:System.Windows.Media.RadialGradientBrush> k malování plnými barvami, lineárních přechodů a paprskových přechodů.

<a name="solidcolor"></a>

## <a name="painting-an-area-with-a-solid-color"></a>Vykreslení oblasti plnou barvou

Jednou z nejběžnějších operací na jakékoli platformě je vymalování oblasti s plnou <xref:System.Windows.Media.Color>kapacitou. K provedení této úlohy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.SolidColorBrush> poskytuje třídu. Následující části popisují různé způsoby malování pomocí <xref:System.Windows.Media.SolidColorBrush>.

<a name="solidcolorinxaml"></a>

### <a name="using-a-solidcolorbrush-in-xaml"></a>Použití SolidColorBrush v jazyce XAML

Chcete-li vykreslit oblast s plnou barvou v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte jednu z následujících možností.

- Vyberte předdefinovaný vzorek plné barvy podle názvu.  Můžete například nastavit tlačítko <xref:System.Windows.Controls.Control.Background%2A> "Red" nebo "MediumBlue".  Seznam dalších předdefinovaných barevných štětců barev naleznete v tématu statické vlastnosti <xref:System.Windows.Media.Brushes> třídy. Následuje příklad.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]

- Vyberte barvu z palety barev 32, a to tak, že zadáte hodnoty červené, zelené a modré, které se sloučí do jedné plné barvy.  Formát pro určení barvy z 32 palet je " *#rrggbb*", kde *RR* je dvě číslice čísla, které určují relativní hodnotu červené, *GG* Určuje hodnotu zelenou a *BB* určuje množství modré.  Kromě toho může být barva zadána jako "#*aarrggbb*", kde *AA* Určuje hodnotu *alfa* , neboli průhlednost barvy. Tento přístup vám umožní vytvořit barvy, které jsou částečně transparentní.  V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> je nastavena na plně neprůhledná červená pomocí šestnáctkového zápisu.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]

- K popisu <xref:System.Windows.Media.SolidColorBrush>použijte syntaxi značek vlastností. Tato syntaxe je podrobněji podrobná, ale umožňuje určit další nastavení, například průhlednost štětce. V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> jsou vlastnosti dvou <xref:System.Windows.Controls.Button> prvků nastaveny na plně neprůhledné červené. Barva prvního štětce je popsána pomocí předdefinovaného názvu barvy. Barva druhého štětce je popsána v šestnáctkovém zápisu.

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]

<a name="solidcolorsincode"></a>

### <a name="painting-with-a-solidcolorbrush-in-code"></a>Malování s SolidColorBrush v kódu

Chcete-li vykreslit oblast s plnou barvou v kódu, použijte jednu z následujících možností.

- Použijte jeden z předdefinovaných štětců poskytovaných <xref:System.Windows.Media.Brushes> třídou. V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> je nastavena na <xref:System.Windows.Media.Brushes.Red%2A>.

  [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]

- Vytvořte a nastavte jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost pomocí <xref:System.Windows.Media.Color> struktury. <xref:System.Windows.Media.SolidColorBrush> Můžete použít předdefinovanou barvu z <xref:System.Windows.Media.Colors> třídy nebo můžete <xref:System.Windows.Media.Color> vytvořit pomocí statické <xref:System.Windows.Media.Color.FromArgb%2A> metody.

  Následující příklad ukazuje, jak nastavit <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush> pomocí předdefinované barvy.

  [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]

Statická <xref:System.Windows.Media.Color.FromArgb%2A> umožňuje zadat hodnoty barev alfa, Red, zelená a modrá. Typický rozsah pro každou z těchto hodnot je 0-255. Například hodnota alfa 0 znamená, že barva je zcela průhledná, zatímco hodnota 255 označuje, že barva je zcela neprůhledná. Podobně červená hodnota 0 značí, že barva v ní nemá červenou barvu, zatímco hodnota 255 indikuje, že barva má maximální možnou délku červené hodnoty.  V následujícím příkladu je popsána barva štětce zadáním hodnot Alpha, Red, zelená a Blue.

[!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]

Další způsoby určení barvy naleznete <xref:System.Windows.Media.Color> v referenčním tématu.

<a name="gradient"></a>

## <a name="painting-an-area-with-a-gradient"></a>Vykreslení oblasti barevným přechodem

Štětec přechodu maluje oblast s více barvami, které se vzájemně promísí podél osy. Můžete je použít k vytvoření křížových pokusů o světlo a stín, což umožní vašim ovládacím prvkům trojrozměrné chování. Můžete je také použít k simulaci skla, Chrome, vody a dalších hladkých ploch.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nabízí dva typy štětců přechodů <xref:System.Windows.Media.LinearGradientBrush> : <xref:System.Windows.Media.RadialGradientBrush>a.

<a name="lineargradientbrush"></a>

## <a name="linear-gradients"></a>Lineární přechody

Vykreslí oblast, která má přechod definovaný podél čáry, na *ose přechodu.* <xref:System.Windows.Media.LinearGradientBrush>  Určete barvy přechodu a jejich umístění podél osy přechodu pomocí <xref:System.Windows.Media.GradientStop> objektů.  Můžete také změnit osu přechodu, která umožňuje vytvořit vodorovné a svislé přechody a obrátit směr přechodu. Osa přechodu je popsána v následující části. Ve výchozím nastavení je vytvořen diagonální přechod.

Následující příklad ukazuje kód, který vytvoří lineární přechod se čtyřmi barvami.

[!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]

Tento kód vytvoří následující přechod:

![Diagonální lineární přechod](./media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")

> [!NOTE]
> Příklady přechodu v tomto tématu používají výchozí systém souřadnic pro nastavení počátečních bodů a koncových bodů. Výchozí souřadnicový systém je relativní vzhledem k ohraničujícímu poli: 0 značí 0 procent ohraničovacího rámečku a 1 označuje 100% ohraničovacího rámečku. Můžete změnit tento systém souřadnic nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> vlastnosti na hodnotu. <xref:System.Windows.Media.BrushMappingMode.Absolute> Absolutní souřadnicový systém není relativní vzhledem k ohraničujícímu poli. Hodnoty jsou interpretovány přímo v místním prostoru.

<xref:System.Windows.Media.GradientStop> Je základní stavební blok štětce přechodu.  Přechodová zastávka Určuje <xref:System.Windows.Media.GradientStop.Color%2A> a <xref:System.Windows.Media.GradientStop.Offset%2A> podél osy přechodu.

- <xref:System.Windows.Media.GradientStop.Color%2A> Vlastnost zastavení přechodu Určuje barvu zarážky přechodu. Barvu můžete nastavit pomocí předdefinované barvy (poskytované <xref:System.Windows.Media.Colors> třídou) nebo zadáním hodnot ScRGB nebo ARGB. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nástroji můžete k popisu barvy použít také hexadecimální zápis. Další informace najdete v tématu <xref:System.Windows.Media.Color> struktura.

- <xref:System.Windows.Media.GradientStop.Offset%2A> Vlastnost zastavení přechodu určuje umístění barvy zarážky přechodu na ose přechodu. Posun je <xref:System.Double> v rozsahu od 0 do 1. Hodnota posunu posunutí zarážky je 0, blíže je barva začátku přechodu. Hodnota posunu posunutí je rovna 1, bližší barva je až na konec barevného přechodu.

Barva každého bodu mezi zarážkami přechodu se lineárně interpoluje jako kombinace barvy určené dvěma zarážkami ohraničujícího přechodu. Následující ilustrace zvýrazní přechodové zarážky v předchozím příkladu. Kroužky označují pozici přechodu na pozici a přerušovaná čára zobrazuje osu přechodu.

![Přechodové zarážky lineárního přechodu](./media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")

První přechodová zastávka určuje žlutou barvu na posunu `0.0`.  Druhý přechodová zastávka určuje červenou barvu na posunu `0.25`.  Body mezi těmito dvěma zarážkami se postupně mění ze žluté na červenou, když přesouváte zleva doprava podél osy přechodů.  Třetí přechodová zastávka Určuje barvu modrou na posunu `0.75`.  Body mezi druhým a třetím přechodem se postupně přestanou měnit z červené na modrou. Čtvrtá přechodová zastávka Určuje barvu, která se na posunu nasadí `1.0`zeleně. Body mezi třetím a čtvrtým přechodem se postupně přestanou měnit z modré na vápno zelenou.

<a name="gradientaxis"></a>

### <a name="the-gradient-axis"></a>Osa přechodu

Jak už jsme uvedli, zarážky barevného štětce lineárního přechodu jsou umístěné podél čáry a osy přechodu. Můžete změnit orientaci a velikost čáry pomocí štětce <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> vlastností. Pomocí manipulace se štětcem <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>můžete vytvořit vodorovné a svislé přechody, obrátit směr přechodu, zúžit rozprostření a další.

Ve výchozím nastavení je štětec <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> lineárního přechodu a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> relativní vzhledem k oblasti, která se vykresluje. Bod (0, 0) představuje levý horní roh oblasti, která se vykresluje, a (1, 1) představuje pravý dolní roh oblasti, která se vykresluje. Výchozí hodnota <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> je (0, 0) a její výchozí <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> hodnota je (1, 1), která vytvoří diagonální přechod začínající v levém horním rohu a rozšíří do pravého dolního rohu oblasti, která se vykresluje. Následující ilustrace znázorňuje osu přechodu lineárního přechodu mezi barevným štětcem s <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> výchozími a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>.

![Osa přechodu pro diagonální lineární přechod](./media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")

Následující příklad ukazuje, jak vytvořit vodorovný přechod zadáním štětce <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a. <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> Všimněte si, že přechodové zarážky jsou stejné jako v předchozích příkladech. pouhou změnou <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>přechodem byl barevný přechod z diagonálního na vodorovný.

[!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]

Následující ilustrace znázorňuje přechod, který je vytvořen. Osa přechodu je označena čárkovanou čárou a přechodové zarážky jsou označeny kroužky.

![Osa přechodu pro horizontální lineární přechod](./media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")

Další příklad ukazuje, jak vytvořit svislý přechod.

[!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]

Následující ilustrace znázorňuje přechod, který je vytvořen. Osa přechodu je označena čárkovanou čárou a přechodové zarážky jsou označeny kroužky.

![Osa přechodu pro svislý přechod](./media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")

<a name="radialgradients"></a>

## <a name="radial-gradients"></a>Paprskové přechody

Podobně jako <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.RadialGradientBrush> , vykreslí oblast s barvami, které se míchají společně podél osy. Předchozí příklady ukázaly, jak je osa štětce s lineárním přechodem rovnou čárou. Osa pro štětec paprskového přechodu je definována kruhem; barvy procházejí směrem ven od počátku.

V následujícím příkladu se k vykreslování vnitřku obdélníku používá štětec paprskového přechodu.

[!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]

Následující ilustrace znázorňuje přechod vytvořený v předchozím příkladu. Bylo zvýrazněno barevné zastavení štětce. Všimněte si, že i když se výsledky liší, přechod v tomto příkladu je stejný jako v předchozích příkladech štětce přechodu na předchozí lineární přechod.

![Přechodové zarážky v paprskovém přechodu](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")

<xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> Určuje počáteční bod osy přechodu na paprskový přechod štětce. Osa přechodu vycházejí z přechodu na počátek přechodu na kroužek. Barevný kroužek štětce je definován pomocí <xref:System.Windows.Media.RadialGradientBrush.Center%2A>vlastností, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>a <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> .

Následující ilustrace znázorňuje několik paprskových přechodů s různými <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>nastaveními <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> a.

![Nastavení RadialGradientBrush](./media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii") RadialGradientBrushes s různými nastaveními GradientOrigin, Center, RadiusX a RADIUS.

<a name="specifyinggradientcolors"></a>

## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Určení průhledných nebo částečně transparentních přechodových ukončení

Vzhledem k tomu, že ukončení přechodu neposkytuje vlastnost neprůhlednosti, je nutné zadat alfa kanál barev pomocí ARGB hexadecimálního zápisu v kódu <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> nebo použít metodu k vytvoření zarážek, které jsou transparentní nebo částečně transparentní. Následující části vysvětlují, jak vytvořit částečně transparentní přechodové [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zarážky v a kódu.

<a name="argbsyntax"></a>

### <a name="specifying-color-opacity-in-xaml"></a>Určení neprůhlednosti barev v jazyce XAML

V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nástroji použijete ARGB hexadecimální zápis k určení neprůhlednosti jednotlivých barev. ARGB hexadecimální zápis používá následující syntaxi:

`#` **aa** *rrggbb*

*AA* na předchozím řádku představuje hexadecimální hodnotu se dvěma číslicemi, která se používá k určení neprůhlednosti barvy. Každý *záznam RR*, *GG*a *BB* představuje dvě číslice šestnáctkové hodnoty, které se používají k určení množství červené, zelené a modré barvy. Každé hexadecimální číslo může mít hodnotu od 0-9 nebo A-F. 0 je nejmenší hodnota a F je největší. Hodnota alfa 00 určuje barvu, která je zcela průhledná, zatímco alfa hodnota FF vytvoří barvu, která je zcela neprůhledná.  V následujícím příkladu je použit hexadecimální zápis ARGB pro zadání dvou barev. První je částečně transparentní (má hodnotu alfa x20), zatímco druhá je zcela neprůhledná.

[!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]

<a name="fromscrgbsyntax"></a>

### <a name="specifying-color-opacity-in-code"></a>Určení neprůhlednosti barev v kódu

Při použití kódu statická <xref:System.Windows.Media.Color.FromArgb%2A> metoda umožňuje zadat hodnotu alfa při vytváření barvy. Metoda přijímá čtyři parametry typu <xref:System.Byte>. První parametr určuje kanál alfa barvy; Další tři parametry určují červenou, zelenou a modrou hodnotu barvy. Každá hodnota by měla být mezi 0 a 255 (včetně). Hodnota alfa 0 určuje, že barva je zcela průhledná, zatímco hodnota alfa 255 určuje, že barva je zcela neprůhledná. V následujícím příkladu <xref:System.Windows.Media.Color.FromArgb%2A> je metoda použita k vytváření dvou barev. První barva je částečně průhledná (má hodnotu alfa 32), zatímco druhá je plně neprůhledná.

[!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]

Alternativně můžete použít <xref:System.Windows.Media.Color.FromScRgb%2A> metodu, která umožňuje použít hodnoty ScRGB k vytvoření barvy.

<a name="otherbrushes"></a>

## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Malování pomocí obrázků, kreseb, vizuálů a vzorů

<xref:System.Windows.Media.ImageBrush>třídy <xref:System.Windows.Media.DrawingBrush>, a <xref:System.Windows.Media.VisualBrush> umožňují malovat oblast obrázky, kresby nebo vizuály. Informace o malování pomocí obrázků, kreseb a vzorů najdete v tématu [malování pomocí obrázků, kreseb a vizuálů](painting-with-images-drawings-and-visuals.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled transformace štětce](brush-transformation-overview.md)
- [Vrstvy vykreslování grafiky](../advanced/graphics-rendering-tiers.md)
