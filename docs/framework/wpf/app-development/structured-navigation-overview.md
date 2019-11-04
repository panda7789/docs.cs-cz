---
title: Přehled strukturované navigace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 09c3c57f3ac1009416a5c67b37c035fe30cd5b5e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425330"
---
# <a name="structured-navigation-overview"></a>Přehled strukturované navigace

Obsah, který lze hostovat pomocí aplikace prohlížeče XAML (XBAP), <xref:System.Windows.Controls.Frame>, nebo <xref:System.Windows.Navigation.NavigationWindow> se skládá ze stránek, které mohou být identifikovány pomocí identifikátorů URI (Uniform Resource Identifier) a přechází na ně pomocí hypertextových odkazů. Struktura stránek a způsoby, kterými se dají přejít, jak jsou definované hypertextovými odkazy, se označují jako navigační topologie. Taková topologie vyhovuje nejrůznějším typům aplikací, zejména k procházení dokumentů. Pro takové aplikace může uživatel přecházet z jedné stránky na jinou stránku, aniž by museli mít žádné informace o druhé straně.

Jiné typy aplikací však mají stránky, které potřebují znát, pokud byly přecházení mezi nimi. Představte si například aplikaci lidských zdrojů, která má jednu stránku k vypsání všech zaměstnanců v organizaci – na stránce "vypsat zaměstnance". Tato stránka může také uživatelům dovolit přidat nového zaměstnance kliknutím na hypertextový odkaz. Po kliknutí na stránku přejdete na stránku přidat zaměstnance, kde zjistíte podrobnosti o novém zaměstnanci a vrátíte je na stránku "seznam zaměstnanců". vytvoří se nový zaměstnanec a seznam se aktualizuje. Tento styl navigace je podobný volání metody pro provedení nějakého zpracování a vrácení hodnoty, která se označuje jako strukturované programování. V takovém případě se tento styl navigace označuje jako *strukturovaná navigace*.

Třída <xref:System.Windows.Controls.Page> neimplementuje podporu strukturované navigace. Místo toho je třída <xref:System.Windows.Navigation.PageFunction%601> odvozena z <xref:System.Windows.Controls.Page> a rozšiřuje ji o základní konstrukce vyžadované pro strukturované navigace. V tomto tématu se dozvíte, jak vytvořit strukturovanou navigaci pomocí <xref:System.Windows.Navigation.PageFunction%601>.

<a name="Structured_Navigation"></a>

## <a name="structured-navigation"></a>Strukturovaná navigace

Když jedna stránka zavolá jinou stránku ve strukturované navigaci, vyžadují se některé nebo všechna následující chování:

- Volající stránka přejde na volanou stránku a volitelně předává parametry vyžadované volanou stránkou.

- Volaná stránka: když uživatel dokončí používání volající stránky, vrátí se konkrétně na volající stránku, volitelně:

  - Vracení informací o stavu, které popisují, jak byla volající stránka dokončena (například zda uživatel stiskne tlačítko OK nebo tlačítko Storno).

  - Vrácení dat, která byla shromážděna uživatelem (například Podrobnosti o novém zaměstnanci).

- Když se volající stránka vrátí na volanou stránku, volaná stránka je odebrána z historie navigace a izoluje jednu instanci pojmenované stránky od druhé.

Toto chování je znázorněno na následujícím obrázku:

![Snímek obrazovky znázorňující tok mezi volající stránkou a volanou stránkou.](./media/structured-navigation-overview/flow-between-calling-page-called-page.png)

Toto chování můžete implementovat pomocí <xref:System.Windows.Navigation.PageFunction%601> jako na volané stránce.

<a name="Structured_Navigation_with_PageFunction"></a>

## <a name="structured-navigation-with-pagefunction"></a>Strukturovaná navigace pomocí PageFunction

Toto téma ukazuje, jak implementovat základní mechanismy strukturované navigace zahrnující jeden <xref:System.Windows.Navigation.PageFunction%601>. V této ukázce <xref:System.Windows.Controls.Page> volá <xref:System.Windows.Navigation.PageFunction%601> a získá <xref:System.String> hodnotu od uživatele a vrátí ji.

### <a name="creating-a-calling-page"></a>Vytvoření volající stránky

