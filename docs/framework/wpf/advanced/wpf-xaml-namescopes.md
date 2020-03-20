---
title: Názvy XAML
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
ms.openlocfilehash: f9d4439c6b102d0d430b5201e3649985daee0b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186277"
---
# <a name="wpf-xaml-namescopes"></a>Obory názvů WPF XAML
XAML namescopes jsou koncept, který identifikuje objekty, které jsou definovány v XAML. Názvy v oboru názvů XAML lze použít k navázání vztahů mezi názvy objektů definovanými xAML a jejich ekvivalenty instancí ve stromu objektů. Názvy XAML ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spravovaném kódu se obvykle vytvářejí při načítání jednotlivých kořenů stránky XAML pro aplikaci XAML. XAML namescopes jako programovací objekt <xref:System.Windows.Markup.INameScope> jsou definovány rozhraním <xref:System.Windows.NameScope>a jsou také implementovány praktickou třídou .  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>
## <a name="namescopes-in-loaded-xaml-applications"></a>Názvy názvů v načtených aplikacích XAML  
 V širším kontextu programování nebo počítačové vědy koncepty často zahrnují princip jedinečného identifikátoru nebo názvu, který lze použít pro přístup k objektu. Pro systémy, které používají identifikátory nebo názvy, název oboru definuje hranice, ve kterém proces nebo technika bude hledat, pokud je požadován objekt tohoto názvu, nebo hranice, v němž je vynucena jedinečnost identifikace názvů. Tyto obecné zásady platí pro názvy XAML. V WPF jsou názvobory XAML vytvořeny na kořenovém prvku stránky XAML při načtení stránky. Každý název zadaný na stránce XAML začínající v kořenovém adresáři stránky je přidán do relevantního oboru názvů XAML.  
  
 V WPF XAML prvky, které jsou <xref:System.Windows.Controls.Page>společné <xref:System.Windows.Window>kořenové prvky (například , a ) vždy řídit název protokolu XAML. Pokud prvek, <xref:System.Windows.FrameworkElement> jako <xref:System.Windows.FrameworkContentElement> je nebo je kořenový prvek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky ve <xref:System.Windows.Controls.Page> značkách, procesor <xref:System.Windows.Controls.Page> přidá kořen implicitně tak, aby může poskytnout pracovní XAML namescope.  
  
> [!NOTE]
> WPF sestavení akce vytvořit název protokolu XAML pro výrobu `Name` `x:Name` XAML i v případě, že žádné nebo atributy jsou definovány na všechny prvky ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značkách.  
  
 Pokud se pokusíte použít stejný název dvakrát v libovolném oboru názvů XAML, je vyvolána výjimka. Pro WPF XAML, který má kód na pozadí a je součástí kompilované aplikace, je výjimka vyvolána v době sestavení akcemi sestavení WPF při vytváření generované třídy pro stránku během počáteční kompilace značek. Pro XAML, který není zkompilován značky žádnou akci sestavení, výjimky související s problémy název XAML může být vyvolána při načtení XAML. Návrháři XAML mohou také předvídat problémy s názvovým rozsahem XAML v době návrhu.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Přidání objektů do stromů objektů runtime  
 Okamžik, kdy je analyzován XAML představuje okamžik v čase, kdy wpf XAML namescope je vytvořen a definován. Pokud přidáte objekt do stromu objektů v okamžiku po XAML, který vytvořil tento `Name` `x:Name` strom byl analyzován, nebo hodnota na nový objekt automaticky aktualizovat informace v oboru názvů XAML. Chcete-li přidat název objektu do jmenovce WPF XAML po načtení <xref:System.Windows.Markup.INameScope.RegisterName%2A> XAML, musíte zavolat příslušnou implementaci objektu, který definuje název protokolu XAML, což je obvykle kořen stránky XAML. Pokud název není registrován, nelze na přidaný objekt odkazovat <xref:System.Windows.FrameworkElement.FindName%2A>podle názvu prostřednictvím metod, jako je například , a tento název nelze použít pro cílení animace.  
  
 Nejběžnější scénář pro vývojáře aplikací je, že budete používat <xref:System.Windows.FrameworkElement.RegisterName%2A> k registraci názvů do oboru názvů XAML v aktuálním kořenovém adresáři stránky. <xref:System.Windows.FrameworkElement.RegisterName%2A>je součástí důležitéscénáře pro scénáře, které cílí na objekty pro animace. Další informace naleznete v [tématu Přehled scénářů](../graphics-multimedia/storyboards-overview.md).  
  
 Pokud voláte <xref:System.Windows.FrameworkElement.RegisterName%2A> na jiný objekt než objekt, který definuje název XAML, název je stále registrován na název xaml oboru, <xref:System.Windows.FrameworkElement.RegisterName%2A> který volající objekt je držen v rámci, jako kdybyste volali na xaml namescope definující objekt.  
  
