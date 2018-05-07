---
title: Přehled strukturované navigace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 9be4e753a229d97f2caf1d74b3b9b8239b99c694
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="structured-navigation-overview"></a>Přehled strukturované navigace
Obsah, který mohou být hostovány systémem [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame>, nebo <xref:System.Windows.Navigation.NavigationWindow> se skládá ze stránek, které lze identifikovat podle pack [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] a nejsnadnější v hypertextové odkazy. Struktura stránek a způsoby, ve kterém se lze procházet, podle definice hypertextové odkazy, se označuje jako topologii navigace. Takové topologii vyhovuje celou řadu typů aplikací, zejména ty, které procházení dokumentů. Pro tyto aplikace uživatele můžete přejít z jedné stránky na jinou stránku bez buď stránky museli mít žádné konkrétní informace o dalších.  
  
 Ale jiných typů aplikací mít stránek, které potřebujete vědět, kdy byla přešli mezi. Představte si třeba aplikace lidských zdrojů, která má jednu stránku do seznamu všechny zaměstnance v organizaci – stránka "Seznamu zaměstnanci". Tato stránka by také povolit uživatelům kliknutím na hypertextový odkaz můžete přidat nové zaměstnance. Po kliknutí na stránce přechodu na stránku "Přidat zaměstnancem" shromažďovat podrobnosti nové zaměstnance a obnoví v nich na stránku "Seznamu zaměstnanci" k vytvoření nového zaměstnance a aktualizaci seznamu. Tento styl navigace je podobná voláním metody k provedení některých zpracování a vrátí hodnotu, která se označuje jako structured programování. Takto se nazývá tento styl navigace *strukturovaná navigační*.  
  
 <xref:System.Windows.Controls.Page> Třída neimplementuje podporu pro strukturovaných navigaci. Místo toho <xref:System.Windows.Navigation.PageFunction%601> třída odvozená z <xref:System.Windows.Controls.Page> a rozšiřuje o základní konstrukce požadované strukturovaných navigace. Toto téma ukazuje, jak vytvořit pomocí strukturovaných navigační <xref:System.Windows.Navigation.PageFunction%601>.  
  
 
  
<a name="Structured_Navigation"></a>   
## <a name="structured-navigation"></a>Strukturované navigace  
 Při jednu stránku volá jinou stránku v strukturovaných navigaci, se vyžadují některé nebo všechny z následujících chování:  
  
-   Volání stránky přejde na stránce názvem, volitelně předání parametrů požadovaných podle názvem stránky.  
  
-   Stránce volané po dokončení uživatele pomocí volání stránky, vrátí konkrétně na stránku volání Volitelně:  
  
    -   Vrací informace o stavu, který popisuje, jak stránce volání bylo dokončeno (například, jestli uživatel stisknutí tlačítko OK nebo na tlačítko Storno).  
  
    -   Vrací data, která nebyla shromážděna od uživatele (například podrobnosti nové zaměstnance).  
  
-   Po návratu volání stránky na stránku názvem volané stránka odebrána z historie navigační izolovat jednu instanci názvem stránky z jiné.  
  
 Tyto chování jsou vidíte na následujícím obrázku.  
  
 ![Tok mezi volání stránky a názvem stránky](../../../../docs/framework/wpf/app-development/media/structurednavigationoverviewfigure1.png "StructuredNavigationOverviewFigure1")  
  
 Tyto chování můžete implementovat pomocí <xref:System.Windows.Navigation.PageFunction%601> jako názvem stránky.  
  
<a name="Structured_Navigation_with_PageFunction"></a>   
## <a name="structured-navigation-with-pagefunction"></a>Strukturované navigace pomocí PageFunction  
 Toto téma ukazuje, jak implementovat základní mechanismy strukturovaných navigace zahrnující jedné <xref:System.Windows.Navigation.PageFunction%601>. V této ukázce <xref:System.Windows.Controls.Page> volání <xref:System.Windows.Navigation.PageFunction%601> získat <xref:System.String> hodnotu od uživatele a obnoví v něm.  
  
### <a name="creating-a-calling-page"></a>Vytvoření stránky volání  
 Stránka, která volá <xref:System.Windows.Navigation.PageFunction%601> může být buď <xref:System.Windows.Controls.Page> nebo <xref:System.Windows.Navigation.PageFunction%601>. V tomto příkladu je <xref:System.Windows.Controls.Page>, jak je znázorněno v následujícím kódu.  
  
 [!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]  
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]  
  
 [!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
 [!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]  
  
### <a name="creating-a-page-function-to-call"></a>Vytvoření stránky funkce k volání  
 Protože volání stránky můžete použít stránku volané ke sběru a vrátit data od uživatele, <xref:System.Windows.Navigation.PageFunction%601> je implementovaný jako obecné třídy argument jehož typu Určuje typ hodnoty, která vrátí názvem stránky. Následující kód ukazuje implementaci počáteční souboru s názvem stránky, můžete použít <xref:System.Windows.Navigation.PageFunction%601>, která vrátí <xref:System.String>.  
  
 [!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]  
  
 [!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
 [!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]  
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]  
  
 Deklaraci <xref:System.Windows.Navigation.PageFunction%601> je podobná deklaraci <xref:System.Windows.Controls.Page> s přidáním systému argumenty typu. Jak je vidět z příkladu kódu argumenty typu jsou určené v obou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek, pomocí `x:TypeArguments` atribut a kódu, pomocí syntaxe argument standardní obecného typu.  
  
 Nemusíte používat jenom [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] třídy jako argumenty typu. A <xref:System.Windows.Navigation.PageFunction%601> ke shromažďování dat specifické pro doménu, která je abstrahované jako vlastní typ může být volána. Následující kód ukazuje, jak chcete použít jako argument typ pro vlastní typ <xref:System.Windows.Navigation.PageFunction%601>.  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]  
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]  
  
 [!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]  
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]  
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]  
  
 Argumenty typu pro <xref:System.Windows.Navigation.PageFunction%601> tvoří základ pro komunikaci mezi volání stránky a názvem stránky, které jsou popsané v následujících částech.  
  
 Jak zjistíte, typ, který je identifikován s deklaraci <xref:System.Windows.Navigation.PageFunction%601> hraje důležitou roli při vracení dat z <xref:System.Windows.Navigation.PageFunction%601> na stránku volání.  
  