Stránka, která volá <xref:System.Windows.Navigation.PageFunction%601> může být buď <xref:System.Windows.Controls.Page> nebo <xref:System.Windows.Navigation.PageFunction%601>. V tomto příkladu je to <xref:System.Windows.Controls.Page>, jak je znázorněno v následujícím kódu.

[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]

[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]

### <a name="creating-a-page-function-to-call"></a>Vytvoření funkce stránky pro volání

Vzhledem k tomu, že volající stránka může použít volanou stránku ke shromáždění a vrácení dat od uživatele, <xref:System.Windows.Navigation.PageFunction%601> je implementována jako obecná třída, jejíž argument typu Určuje typ hodnoty, která volaná stránka vrátí. Následující kód ukazuje počáteční implementaci volané stránky pomocí <xref:System.Windows.Navigation.PageFunction%601>, která vrací <xref:System.String>.

[!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]

[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]

Deklarace <xref:System.Windows.Navigation.PageFunction%601> je podobná deklaraci <xref:System.Windows.Controls.Page> s přidáním argumentů typu. Jak vidíte z příkladu kódu, argumenty typu jsou zadány v kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], pomocí atributu `x:TypeArguments` a kódu na pozadí pomocí standardní syntaxe argumentu obecného typu.

Nemusíte používat pouze .NET Framework třídy jako argumenty typu. Pro shromažďování dat specifických pro doménu, která jsou abstraktní jako vlastní typ, by mohla být volána <xref:System.Windows.Navigation.PageFunction%601>. Následující kód ukazuje, jak použít vlastní typ jako argument typu pro <xref:System.Windows.Navigation.PageFunction%601>.

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]

[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]

Argumenty typu <xref:System.Windows.Navigation.PageFunction%601> poskytují základ pro komunikaci mezi volající stránkou a volanou stránkou, která je popsána v následujících částech.

Jak vidíte, typ, který je identifikován deklarací <xref:System.Windows.Navigation.PageFunction%601>, hraje důležitou roli při vracení dat z <xref:System.Windows.Navigation.PageFunction%601> na volající stránku.

### <a name="calling-a-pagefunction-and-passing-parameters"></a>Volání PageFunction a předávání parametrů

Chcete-li zavolat stránku, musí volající strana vytvořit instanci pojmenované stránky a přejít na ni pomocí metody <xref:System.Windows.Navigation.NavigationService.Navigate%2A>. Tato možnost umožňuje volající stránce předat počáteční data na volanou stránku, například výchozí hodnoty pro data shromažďovaná pomocí volané stránky.

Následující kód ukazuje volanou stránku s konstruktorem bez parametrů pro příjem parametrů z volající stránky.

[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]

Následující kód ukazuje volající stránku, která zpracovává událost <xref:System.Windows.Documents.Hyperlink.Click> <xref:System.Windows.Documents.Hyperlink> k vytvoření instance pojmenované stránky a předání počáteční hodnoty řetězce.

[!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]

Na volanou stránku není nutné předávat parametry. Místo toho můžete provést následující akce:

- Z volající stránky:

  1. Vytvořte instanci volaného <xref:System.Windows.Navigation.PageFunction%601> pomocí konstruktoru bez parametrů.

  2. Uložte parametry do <xref:System.Windows.Application.Properties%2A>.

  3. Přejděte na volaný <xref:System.Windows.Navigation.PageFunction%601>.

- Z volané <xref:System.Windows.Navigation.PageFunction%601>:

  - Načte a použije parametry uložené v <xref:System.Windows.Application.Properties%2A>.