### <a name="xaml-namescopes-in-code"></a>Názvové obory XAML v kódu  
 Můžete vytvořit a potom použít XAML namescopes v kódu. Api a koncepty zapojené do vytvoření oboru názvů XAML jsou stejné i pro čisté použití [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kódu, protože procesor XAML pro použití těchto api a koncepty, když zpracovává XAML sám. Koncepty a rozhraní API existují hlavně za účelem, aby bylo možné najít objekty podle názvu ve stromu objektů, který je obvykle definován částečně nebo zcela v XAML.  
  
 Pro aplikace, které jsou vytvořeny programově a nikoli z načteného XAML, musí <xref:System.Windows.Markup.INameScope>objekt, který <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> definuje obor názvů XAML implementovat nebo být nebo odvozenou třídou, aby podporoval vytváření oboru názvů XAML v jeho instancích.  
  
 Také pro všechny prvky, které nejsou načteny a zpracovány procesorem XAML, název pole XAML pro objekt není vytvořen nebo inicializován ve výchozím nastavení. Je nutné explicitně vytvořit nový název oboru XAML pro libovolný objekt, který chcete zaregistrovat názvy do následně. Chcete-li vytvořit název pole XAML, zavolejte statickou <xref:System.Windows.NameScope.SetNameScope%2A> metodu. Zadejte objekt, který bude `dependencyObject` vlastnit jako <xref:System.Windows.NameScope.%23ctor%2A> parametr a nové `value` volání konstruktoru jako parametr.  
  
 Pokud objekt k `dependencyObject` dispozici <xref:System.Windows.NameScope.SetNameScope%2A> jako <xref:System.Windows.Markup.INameScope> pro <xref:System.Windows.FrameworkElement> není <xref:System.Windows.FrameworkContentElement>implementace <xref:System.Windows.FrameworkElement.RegisterName%2A> nebo , volání na všechny podřízené prvky nebude mít žádný vliv. Pokud se vám nepodaří vytvořit nový název oboru <xref:System.Windows.FrameworkElement.RegisterName%2A> XAML explicitně, pak volání vyvolá výjimku.  
  
 Příklad použití xaml název oboru API v kódu, naleznete [v tématu Definování oboru názvů](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>
## <a name="xaml-namescopes-in-styles-and-templates"></a>Názvy XAML ve stylech a šablonách  
 Styly a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] šablony v aplikaci poskytují možnost opakovaného použití a opětovného použití obsahu jednoduchým způsobem. Styly a šablony však mohou také obsahovat prvky s názvy XAML definovanými na úrovni šablony. Stejná šablona může být na stránce použita vícekrát. Z tohoto důvodu styly a šablony oba definovat své vlastní názvové obory XAML, nezávisle na jakékoli umístění ve stromu objektů, kde je použit styl nebo šablona.  
  
 Uvažujte následující příklad:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Zde je stejná šablona použita na dvě různá tlačítka. Pokud šablony neměly diskrétní názvové obory XAML, `TheBorder` název použitý v šabloně by způsobil kolizi názvů v oboru názvů XAML. Každá instance šablony má svůj vlastní název XAML, takže v tomto příkladu by každý konstikovaný název šablony XAML obsahoval přesně jeden název.  
  
 Styly také definovat vlastní název oboru XAML, většinou tak, aby části scénářů může mít přiřazeny konkrétní názvy. Tyto názvy umožňují řídit specifické chování, které se zaměří na prvky tohoto názvu, i v případě, že šablona byla znovu definována jako součást přizpůsobení ovládacího prvku.  
  
 Z důvodu samostatné názvobory XAML hledání pojmenovaných prvků v šabloně je náročnější než nalezení nešablonovaného pojmenovaného prvku na stránce. Nejprve je třeba určit použitou <xref:System.Windows.Controls.Control.Template%2A> šablonu tím, že získáte hodnotu vlastnosti ovládacího prvku, kde je šablona použita. Potom zavoláte verzi šablony <xref:System.Windows.FrameworkTemplate.FindName%2A>, předání ovládacího prvku, kde byla použita šablona jako druhý parametr.  
  
 Pokud jste autor ovládacího prvku a vytváříte konvenci, kde konkrétní pojmenovaný prvek v použité šabloně je cílem <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> pro chování, které je definováno samotným ovládacím prvkem, můžete použít metodu z kódu implementace ovládacího prvku. Metoda <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> je chráněna, takže k ní má přístup pouze autor ovládacího prvku.  
  
 Pokud pracujete z v rámci šablony a potřebujete se dostat do oboru názvů XAML, kde je šablona použita, získejte hodnotu <xref:System.Windows.FrameworkElement.TemplatedParent%2A>aplikace a pak tam zavolejte. <xref:System.Windows.FrameworkElement.FindName%2A> Příkladem práce v rámci šablony by bylo, pokud píšete implementaci obslužné rutiny události, kde bude událost vyvolána z prvku v použité šabloně.  
  
<a name="Namescopes_and_Name_related_APIs"></a>
## <a name="xaml-namescopes-and-name-related-apis"></a>Obory názvů XAML a api související s názvem  
 <xref:System.Windows.FrameworkElement>má <xref:System.Windows.FrameworkElement.FindName%2A> <xref:System.Windows.FrameworkElement.RegisterName%2A> , <xref:System.Windows.FrameworkElement.UnregisterName%2A> a metody. Pokud objekt, který voláte tyto metody na vlastní XAML namescope, metody volání do metody příslušné xaml namescope. V opačném případě je nadřazený prvek zkontrolován, zda vlastní název xaml a tento proces pokračuje rekurzivně, dokud není nalezen název xaml (z důvodu chování procesoru XAML je zaručeno, že bude název xaml v kořenovém adresáři). <xref:System.Windows.FrameworkContentElement>má podobné chování, s výjimkou, <xref:System.Windows.FrameworkContentElement> že žádný bude nikdy vlastní Název pole XAML. Existují metody <xref:System.Windows.FrameworkContentElement> tak, aby volání mohou být případně <xref:System.Windows.FrameworkElement> předány nadřazený prvek.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>slouží k mapování nového oboru názvů XAML na existující objekt. Můžete volat <xref:System.Windows.NameScope.SetNameScope%2A> více než jednou za účelem obnovení nebo vymazání oboru názvů XAML, ale to není běžné použití. Také <xref:System.Windows.NameScope.GetNameScope%2A> se obvykle nepoužívá z kódu.  
  
### <a name="xaml-namescope-implementations"></a>Implementace oboru názvů XAML  
 Následující třídy <xref:System.Windows.Markup.INameScope> implementovat přímo:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>nepoužívá názvy XAML nebo názvy ; místo toho používá klíče, protože se jedná o implementaci slovníku. Jediným <xref:System.Windows.ResourceDictionary> důvodem, <xref:System.Windows.Markup.INameScope> který implementuje je tak, že může vyvolat výjimky z uživatelského kódu, které pomáhají objasnit rozdíl mezi true XAML namescope a jak <xref:System.Windows.ResourceDictionary> zpracovává klíče a také zajistit, že XAML namescopes nejsou použity na nadřazené <xref:System.Windows.ResourceDictionary> prvky.  
  
 <xref:System.Windows.FrameworkTemplate>a <xref:System.Windows.Style> <xref:System.Windows.Markup.INameScope> implementovat prostřednictvím explicitních definic rozhraní. Explicitní implementace umožňují tyto názvové obory XAML chovat konvenčně, když jsou přístupné prostřednictvím <xref:System.Windows.Markup.INameScope> rozhraní, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] což je způsob, jakým jsou sdělovány obory názvů XAML interními procesy. Explicitní definice rozhraní však nejsou součástí konvenčního <xref:System.Windows.FrameworkTemplate> <xref:System.Windows.Style>povrchu rozhraní API a <xref:System.Windows.Markup.INameScope> , <xref:System.Windows.FrameworkTemplate> <xref:System.Windows.Style> protože zřídka potřebujete volat metody <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>přímo a místo toho byste použili jiné rozhraní API, například .  
  
 Následující třídy definují vlastní název xaml pomocí <xref:System.Windows.NameScope?displayProperty=nameWithType> pomocné třídy a připojení k <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> jeho implementaci název xaml prostřednictvím připojené vlastnosti:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Viz také

- [Obory názvů XAML a mapování oboru názvů pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name – direktiva](../../../desktop-wpf/xaml-services/xname-directive.md)
