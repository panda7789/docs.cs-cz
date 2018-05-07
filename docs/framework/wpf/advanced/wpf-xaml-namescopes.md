---
title: Obory názvů WPF XAML
ms.date: 03/30/2017
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
ms.openlocfilehash: c13dba48d21235c57be64d90b6547902e0428a6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-xaml-namescopes"></a>Obory názvů WPF XAML
XAML namescopes jsou koncept identifikující objekty, které jsou definovány v jazyce XAML. Názvy v jazyce XAML namescope slouží k vytvoření vztahů mezi názvy definované XAML objektů a jejich ekvivalenty u instance ve stromu k objektu. Obvykle XAML namescopes v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spravovaného kódu jsou vytvořeny při načítání jednotlivých stránek XAML kořeny pro aplikace XAML. XAML namescopes jako objekt programovací jsou definovány <xref:System.Windows.Markup.INameScope> rozhraní a také implementují třídu praktické <xref:System.Windows.NameScope>.  
  
  
  
<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Namescopes v aplikacích načíst XAML  
 Koncepty programování v širší programování nebo kontextu vědecké účely počítače, často patří Princip jedinečný identifikátor nebo název, který umožňuje přístup k objektu. Pro systémy, které používají identifikátory nebo názvy, namescope definuje hranice, do které bude vyhledávat procesu nebo techniku, pokud se požaduje objekt s tímto názvem nebo hranice, ve kterém se vynucuje jedinečnost identifikace názvy. Tyto obecné zásady platí pro XAML namescopes. V WPF XAML namescopes vytvoří v kořenovém elementu stránky XAML při načtení stránky. Každý název v rámci dané stránky XAML spouštění v kořenovém adresáři stránky je přidaný do příslušné namescope XAML.  
  
 V jazyce XAML WPF, prvky, které jsou společné prvky kořenové (například <xref:System.Windows.Controls.Page>, a <xref:System.Windows.Window>) vždy řízení XAML namescope. Pokud element jako <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> není kořenovým elementem stránky v značek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] přidá procesoru <xref:System.Windows.Controls.Page> kořenový implicitně tak, aby <xref:System.Windows.Controls.Page> může poskytnout namescope XAML pracovních.  
  
