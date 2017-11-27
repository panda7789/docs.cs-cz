---
title: "Přehled malování plnými barvami a přechody"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solid colors [WPF], painting with
- painting with gradients [WPF]
- gradients [WPF], painting with
- brushes [WPF], painting with solid colors
- brushes [WPF], painting with gradients
- painting with solid colors [WPF]
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f26ab394ea94b27257b6d0b662f3a78f3e68ca99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>Přehled malování plnými barvami a přechody
Toto téma popisuje postup použití <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.LinearGradientBrush>, a <xref:System.Windows.Media.RadialGradientBrush> objekty k malování plné barvy, lineární přechody a paprskového přechody.  
  

  
<a name="solidcolor"></a>   
## <a name="painting-an-area-with-a-solid-color"></a>Vykreslování oblast plnou barvou  
 Některé z nejběžnějších operací v libovolné platformě je k vyplnění oblast s ucelený <xref:System.Windows.Media.Color>. K provedení této úlohy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje <xref:System.Windows.Media.SolidColorBrush> třídy. Následující části popisují různé způsoby, jak Malování <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="solidcolorinxaml"></a>   
### <a name="using-a-solidcolorbrush-in-xaml"></a>Pomocí objektu SolidColorBrush v "XAML"  
 K vyplnění oblast plnou barvou v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte jednu z následujících možností.  
  
-   Vyberte předdefinované plnobarevné štětce podle názvu.  Například můžete nastavit na tlačítko <xref:System.Windows.Controls.Control.Background%2A> "Red" nebo "Středně modrá".  Seznam dalších předdefinované plnobarevné štětce, najdete v části statické vlastnosti <xref:System.Windows.Media.Brushes> třídy. Následuje příklad.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]  
  
-   Vyberte barvu z palety 32-bit zadáním množství červená, zelená a modrá se zkombinovat do jednoho plnou barvou.  Formát pro zadání barvu z palety 32-bit je "*#rrggbb*", kde *rr* dva hexadecimální číslice určující relativní množství červené, *gg* Určuje množství zelené, a *bb* určuje množství blue.  Kromě toho lze zadat barvu jako "#*aarrggbb*" kde *aa* Určuje *alpha* hodnotu, nebo průhlednost barvy. Tento přístup umožňuje vytvořit barev, které jsou částečně transparentní.  V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> nastavený na plně neprůhledné červený pomocí šestnáctkové soustavě.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]  
  
-   Použití syntaxe značek vlastnost k popisu <xref:System.Windows.Media.SolidColorBrush>. Tato syntaxe je podrobnější ale můžete určit další nastavení, jako štětce krytí. V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> vlastnosti dva <xref:System.Windows.Controls.Button> elementy jsou nastaveny na plně neprůhledné červený. Barva první štětce je popsán pomocí názvu předdefinované barvy. Barva druhý štětce je popsán pomocí šestnáctkové soustavě.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]  
  
<a name="solidcolorsincode"></a>   
### <a name="painting-with-a-solidcolorbrush-in-code"></a>Malování s SolidColorBrush v kódu  
 Malovat oblast plnou barvou v kódu, použijte jednu z následujících možností.  
  
-   Použijte jeden z předdefinovaných štětce poskytované <xref:System.Windows.Media.Brushes> třídy. V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> je nastaven na <xref:System.Windows.Media.Brushes.Red%2A>.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]  
  
-   Vytvoření <xref:System.Windows.Media.SolidColorBrush> a nastavit jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> pomocí vlastnosti <xref:System.Windows.Media.Color> struktury. Můžete použít předdefinované barvu ze <xref:System.Windows.Media.Colors> třídy nebo můžete vytvořit <xref:System.Windows.Media.Color> pomocí statické <xref:System.Windows.Media.Color.FromArgb%2A> metoda.  
  
     Následující příklad ukazuje, jak nastavit <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush> pomocí předdefinovaných barev.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]  
  
 Statické <xref:System.Windows.Media.Color.FromArgb%2A> umožňuje určit hodnoty alfa, červené, zelené a modré barvy. Typické rozsah pro každou z těchto hodnot je 0 až 255. Například při použití hodnoty alfa 0 označuje, že je barvu, která je zcela transparentní, při hodnotu 255 značí, že je zcela neprůhledný barvu. Podobně red hodnota 0 značí, že barvu, která má žádné red v něm, zatímco hodnota 255 znamená, že barvu, která má maximální množství red možné.  V následujícím příkladu je popsána štětce barvu zadáním hodnoty alfa, červené, zelené a modré.  
  
 [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]  
  
 Další způsoby, jak zadat barvu, najdete v článku <xref:System.Windows.Media.Color> referenční téma.  
  
<a name="gradient"></a>   
## <a name="painting-an-area-with-a-gradient"></a>Vykreslování oblast s přechodem  
 Štětce přechodu vybarví oblast s více barev, které slučují do sebe navzájem podél osy. Můžete je používat vytvořit možnost vytvořit dojem světlým a shadow, udělíte vaše ovládací prvky trojrozměrné chování. Můžete je také použít k simulaci skla, chrome, horních a jiné technologie smooth plochy.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nabízí dva typy štětce přechodu: <xref:System.Windows.Media.LinearGradientBrush> a <xref:System.Windows.Media.RadialGradientBrush>.  
  
