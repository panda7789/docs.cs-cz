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
ms.openlocfilehash: 97889b302aac06e118c93f2d000b0eeeed8b71bb
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559934"
---
# <a name="wpf-xaml-namescopes"></a>Obory názvů WPF XAML
XAML obory názvů WPF jsou koncept, který identifikuje objekty, které jsou definovány v jazyce XAML. Názvy v jazyce XAML namescope lze použít k vytvoření vztahů mezi názvy objektů definovaných v jazyce XAML a jejich ekvivalenty instancí ve stromu objektů. Při načítání jednotlivých kořenových adresářů stránek XAML pro aplikaci XAML se obvykle vytvoří kód XAML obory názvů WPF v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spravovaném kódu. XAML obory názvů WPF jako programovací objekt jsou definovány rozhraním <xref:System.Windows.Markup.INameScope> a jsou implementovány také pomocí <xref:System.Windows.NameScope>praktické třídy.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Obory názvů WPF v načtených aplikacích XAML  
 V širším programovacím nebo počítačových kontextech programování často programovací pojmy často zahrnují princip jedinečného identifikátoru nebo názvu, který lze použít pro přístup k objektu. V systémech, které používají identifikátory nebo názvy, definuje namescope hranice, v rámci kterých bude proces nebo technika Hledat, pokud je požadován objekt daného názvu, nebo dojde k vykonání hranic, na kterých je ZAA jedinečnost identifikace názvů. Tyto obecné principy jsou pro XAML obory názvů WPF pravdivé. V jazyce WPF se při načtení stránky v kořenovém elementu stránky XAML vytvoří obory názvů WPF XAML. Každý název zadaný v rámci stránky XAML začínající na kořenu stránky se přidá do relevantního namescope XAML.  
  
 V jazyce WPF XAML elementy, které jsou běžnými kořenovými prvky (například <xref:System.Windows.Controls.Page>a <xref:System.Windows.Window>) vždy ovládají namescope XAML. Pokud je prvek jako <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> kořenovým prvkem stránky v kódu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor přidá kořen <xref:System.Windows.Controls.Page> implicitně, aby <xref:System.Windows.Controls.Page> mohl poskytnout funkční namescope jazyka XAML.  
  
> [!NOTE]
> Akce sestavení WPF vytvoří namescope XAML pro produkci XAML i v případě, že nejsou definovány žádné `Name` ani `x:Name` atributů na žádném elementu v kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Pokud se pokusíte použít stejný název dvakrát v namescope XAML, je vyvolána výjimka. Pro WPF XAML, který má kód na pozadí a je součástí zkompilované aplikace, je výjimka vyvolána při sestavení pomocí akcí sestavení WPF při vytváření vygenerované třídy pro stránku během počáteční kompilace kódu. Pro kódování XAML, které není zkompilováno pomocí žádné akce sestavení, mohou být při načtení XAML výjimky související s problémy s XAML namescope vyvolány. Návrháři XAML mohou také odhadnout problémy namescope XAML v době návrhu.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Přidání objektů do stromů objektů za běhu  
 Okamžik, kdy je analyzován XAML, představuje moment v čase, kdy je vytvořen a definován namescope WPF XAML. Pokud přidáte objekt do stromové struktury objektů v určitém bodě v čase poté, co byl vytvořen tento strom, `Name` nebo `x:Name` hodnota nového objektu automaticky neaktualizuje informace v namescope XAML. Chcete-li přidat název pro objekt do namescope WPF XAML po načtení XAML, je nutné volat odpovídající implementaci <xref:System.Windows.Markup.INameScope.RegisterName%2A> pro objekt, který definuje namescope XAML, což je obvykle kořenový adresář stránky XAML. Pokud název není zaregistrován, nelze přidaný objekt odkazovat podle názvu prostřednictvím metod, jako je například <xref:System.Windows.FrameworkElement.FindName%2A>, a nelze použít tento název pro cílení animace.  
  
 Nejběžnější scénář pro vývojáře aplikací je, že použijete <xref:System.Windows.FrameworkElement.RegisterName%2A> k registraci názvů do namescope XAML v aktuálním kořenu stránky. <xref:System.Windows.FrameworkElement.RegisterName%2A> je součástí důležitého scénáře pro scénáře, které cílí na objekty pro animace. Další informace najdete v tématu [Přehled scénářů](../graphics-multimedia/storyboards-overview.md).  
  
 Pokud zavoláte <xref:System.Windows.FrameworkElement.RegisterName%2A> na jiném objektu, než je objekt, který definuje namescope XAML, název je stále zaregistrován pro namescope XAML, že volající objekt je držen v, jako kdyby byla volána <xref:System.Windows.FrameworkElement.RegisterName%2A> v namescope definujícím objektu XAML.  
  