> [!NOTE]
>  Akce sestavení WPF vytvořte namescope XAML pro produkční prostředí XAML to i v případě žádné `Name` nebo `x:Name` atributy jsou definovány na všechny elementy ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 Pokud se pokusíte použít stejný název dvakrát v jakékoli namescope XAML, je vyvolána výjimka. Pro jazyk XAML WPF, který má kódu a je součástí kompilované aplikace k výjimce v čase vytvoření buildu akcemi WPF sestavení, při vytváření vygenerované třídy pro stránku během kompilace počáteční značka. Výjimky související s problémy namescope XAML pro jazyk XAML, který není značek zkompilují všechny akce sestavení, může být vyvolána při načtení XAML. Návrháři XAML může také předvídat problémy namescope XAML v době návrhu.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Přidání objektů do objektu Runtime stromů  
 V okamžiku, který je analyzovat XAML představuje okamžik v čase, který je vytvořen a definované namescope WPF XAML. Pokud přidáte objekt na strom objektu na místo v době po analýze XAML, který vytváří stromové struktuře, `Name` nebo `x:Name` hodnota u nového objektu informace v jazyce XAML namescope automaticky neaktualizuje. Umožňuje přidat název pro objekt do namescope WPF XAML po načtení XAML, musí volat odpovídající implementace <xref:System.Windows.Markup.INameScope.RegisterName%2A> na objekt, který definuje XAML namescope, který je obvykle kořenu stránky XAML. Pokud název není registrované, přidaný objekt nelze na něj odkazovat podle názvu prostřednictvím metody, jako <xref:System.Windows.FrameworkElement.FindName%2A>, a nemůžete použít tento název pro cílení na animace.  
  
 Nejběžnější scénáře pro vývojáře aplikací je, že použijete <xref:System.Windows.FrameworkElement.RegisterName%2A> registraci názvů v XAML namescope na aktuální kořenový adresář stránky. <xref:System.Windows.FrameworkElement.RegisterName%2A> je součástí scénářem důležité pro scénářů této cílové objekty pro animace. Další informace najdete v tématu [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Když zavoláte <xref:System.Windows.FrameworkElement.RegisterName%2A> na objektu, než objekt, který definuje XAML namescope, název je pořád zaregistrovaný namescope XAML, která volání objektu se nachází v rámci, jako by se měla volat <xref:System.Windows.FrameworkElement.RegisterName%2A> na namescope XAML definice objektu.  
  
### <a name="xaml-namescopes-in-code"></a>Namescopes XAML v kódu  
 Můžete vytvořit a pak použít XAML namescopes v kódu. Rozhraní API a koncepty účastnící se vytváření namescope XAML stejné i pro použití čistém kódu jsou protože procesoru XAML pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá tato rozhraní API a koncepty při procesu XAML sám sebe. Koncepty a rozhraní API existují především pro účely schopnost najít objekty podle názvu v rámci objektu stromové struktury, která je obvykle definováno částečně nebo zcela v jazyce XAML.  
  
 Pro aplikace, které jsou vytvořené prostřednictvím kódu programu a nikoli z načíst XAML, musí implementovat objekt, který definuje XAML namescope <xref:System.Windows.Markup.INameScope>, nebo <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy, aby bylo možné podporovat vytvoření XAML namescope na jeho instance.  
  
 Navíc pro libovolný element, který není načtena a zpracovaných procesorem XAML, namescope XAML pro objekt není vytvořen nebo inicializovat ve výchozím nastavení. Musíte explicitně vytvořit nové namescope XAML pro libovolný objekt, který chcete zaregistrovat názvy do následně. Pokud chcete vytvořit XAML namescope, zavolejte statickou <xref:System.Windows.NameScope.SetNameScope%2A> metoda. Zadejte objektu, která se jej jako vlastní `dependencyObject` parametr a novou <xref:System.Windows.NameScope.%23ctor%2A> volání konstruktoru, jako `value` parametr.  
  
 Pokud se zadaný objekt jako `dependencyObject` pro <xref:System.Windows.NameScope.SetNameScope%2A> není <xref:System.Windows.Markup.INameScope> implementace <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, volání <xref:System.Windows.FrameworkElement.RegisterName%2A> na všechny podřízené prvky budou mít žádný vliv. Pokud jste se nepodařilo vytvořit nový namescope XAML explicitně, pak zavolá do <xref:System.Windows.FrameworkElement.RegisterName%2A> vyvolá výjimku.  
  
 Příklad použití XAML namescope rozhraní API v kódu, naleznete v části [definování oboru název](../../../../docs/framework/wpf/graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Namescopes XAML v šablonách a styly  
 Styly a šablon v nástroji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňují opakovaně používat a znovu zásadu použijte obsah přehledné způsobem. Ale styly a šablony může také obsahovat elementy s názvy XAML definované na úrovni šablony. Že stejné šablony se dají používat více než jednou. na stránce. Z tohoto důvodu definovat vlastní namescopes XAML, nezávisle na libovolnou umístění ve stromu k objektu, kdy se používá styl nebo šablony stylů a šablony.  
  
 Podívejte se na následující příklad:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Zde je stejný šablonu použít dvě různé tlačítka. Pokud šablony neměl diskrétní XAML namescopes `TheBorder` název použité v šabloně by způsobilo kolize názvů v XAML namescope. Každý vytvoření instance šablony má svou vlastní namescope XAML, takže v tomto příkladu by jednotlivých instancí šablony XAML namescope obsahovat přesně jeden název.  
  
 Styly také definovat vlastní namescope XAML většinou tak, aby součástí scénářů může mít konkrétní názvy přiřazené. Názvy těchto povolte řízení konkrétní chování, které se zaměří na elementy daným jménem, i v případě, že šablona byla znovu definována jako součást přizpůsobení ovládacího prvku.  
  
 Z důvodu samostatné XAML je náročnější než hledání bez použití šablon s názvem elementu na stránce namescopes, vyhledávání elementů s názvem v šabloně. Nejprve je nutné určit šabloně použité získáním <xref:System.Windows.Controls.Control.Template%2A> hodnotu vlastnosti ovládacího prvku, kde bude použita šablona. Potom zavolejte šablony verze <xref:System.Windows.FrameworkTemplate.FindName%2A>, předávání ovládacího prvku, kde byla tuto šablonu použít jako druhý parametr.  
  
 Pokud jste ovládacího prvku Autor a jsou generování názvů, kde konkrétní s názvem elementu v použité šablony je cílem pro chování, které je definované samotném ovládacím prvku, můžete použít <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metoda z vašeho kódu implementaci ovládacího prvku. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> Metoda chráněný, takže jenom autora ovládacího prvku k němu má přístup.  
  
 Pokud pracujete v rámci šablony a potřeba získat XAML namescope, kde se použije šablona, získat hodnotu <xref:System.Windows.FrameworkElement.TemplatedParent%2A>a pak zavolají <xref:System.Windows.FrameworkElement.FindName%2A> existuje. Příkladem práci v rámci šablony by, pokud píšete implementace obslužné rutiny událostí kde, bude vyvolána událost z elementu v použité šablony.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML Namescopes a rozhraní API související s názvem  
 <xref:System.Windows.FrameworkElement> má <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> a <xref:System.Windows.FrameworkElement.UnregisterName%2A> metody. Pokud objekt, který volání těchto metod na vlastní XAML namescope, metody volání do metody relevantní namescope XAML. Jinak, zkontroluje nadřazeného elementu se pokud vlastní XAML namescope a tento proces pokračuje rekurzivně, dokud nebude nalezen XAML namescope (z důvodu chování procesoru XAML, existuje představuje záruku namescope XAML v kořenovém adresáři). <xref:System.Windows.FrameworkContentElement> je obdobou chování, s výjimkou který žádné <xref:System.Windows.FrameworkContentElement> se někdy vlastní XAML namescope. Metody existovat na <xref:System.Windows.FrameworkContentElement> tak, aby nakonec do může být přeposílán volání <xref:System.Windows.FrameworkElement> nadřazeného elementu.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> slouží k mapování nové namescope XAML na existující objekt. Můžete volat <xref:System.Windows.NameScope.SetNameScope%2A> více než jednou za účelem obnovení nebo zrušte XAML namescope, ale není běžné využití. Navíc <xref:System.Windows.NameScope.GetNameScope%2A> se obvykle nepoužívá z kódu.  
  
### <a name="xaml-namescope-implementations"></a>Implementace Namescope XAML  
 Následující třídy implementují <xref:System.Windows.Markup.INameScope> přímo:  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> nepoužívá XAML názvy nebo namescopes; používá klíče místo, protože je implementace slovníku. Jediným důvodu <xref:System.Windows.ResourceDictionary> implementuje <xref:System.Windows.Markup.INameScope> je tak může být spojeno výjimky uživatelského kódu, které pomáhají vysvětlení rozdílu mezi true XAML namescope a jak <xref:System.Windows.ResourceDictionary> zpracovává klíčů a také, aby zajistil, že se nepoužije XAML namescopes <xref:System.Windows.ResourceDictionary> nadřazené elementy.  
  
 <xref:System.Windows.FrameworkTemplate> a <xref:System.Windows.Style> implementovat <xref:System.Windows.Markup.INameScope> prostřednictvím definice explicitního rozhraní. Explicitní implementace povolit tyto XAML namescopes chovat obvykle, když jsou přístupné prostřednictvím <xref:System.Windows.Markup.INameScope> rozhraní, které je, jak se předávají XAML namescopes podle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vnitřních procesů. Definice explicitního rozhraní nejsou součástí konvenční plochy rozhraní API, ale <xref:System.Windows.FrameworkTemplate> a <xref:System.Windows.Style>, protože potřebujete málokdy volání <xref:System.Windows.Markup.INameScope> metody na <xref:System.Windows.FrameworkTemplate> a <xref:System.Windows.Style> přímo a místo toho využije jiných rozhraní API například <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Následující třídy definují vlastní namescope XAML pomocí <xref:System.Windows.NameScope?displayProperty=nameWithType> pomocná třída a připojení k jeho implementace namescope XAML prostřednictvím <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> přidružená vlastnost:  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Viz také  
 [Obory názvů XAML a mapování oboru názvů pro WPF XAML](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)  
 [x:Name – direktiva](../../../../docs/framework/xaml-services/x-name-directive.md)