Ale jak vidíte za chvíli, budete potřebovat použít kód pro vytvoření instance a přejít na volanou stránku, kde můžete shromažďovat data vrácená volanou stránkou. Z tohoto důvodu musí být <xref:System.Windows.Navigation.PageFunction%601> udržována v neaktivním stavu. v opačném případě při příštím přechodu na <xref:System.Windows.Navigation.PageFunction%601>[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vytvoří instance <xref:System.Windows.Navigation.PageFunction%601> pomocí konstruktoru bez parametrů.

Před vrácením volané stránky však musí vracet data, která lze načíst volající stránkou.

### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Vrácení výsledku úkolu a dat úkolu z úkolu na volající stránku

Jakmile uživatel dokončí používání pojmenované stránky, které jsou v tomto příkladu označeny tlačítky OK nebo Storno, je nutné, aby volaná stránka vrátila hodnotu. Vzhledem k tomu, že volající stránka použila volaný stránku ke shromáždění dat od uživatele, volající stránka vyžaduje dva typy informací:

1. Určuje, zda uživatel zrušil volanou stránku (stisknutím tlačítka OK nebo tlačítkem zrušit v tomto příkladu). To umožňuje volající stránce určit, jestli se mají zpracovávat data, která volající stránka shromáždila od uživatele.

2. Data, která byla poskytnuta uživatelem.

Pro vrácení informací <xref:System.Windows.Navigation.PageFunction%601> implementuje metodu <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>. Následující kód ukazuje, jak ho zavolat.

[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]

Pokud uživatel v tomto příkladu stiskne tlačítko Storno, vrátí se na volající stránku hodnota `null`. Pokud se místo toho stiskne tlačítko OK, vrátí se hodnota řetězce zadaná uživatelem. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> je `protected virtual` metoda, kterou zavoláte, abyste vrátili data na volající stránku. Vaše data musí být zabalena do instance obecného typu <xref:System.Windows.Navigation.ReturnEventArgs%601>, jehož argument typu Určuje typ hodnoty, která <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> vrací. Tímto způsobem, pokud deklarujete <xref:System.Windows.Navigation.PageFunction%601> pomocí konkrétního argumentu typu, zjistíte, že <xref:System.Windows.Navigation.PageFunction%601> vrátí instanci typu, který je určen argumentem typu. V tomto příkladu je argument typu a v důsledku toho návratová hodnota typu <xref:System.String>.

Když je volána <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>, volající stránka potřebuje určitý způsob, jak přijmout návratovou hodnotu <xref:System.Windows.Navigation.PageFunction%601>. Z tohoto důvodu <xref:System.Windows.Navigation.PageFunction%601> implementuje událost <xref:System.Windows.Navigation.PageFunction%601.Return> pro volání stránek, které mají být zpracovány. Při volání <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> je vyvolána <xref:System.Windows.Navigation.PageFunction%601.Return>, aby se volající stránka mohla zaregistrovat v <xref:System.Windows.Navigation.PageFunction%601.Return> pro příjem oznámení.

[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]

### <a name="removing-task-pages-when-a-task-completes"></a>Odebrání stránek úloh po dokončení úkolu

Když se volaná stránka vrátí a uživatel nezrušil volanou stránku, volající stránka zpracuje data poskytnutá uživatelem a také vrátila z volané stránky. Získání dat tímto způsobem je obvykle izolovaná aktivita; Po návratu volané stránky musí volající stránka vytvořit novou volající stránku a přejít na ni a zachytit další data.

Pokud se ale z deníku neodebere volaná stránka, uživatel bude moct přejít zpátky na předchozí instanci volající stránky. Zda je v deníku zachována <xref:System.Windows.Navigation.PageFunction%601>, je určena vlastností <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>. Ve výchozím nastavení je funkce stránky automaticky odebrána při volání <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>, protože <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> je nastavena na `true`. Chcete-li zachovat funkci stránky v historii navigace po volání <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>, nastavte <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> na `false`.

<a name="Other_Types_of_Structured_Navigation"></a>

## <a name="other-types-of-structured-navigation"></a>Jiné typy strukturované navigace

Toto téma ukazuje základní použití <xref:System.Windows.Navigation.PageFunction%601> pro podporu strukturované navigace typu volání nebo vrácení. Tato základ vám umožní vytvořit komplexnější typy strukturované navigace.

Například někdy je vyžadováno více stránek volající stránky, aby bylo možné shromáždit dostatek dat od uživatele nebo provést úlohu. Použití více stránek je označováno jako "Průvodce".

V ostatních případech můžou aplikace mít složité navigační topologie, které jsou závislé na strukturované navigaci, aby fungovaly efektivně. Další informace najdete v tématu [Přehled topologií navigace](navigation-topologies-overview.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Přehled topologií navigace](navigation-topologies-overview.md)