### <a name="xaml-namescopes-in-code"></a>Obory názvů WPF XAML v kódu  
 V kódu můžete vytvořit a potom použít XAML obory názvů WPF. Rozhraní API a koncepty spojené s vytvářením XAML namescope jsou stejné i pro použití čistě kódu, protože procesor XAML pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá tato rozhraní API a koncepty při zpracovávání samotného XAML. Koncepty a rozhraní API existují hlavně k tomu, aby bylo možné najít objekty podle názvu v rámci stromu objektů, které je obvykle definováno částečně nebo zcela v jazyce XAML.  
  
 Pro aplikace, které jsou vytvořeny programově a nikoli z načteného XAML, musí objekt definující namescope jazyka XAML implementovat <xref:System.Windows.Markup.INameScope>, nebo být odvozenou třídou <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, aby bylo možné podporovat vytváření namescopey XAML na svých instancích.  
  
 Také pro všechny prvky, které nejsou načteny a zpracovány procesorem XAML, není ve výchozím nastavení vytvořen nebo inicializován namescope XAML pro objekt. Je nutné explicitně vytvořit nové namescope XAML pro libovolný objekt, na který chcete později zaregistrovat názvy. Chcete-li vytvořit namescope XAML, zavoláte statickou metodu <xref:System.Windows.NameScope.SetNameScope%2A>. Zadejte objekt, který bude vlastnit jako parametr `dependencyObject` a nové volání konstruktoru <xref:System.Windows.NameScope.%23ctor%2A> jako parametr `value`.  
  
 Pokud objekt zadaný jako `dependencyObject` pro <xref:System.Windows.NameScope.SetNameScope%2A> není <xref:System.Windows.Markup.INameScope> implementace, <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, volání <xref:System.Windows.FrameworkElement.RegisterName%2A> na všech podřízených prvcích nebude mít žádný vliv. Pokud se nedaří vytvořit nový namescope XAML explicitně, volání <xref:System.Windows.FrameworkElement.RegisterName%2A> vyvolá výjimku.  
  
 Příklad použití rozhraní API XAML namescope v kódu najdete v tématu [definice oboru názvů](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Obory názvů WPF XAML v stylech a šablonách  
 Styly a šablony v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytují možnost opakovaného použití a opětovného použití obsahu jednoduchým způsobem. Styly a šablony však mohou obsahovat také prvky s názvy XAML definovanými na úrovni šablony. Stejnou šablonu můžete použít několikrát na stránce. Z tohoto důvodu styly a šablony definují vlastní obory názvů WPF XAML, nezávisle na jakémkoli umístění ve stromu objektů, kde je použit styl nebo šablona.  
  
 Vezměte v úvahu v následujícím příkladu:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 V tomto případě se stejná šablona aplikuje na dvě různá tlačítka. Pokud šablony neobsahovaly diskrétní obory názvů WPF XAML, název `TheBorder` použitý v šabloně způsobí kolizi názvů v namescope XAML. Každé vytvoření instance šablony má vlastní namescope XAML, takže v tomto příkladu by měla být v tomto příkladu každá vytvořená instance XAML namescope šablony obsahovat přesně jeden název.  
  
 Styly také definují vlastní namescope XAML, což většinou umožňuje, aby části scénářů měly přiřazeny konkrétní názvy. Tyto názvy umožňují řídit konkrétní chování ovládacího prvku, které budou cílem prvků daného názvu, a to i v případě, že byla šablona znovu definovaná jako součást přizpůsobení ovládacího prvku.  
  
 Z důvodu samostatného obory názvů WPF jazyka XAML je hledání pojmenovaných prvků v šabloně náročnější než hledání pojmenovaného prvku, který není šablonou na stránce. Nejdříve je nutné určit použitou šablonu tím, že získáte hodnotu vlastnosti <xref:System.Windows.Controls.Control.Template%2A> ovládacího prvku, ve kterém je šablona použita. Pak zavolejte šablonu verze <xref:System.Windows.FrameworkTemplate.FindName%2A>a předáním ovládacího prvku, kde byla šablona použita, jako druhý parametr.  
  
 Pokud jste autorem ovládacího prvku a generujete konvenci, kde konkrétní pojmenovaný element v použité šabloně je cílem pro chování, které je definováno samotným ovládacím prvkem, můžete použít metodu <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> z kódu implementace ovládacího prvku. Metoda <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> je chráněna, takže k ní má přístup pouze autor ovládacího prvku.  
  
 Pokud pracujete v rámci šablony a potřebujete získat přístup k namescope XAML, kde je šablona použita, Získejte hodnotu <xref:System.Windows.FrameworkElement.TemplatedParent%2A>a potom zavolejte <xref:System.Windows.FrameworkElement.FindName%2A>. Příklad práce v rámci šablony by byl, pokud píšete implementaci obslužné rutiny události, kde se událost vyvolá z prvku v použité šabloně.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>Obory názvů WPF XAML a rozhraní API související s názvem  
 <xref:System.Windows.FrameworkElement> má metody <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> a <xref:System.Windows.FrameworkElement.UnregisterName%2A>. Pokud objekt, který zavoláte tyto metody pro vlastní namescope XAML, metody volají do metod relevantního XAML namescope. V opačném případě je kontrolován nadřazený prvek, zda je vlastníkem XAML namescope a tento proces pokračuje rekurzivně, dokud není nalezen namescope XAML (vzhledem k chování procesoru XAML, je zaručeno, že by to byl namescope XAML v kořenu). <xref:System.Windows.FrameworkContentElement> má podobné chování s výjimkou, že žádné <xref:System.Windows.FrameworkContentElement> by nikdy nevlastní namescope XAML. Metody existují na <xref:System.Windows.FrameworkContentElement>, aby bylo možné volat nakonec do <xref:System.Windows.FrameworkElement> nadřazeného elementu.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> slouží k namapování nového objektu XAML namescope na existující objekt. Můžete volat <xref:System.Windows.NameScope.SetNameScope%2A> více než jednou, aby bylo možné resetovat nebo vymazat namescope XAML, ale to není běžné použití. <xref:System.Windows.NameScope.GetNameScope%2A> se také obvykle nepoužívá z kódu.  
  
### <a name="xaml-namescope-implementations"></a>Implementace XAML namescope  
 Následující třídy implementují <xref:System.Windows.Markup.INameScope> přímo:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> nepoužívá názvy XAML ani obory názvů WPF; místo toho používá klíče, protože se jedná o implementaci slovníku. Jediným důvodem, proč <xref:System.Windows.ResourceDictionary> implementuje <xref:System.Windows.Markup.INameScope>, je, že může vyvolávat výjimky pro uživatelský kód, které vám pomohou objasnit rozdíl mezi skutečným namescope XAML a způsob, jakým <xref:System.Windows.ResourceDictionary> zpracovává klíče, a také zajistit, aby obory názvů wpfy XAML nebyly aplikovány na <xref:System.Windows.ResourceDictionary> nadřazenými prvky.  
  
 <xref:System.Windows.FrameworkTemplate> a <xref:System.Windows.Style> implementují <xref:System.Windows.Markup.INameScope> prostřednictvím explicitních definic rozhraní. Explicitní implementace umožňují, aby se tyto XAML obory názvů WPF chovat bez konvence, když jsou dostupné prostřednictvím rozhraní <xref:System.Windows.Markup.INameScope>, což je způsob, jakým [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interní procesy komunikuje s XAML obory názvů WPF. Definice explicitního rozhraní ale nejsou součástí konvenčního prostoru rozhraní API <xref:System.Windows.FrameworkTemplate> a <xref:System.Windows.Style>, protože není zřídka nutné volat <xref:System.Windows.Markup.INameScope> metody pro <xref:System.Windows.FrameworkTemplate> a <xref:System.Windows.Style> přímo a místo toho použít jiné rozhraní API, jako je <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Následující třídy definují vlastní namescope XAML pomocí pomocné třídy <xref:System.Windows.NameScope?displayProperty=nameWithType> a připojují se ke své implementaci XAML namescope prostřednictvím vlastnosti připojené <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType>:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Viz také:

- [Obory názvů XAML a mapování oboru názvů pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name – direktiva](../../../desktop-wpf/xaml-services/xname-directive.md)
