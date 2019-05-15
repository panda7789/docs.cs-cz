---
title: Přehled strukturované navigace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: a0da874c74562822d521d4a44782d9372cd62f90
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588648"
---
# <a name="structured-navigation-overview"></a>Přehled strukturované navigace
Obsah, který může být hostován [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame>, nebo <xref:System.Windows.Navigation.NavigationWindow> se skládá z stránky, které lze identifikovat podle pack [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] a kterou se odkazuje hypertextové odkazy. Struktura stránek a způsoby, ve kterém se dá Navigovat, tak jak je definoval hypertextové odkazy, se označuje jako topologie navigace. Tato topologie vyhovuje širokou škálu typů aplikací, zejména těch, které procházejí dokumenty. Pro takové aplikace uživatele můžete přejít z jedné stránky na jinou stránku bez buď stránky museli cokoliv vědět o nich.  
  
 Jiné druhy aplikací však mít stránek, které je potřeba vědět, kdy byla přešli mezi. Zvažte například aplikaci lidských zdrojů, která má jednu stránku, chcete-li vypsat všechny zaměstnance v organizaci – na stránce "Seznamu zaměstnanci". Tato stránka může také umožňují uživatelům přidat nového zaměstnance kliknutím na hypertextový odkaz. Po kliknutí na stránce přejde na stránku "Přidat Employee" shromažďování podrobnosti nového zaměstnance a vrátit na stránku "Seznamu zaměstnanci" k vytvoření nového zaměstnance a aktualizaci seznamu. Tento styl navigace je podobný voláním metody k nějakým způsobem zpracovat a vrátí hodnotu, která se nazývá strukturované programování. V důsledku toho se nazývá tento styl navigace *strukturovaná navigace*.  
  
 <xref:System.Windows.Controls.Page> Třída neimplementuje podporu pro strukturované navigace. Místo toho <xref:System.Windows.Navigation.PageFunction%601> třída odvozena z <xref:System.Windows.Controls.Page> a rozšiřuje základní konstrukcí, vyžaduje se pro strukturované navigace. Toto téma ukazuje, jak vytvořit strukturované navigace pomocí <xref:System.Windows.Navigation.PageFunction%601>.  

<a name="Structured_Navigation"></a>   
## <a name="structured-navigation"></a>Strukturované navigace  
 Při jedné stránce volá jiné stránky v strukturované navigace, se vyžadují některé nebo všechny z následujících chování:  
  
- Stránce volání přejde na stránce volané, volitelně předávání parametrů vyžadovaných názvem stránky.  
  
- Stránce volaná po dokončení uživatele na stránce volání vrátí konkrétně na stránku pro volání Volitelně:  
  
    - Vrací informace o stavu, který popisuje, jak stránce volání bylo dokončeno (například, zda uživatel stiskne tlačítko OK nebo tlačítko Storno).  
  
    - Vrací data, která byla shromážděna z uživatele (například podrobnosti nového zaměstnance).  
  
- Po návratu volání stránky na stránku volané stránce volané Odebereme z historii navigace k izolaci jeden výskyt stránku volané z jiného.  
  
 Těchto projevů je znázorněn ve na následujícím obrázku:  
  
 ![Snímek obrazovky znázorňuje tok mezi volajícím a volané stránky.](./media/structured-navigation-overview/flow-between-calling-page-called-page.png)  
  
 Tyto chování můžete implementovat pomocí <xref:System.Windows.Navigation.PageFunction%601> jako názvem stránky.  
  
<a name="Structured_Navigation_with_PageFunction"></a>   
## <a name="structured-navigation-with-pagefunction"></a>Strukturovaná navigace pomocí funkce PageFunction  
 Toto téma ukazuje, jak implementovat základní mechanismy strukturované navigace zahrnující jediného <xref:System.Windows.Navigation.PageFunction%601>. V této ukázce <xref:System.Windows.Controls.Page> volání <xref:System.Windows.Navigation.PageFunction%601> zobrazíte <xref:System.String> hodnotu od uživatele a vrátí jej.  
  
### <a name="creating-a-calling-page"></a>Vytvoření volání funkce stránky  
 Na stránce, která volá <xref:System.Windows.Navigation.PageFunction%601> může být buď <xref:System.Windows.Controls.Page> nebo <xref:System.Windows.Navigation.PageFunction%601>. V tomto příkladu je <xref:System.Windows.Controls.Page>, jak je znázorněno v následujícím kódu.  
  
 [!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]  
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]  
  
 [!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
 [!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]  
  
### <a name="creating-a-page-function-to-call"></a>Vytváření pro volání funkce stránky  
 Protože volání stránku použijte ke shromažďování a vrátit data od uživatele, názvem stránky <xref:System.Windows.Navigation.PageFunction%601> je implementovaný jako obecné třídy, jehož argument typu Určuje typ hodnoty, která vrátí názvem stránky. Následující kód ukazuje počáteční implementace souboru s názvem stránky, můžete použít <xref:System.Windows.Navigation.PageFunction%601>, který vrátí hodnotu <xref:System.String>.  
  
 [!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]  
  
 [!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
 [!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]  
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]  
  
 Deklarace <xref:System.Windows.Navigation.PageFunction%601> je podobná deklaraci <xref:System.Windows.Controls.Page> přidání argumentů typu. Jak je vidět z příkladu kódu, zadejte argumenty jsou určené v i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód, pomocí `x:TypeArguments` atribut a kódu, pomocí syntaxe standardní obecný typ argumentu.  
  
 Není nutné používat pouze třídy rozhraní .NET Framework jako argumenty typu. A <xref:System.Windows.Navigation.PageFunction%601> mohl nazývat shromažďovat data specifického pro doménu, která je abstrahovaný jako vlastního typu. Následující kód ukazuje, jak použít jako argument typu pro vlastní typ <xref:System.Windows.Navigation.PageFunction%601>.  
  
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
  
 Argumenty typu pro <xref:System.Windows.Navigation.PageFunction%601> poskytují základ pro komunikaci mezi stránku volající a volané stránky, které jsou popsány v následujících částech.  
  
 Jak uvidíte, typ, který je označen deklarace <xref:System.Windows.Navigation.PageFunction%601> hraje důležitou roli při vracení dat z <xref:System.Windows.Navigation.PageFunction%601> na stránku pro volání.  
  
### <a name="calling-a-pagefunction-and-passing-parameters"></a>Třída PageFunction volání a předávání parametrů  
 Volání na stránce, volání stránku vytvořit instanci názvem stránky a přejít k němu pomocí <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metody. To umožňuje, aby volající stránka počáteční data předat názvem stránky, například výchozí hodnoty pro shromážděné volané stránkou.  
  
 Následující kód ukazuje názvem stránky pomocí jiného než výchozího konstruktoru pro příjem parametrů z volající stránky.  
  
 [!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
 [!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]  
  
 Následující kód ukazuje volání zpracování stránky <xref:System.Windows.Documents.Hyperlink.Click> událost <xref:System.Windows.Documents.Hyperlink> instanci volané stránku a předat ji počáteční řetězcovou hodnotu.  
  
 [!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]  
  
 Můžete se nevyžadují pro předání parametrů do volané stránky. Místo toho může postupujte takto:  
  
- Na stránce volání:  
  
    1. Vytvořit instanci s názvem <xref:System.Windows.Navigation.PageFunction%601> pomocí výchozího konstruktoru.  
  
    2. Parametry v Store <xref:System.Windows.Application.Properties%2A>.  
  
    3. Přejděte do volaného <xref:System.Windows.Navigation.PageFunction%601>.  
  
- Z s názvem <xref:System.Windows.Navigation.PageFunction%601>:  
  
    - Načtení a použití parametry uložené v <xref:System.Windows.Application.Properties%2A>.  
  
 Ale jak uvidíte krátce, stále potřebovat použijete kód instanci a přejděte na stránku volaná ke shromažďování dat vrácených názvem stránky. Z tohoto důvodu <xref:System.Windows.Navigation.PageFunction%601> musí uchovávat zachování připojení; jinak vrátí hodnotu, při příštím přejdete na <xref:System.Windows.Navigation.PageFunction%601>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vytvoří instanci <xref:System.Windows.Navigation.PageFunction%601> pomocí výchozího konstruktoru.  
  
 Před názvem stránky můžete vrátit, ale je potřeba vrátit data, která je možné načíst podle volání stránky.  
  
### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Vrátí výsledek úlohy a úkolů Data z úlohy k volání funkce stránky  
 Po dokončení volané stránce uživatel označeny v tomto příkladu stisknutím tlačítka OK ani Storno, volaná stránka potřebám vrátit. Protože volání stránky volané stránka používá ke shromažďování dat od uživatele, volání stránka vyžaduje dva typy informací:  
  
1. Určuje, zda uživatel zrušil názvem stránky (stisknutím klávesy na tlačítko OK nebo na tlačítko Storno v tomto příkladu). To umožňuje, aby volající stránka k určení, jestli se má zpracovat data, která stránce volání shromážděných od uživatele.  
  
2. Data zadaná uživatelem.  
  
 K vrácení informací, <xref:System.Windows.Navigation.PageFunction%601> implementuje <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> metody. Následující kód ukazuje, jak ji volat.  
  
 [!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
 [!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]  
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]  
  
 V tomto příkladu, pokud uživatel stiskne tlačítko Storno, hodnota `null` se vrátí na původní stránku. Pokud místo toho stisknutí tlačítka OK, je vrácena hodnota řetězce zadaná uživatelem. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> je `protected virtual` metodu, která volání vrátit data na stránku pro volání. Vaše data musí být zabalené v instanci obecného <xref:System.Windows.Navigation.ReturnEventArgs%601> typ, jehož argument typu Určuje typ hodnoty, které <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> vrátí. Tímto způsobem, když deklarujete <xref:System.Windows.Navigation.PageFunction%601> s argumentem určitého typu jsou oznamující, že <xref:System.Windows.Navigation.PageFunction%601> vrátí instanci typu, který je určený argumentem typu. V tomto příkladu argument typu a v důsledku toho návratová hodnota je typu <xref:System.String>.  
  
 Když <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> je volána, volajícího stránka potřebám nějaký způsob přijímá návratovou hodnotu <xref:System.Windows.Navigation.PageFunction%601>. Z tohoto důvodu <xref:System.Windows.Navigation.PageFunction%601> implementuje <xref:System.Windows.Navigation.PageFunction%601.Return> událost pro stránky, které zpracovávají volání. Když <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> se nazývá <xref:System.Windows.Navigation.PageFunction%601.Return> se vyvolá, aby volající stránky můžete zaregistrovat pomocí <xref:System.Windows.Navigation.PageFunction%601.Return> pro příjem oznámení.  
  
 [!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
 [!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]  
  
### <a name="removing-task-pages-when-a-task-completes"></a>Odebrání stránky úloh po dokončení úkolu  
 Vrátí stránku volané a uživatel nebyl zrušit názvem stránky, volání stránky bude zpracovávat data, která byla zadaná uživatelem a vráceny také ze stránky s názvem. Získání dat tímto způsobem je obvykle aktivitu izolované; Po návratu názvem stránky, na stránce volání je třeba můžete vytvořit a přejít na novou stránku volání zaznamenat další data.  
  
 Nicméně pokud volaná stránka je odebrána z deníku, bude uživatel moci přejít zpět na předchozí instanci volání stránky. Jestli <xref:System.Windows.Navigation.PageFunction%601> se uchovávají v deníku závisí <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> vlastnost. Ve výchozím nastavení, je funkce stránky automaticky odebrány při <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> se nevolá, protože <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> je nastavena na `true`. Aby funkce stránky v historii navigace po <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> je volána, nastavte <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> k `false`.  
  
<a name="Other_Types_of_Structured_Navigation"></a>   
## <a name="other-types-of-structured-navigation"></a>Jiné druhy strukturované navigace  
 Toto téma ukazuje nejzákladnější použití <xref:System.Windows.Navigation.PageFunction%601> pro podporu volání nebo vracet strukturovaná navigace. Tyto základy vám poskytuje možnost vytvářet složitější typy strukturované navigace.  
  
 Například někdy více stránek nevyžadovala volání stránky shromažďovat dostatek dat od uživatele nebo k provádění úkolu. Použití více stránek se označuje jako "wizard".  
  
 V ostatních případech aplikace mohou mít topologie komplexních navigace, které jsou závislé na strukturované navigace efektivně pracovat. Další informace najdete v tématu [přehled topologií navigace](navigation-topologies-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Přehled topologií navigace](navigation-topologies-overview.md)