### <a name="calling-a-pagefunction-and-passing-parameters"></a>Volání PageFunction a předávání parametrů  
 K volání na stránce, musíte stránce volání doložit názvem stránky a přejděte do pomocí <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metoda. To umožňuje stránce volání mají být předány volané stránky, jako je například výchozí hodnoty pro shromážděné volané stránka počáteční data.  
  
 Následující kód ukazuje volané stránka s jiné než výchozí konstruktor tak, aby přijímal parametry z volání stránky.  
  
 [!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
 [!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]  
  
 Následující kód ukazuje volání zpracování stránky <xref:System.Windows.Documents.Hyperlink.Click> události <xref:System.Windows.Documents.Hyperlink> doložit názvem stránky a jejich předávání počáteční řetězcovou hodnotu.  
  
 [!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]  
  
 Nejste potřeba předat parametry názvem stránky. Místo toho můžete postupovat takto:  
  
-   Na stránce volání:  
  
    1.  Vytváření instancí s názvem <xref:System.Windows.Navigation.PageFunction%601> pomocí výchozí konstruktor.  
  
    2.  Uložit parametry v <xref:System.Windows.Application.Properties%2A>.  
  
    3.  Přejděte do volaného <xref:System.Windows.Navigation.PageFunction%601>.  
  
-   Z volaného <xref:System.Windows.Navigation.PageFunction%601>:  
  
    -   Načtení a použití parametrů uložených v <xref:System.Windows.Application.Properties%2A>.  
  
 Ale jako se krátce zobrazí, budete stále nutné používat kód k vytváření instancí a přejít na stránku volané ke shromažďování dat vrácených názvem stránky. Z tohoto důvodu <xref:System.Windows.Navigation.PageFunction%601> musí být zachovány zachování připojení; jinak hodnota, při příštím přejdete k <xref:System.Windows.Navigation.PageFunction%601>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vytvoří <xref:System.Windows.Navigation.PageFunction%601> pomocí výchozí konstruktor.  
  
 Před názvem stránky může vrátit, ale je nutné vrátit data, která může načíst stránku volání.  
  
### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Vrací výsledek úlohy a úkolů Data z úlohy na stránku volání  
 Po dokončení uživatele pomocí stránky volané označeny v tomto příkladu stisknutím tlačítka OK nebo zrušit, je nutné vrátit názvem stránky. Vzhledem k tomu, že stránce volání volané stránka používá ke shromažďování dat od uživatele, volání stránka vyžaduje dva typy informací:  
  
1.  Tom, jestli uživatel stornoval názvem stránky (stisknutím tlačítka OK nebo na tlačítko Storno v tomto příkladu). To umožňuje stránku volání a určení, zda ke zpracování dat, která stránce volání získané od uživatele.  
  
2.  Data zadaná uživatelem.  
  
 K vrácení informací, <xref:System.Windows.Navigation.PageFunction%601> implementuje <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> metoda. Následující kód ukazuje, jak ji volat.  
  
 [!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
 [!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]  
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]  
  
 V tomto příkladu, pokud uživatel stiskne tlačítko Zrušit, hodnota `null` je vrácen do stránce volání. Pokud místo toho stisknutí tlačítka OK, je vrácena hodnota řetězce zadaná uživatelem. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> je `protected``virtual` metoda, kterou je možné volat vrátit na stránku volání vaše data. Vaše data musí být zabalené v instanci Obecné <xref:System.Windows.Navigation.ReturnEventArgs%601> hodnota typu, jehož typ argumentu určuje typ, který <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> vrátí. Tímto způsobem po deklarování <xref:System.Windows.Navigation.PageFunction%601> s argumentem konkrétního typu jsou oznamující, že <xref:System.Windows.Navigation.PageFunction%601> vrátí instanci typu, který je zadán argument typu. V tomto příkladu argument typu a v důsledku toho návratová hodnota je typu <xref:System.String>.  
  
 Když <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> nazývá volání potřebám stránky nějakým způsobem pro příjem vrácenou hodnotu <xref:System.Windows.Navigation.PageFunction%601>. Z tohoto důvodu <xref:System.Windows.Navigation.PageFunction%601> implementuje <xref:System.Windows.Navigation.PageFunction%601.Return> událost pro volání stránky pro zpracování. Když <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> je volána, <xref:System.Windows.Navigation.PageFunction%601.Return> se vyvolá, takže volání stránky můžete zaregistrovat s <xref:System.Windows.Navigation.PageFunction%601.Return> pro příjem oznámení.  
  
 [!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
 [!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]  
  
### <a name="removing-task-pages-when-a-task-completes"></a>Odebrání stránky úloh po dokončení úlohy  
 Pokud vrátí názvem stránky a uživatel nebyl zrušit názvem stránky, stránce volání bude zpracovávat data, která nebyla zadané uživatelem a také vrácena z názvem stránky. Získávání dat tímto způsobem je obvykle izolované aktivitu; Po návratu stránce volané stránce volání je potřeba vytvořit a přejděte na novou stránku volání k zaznamenání dat o další.  
  
 Ale pokud názvem stránky je odebrán z deník, uživatel bude moci přejít zpět na předchozí instanci volání stránky. Jestli <xref:System.Windows.Navigation.PageFunction%601> se uchovávají v Deník je dáno <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> vlastnost. Ve výchozím nastavení, na stránce funkce je automaticky odebrány při <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> je volána, protože <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> je nastaven na `true`. Aby funkce stránky v historii navigace po <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> je volána, nastavte <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> k `false`.  
  
<a name="Other_Types_of_Structured_Navigation"></a>   
## <a name="other-types-of-structured-navigation"></a>Jiné typy strukturovaných navigace  
 Toto téma ukazuje nejzákladnější použití <xref:System.Windows.Navigation.PageFunction%601> pro podporu volání nebo vrátit strukturovaná navigace. Tento foundation vám poskytuje možnost vytvářet složitější typy strukturovaných navigace.  
  
 Například někdy více stránek nebo jsou vyžadované volání stránka získat dostatek dat od uživatele při provádění úlohy. Použití více stránek se označuje jako "Průvodce".  
  
 V ostatních případech aplikace mohou mít komplexní navigační topologie, které jsou závislé na strukturovaných navigační efektivní práci. Další informace najdete v tématu [přehled topologie navigační](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [Přehled topologií navigace](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)