<a name="lineargradientbrush"></a>   
## <a name="linear-gradients"></a>Lineární přechody  
 A <xref:System.Windows.Media.LinearGradientBrush> vybarví oblast s přechodem definována na řádek, *přechodu osy*.  Zadejte barvy má barevný přechod a jejich umístění podél osy přechodu pomocí <xref:System.Windows.Media.GradientStop> objekty.  Může také upravit ose přechodu, který umožňuje vytvořit vodorovně a svisle přechody a obrátit směr přechodu. Osa přechodu je popsaná v další části. Ve výchozím nastavení se vytvoří diagonálních přechodu.  
  
 Následující příklad ukazuje kód, který vytvoří lineárního přechodu s čtyři barvy.  
  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Tento kód vytvoří následující přechodu:  
  
 ![Diagonálních lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")  
  
 **Poznámka:** přechodu příklady v tomto tématu použijte výchozí souřadnicový systém pro nastavení body počáteční a koncové body. Systém souřadnic výchozí je relativní vzhledem ke ohraničující pole: 0 označuje 0 procent rámečku a 1 označuje 100 procent ohraničujícího rámečku. Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> vlastnost na hodnotu <xref:System.Windows.Media.BrushMappingMode.Absolute>. Absolutní souřadnicový systém není relativně k ohraničující pole. Hodnoty se interpretují přímo v místním prostoru.  
  
 <xref:System.Windows.Media.GradientStop> Je základním stavebním blokem štětce přechodu.  Určuje Přechodové zarážky <xref:System.Windows.Media.GradientStop.Color%2A> v <xref:System.Windows.Media.GradientStop.Offset%2A> přechodu osy.  
  
-   Přechodové zarážky <xref:System.Windows.Media.GradientStop.Color%2A> vlastnost určuje barvu Přechodové zarážky. Barva může nastavit pomocí předdefinovaných barvu (poskytované <xref:System.Windows.Media.Colors> třída) nebo zadáním hodnot ScRGB nebo ARGB. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete také používat šestnáctkové soustavě k popisu barvy. Další informace najdete v tématu <xref:System.Windows.Media.Color> struktura.  
  
-   Přechodové zarážky <xref:System.Windows.Media.GradientStop.Offset%2A> vlastnost určuje pozici Přechodové zarážky barvy na ose přechodu. Posun je <xref:System.Double> , rozsah od 0 do 1. Čím bližší Přechodové zarážky posunutí hodnota je 0, že Čím bližší je barvu spuštění barevného přechodu. Čím bližší má barevný přechod posunutí hodnota je 1, že Čím bližší je barva barevného přechodu na konec.  
  
 Barva každý bod mezi zarážkami je lineárně interpolované jako kombinace barvu uvedené ve dvou ohraničujícího Přechodové zarážky. Na následujícím obrázku jsou vysvětlené Přechodové zarážky v předchozím příkladu. Kroužky označte pozici přechodu zastaví a na přerušovanou čáru ukazuje osy přechodu.  
  
 ![Přechodové zarážky v lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")  
  
 Určuje barvu žlutý v posunem první Přechodové zarážky `0.0`.  Druhý Přechodové zarážky určuje v posunem červenou barvu `0.25`.  Body mezi těmito dvěma zastaví postupně změnit z žlutý na červený jako přesunout zleva doprava přechodu osy.  Třetí Přechodové zarážky Určuje barvu blue v posunem `0.75`.  Body mezi ukončení přechodu druhý a třetí postupně z červené na modrou změnit. Čtvrtý Přechodové zarážky určuje v posunem zelenou barvu vápna `1.0`. Body mezi třetí a čtvrtý Přechodové zarážky postupně změnit z modré na vápna zeleně.  
  
<a name="gradientaxis"></a>   
### <a name="the-gradient-axis"></a>Osa přechodu  
 Jak jsme uvedli jsou lineárního přechodu štětce přechodu zastaví umístěné společně řádek přechodu osy. Můžete změnit orientaci a velikost řádku pomocí štětce <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> vlastnosti. Manipulací stopy <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, můžete vytvořit vodorovné a přechody vertikální, změnit směr přechodu, zúžit přechodu šíření a další.  
  
 Ve výchozím nastavení, lineární štětce přechodu na <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> jsou relativní vzhledem k oblasti se vykresluje. Bod (0,0) představuje oblasti se malovaného a (1,1) představuje pravém dolním rohu oblasti se vykresluje levém horním rohu. Výchozí <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> je (0,0) a jeho výchozí <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> je (1,1), která vytvoří diagonálních přechodu od levého horního rohu a rozšíření na pravém dolním rohu oblasti se vykresluje. Následující obrázek ukazuje na přechodu ose lineární štětce přechodu na výchozích <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>.  
  
 ![Osa přechodu pro diagonálních lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")  
  
 Následující příklad ukazuje postup vytvoření vodorovných přechodu zadáním stopy <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>. Všimněte si, že Přechodové zarážky jsou stejné jako v předchozích příkladech; jednoduše změnou <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, má barevný přechod byl změněn z diagonálních na vodorovné.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu, který je vytvořen. Osa přechodu je označené jako přerušovaná čára a Přechodové zarážky jsou označené kroužky.  
  
 ![Osa přechodu pro vodorovné lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")  
  
 Další příklad ukazuje, jak vytvořit svislý přechod.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu, který je vytvořen. Osa přechodu je označené jako přerušovaná čára a Přechodové zarážky jsou označené kroužky.  
  
 ![Osa přechodu pro svislý přechod](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")  
  
<a name="radialgradients"></a>   
## <a name="radial-gradients"></a>Kruhové přechody  
 Podobně jako <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush> vybarví oblast s barev, které mísí podél osy. V předchozích příkladech vám ukázal, jak lineárního přechodu štětce osy je přímka. Paprskového přechodu štětce osy je definována kruh; jeho barvy "radiate" i z původu.  
  
 V následujícím příkladu se používá paprskového štětce přechodu k vyplnění vnitřku obdélníku.  
  
 [!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu vytvořili v předchozím příkladu. Zdůraznily štětce přechodu zastaví. Všimněte si, že i když výsledky se liší, Přechodové zarážky v tomto příkladu jsou shodné s Přechodové zarážky v předchozích příkladech lineární štětce přechodu.  
  
 ![Přechodové zarážky v kruhového přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> Určuje počáteční bod paprskového přechodu štětce přechodu osy. Osa přechodu vycházející ze přechodu počátek k přechodu kruhu. Je definované štětce přechodu kruh jeho <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, a <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> vlastnosti.  
  
 Následující obrázek znázorňuje několik paprskového přechody jiné <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>, <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, a <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> nastavení.  
  
 ![RadialGradientBrush – nastavení](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii")  
RadialGradientBrushes s jiným nastavením GradientOrigin, Center, RadiusX a RadiusY.  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>Určení průhledných nebo částečně transparentní Přechodové zarážky  
 Protože Přechodové zarážky neposkytují ve vlastnosti krytí, je nutné zadat alfa kanálu pomocí barev [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] šestnáctkové soustavě v kódu nebo použití <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> metodu pro vytvoření přechodu zastaví, které jsou transparentní nebo částečně transparentní. Následující části popisují postup vytvoření částečně transparentní Přechodové zarážky v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a kód.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Určení krytí barev v "XAML"  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijete [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] šestnáctkové soustavě k určení krytí jednotlivých barev. [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)]šestnáctkové soustavě používá následující syntaxe:  
  
 `#`**aa** *rrggbb*  
  
 *Aa* v předchozí řádek představuje letopočty šestnáctkové hodnoty slouží k zadání krytí barvy. *Rr*, *gg*, a *bb* každý představují dvoumístné šestnáctkové hodnoty používaný k zadání množství červená, zelená a modrá v barvu. Každý šestnáctková číslice může mít hodnotu od 0 – 9 nebo A-F. 0 je nejmenší hodnota a F je největší. Při použití hodnoty alfa 00 určuje barvu, která je zcela transparentní, zatímco při použití hodnoty alfa FF vytvoří barvu, která je plně neprůhledný.  V následujícím příkladu, hexadecimální [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] zápis slouží k určení dvě barvy. První je částečně transparentní (má při použití hodnoty alfa x20), zatímco druhý je zcela neprůhledný.  
  
 [!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]  
  
<a name="fromscrgbsyntax"></a>   
### <a name="specifying-color-opacity-in-code"></a>Určení krytí barev v kódu  
 Při použití kódu statických <xref:System.Windows.Media.Color.FromArgb%2A> metoda umožňuje určit hodnotu alfa při vytváření barvy. Metoda přebírá čtyři parametry typu <xref:System.Byte>. První parametr určuje alfa kanálu barvy; ostatní tři parametry zadejte hodnoty červené, zelené a modré barvy. Každá hodnota by měla být mezi 0 až 255. Při použití hodnoty alfa 0 určuje, že je barvu zcela transparentní, při hodnotu alfa 255 Určuje, že je zcela neprůhledný barvu. V následujícím příkladu <xref:System.Windows.Media.Color.FromArgb%2A> metoda se používá k vytvoření dvě barvy. První barvu je částečně transparentní (obsahuje alfa hodnotu 32), zatímco druhý je zcela neprůhledné.  
  
 [!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]  
  
 Alternativně můžete použít <xref:System.Windows.Media.Color.FromScRgb%2A> metoda, která umožňuje použít k vytvoření barvu ScRGB hodnoty.  
  
<a name="otherbrushes"></a>   
## <a name="painting-with-images-drawings-visuals-and-patterns"></a>Malování s obrázky, kresby, Vizuály a vzory  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, a <xref:System.Windows.Media.VisualBrush> třídy umožňují malovat oblast s obrázky, kresby nebo vizuální prvky. Informace o Malování s obrázky, kresby a vzory najdete v tématu [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Brush>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 [Malování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Přehled transformace štětce](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [Grafika vykreslování vrstev](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)
