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
ms.openlocfilehash: edf5c8a828bea182cd87542276fb7eb2df1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917327"
---
# <a name="wpf-xaml-namescopes"></a>Obory názvů WPF XAML
XAML obory názvů WPF jsou koncept, který identifikuje objekty, které jsou definovány v jazyce XAML. Názvy v jazyce XAML namescope lze použít k vytvoření vztahů mezi názvy objektů definovaných v jazyce XAML a jejich ekvivalenty instancí ve stromu objektů. Při načítání jednotlivých kořenových [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] adresářů stránek XAML pro aplikaci XAML se obvykle vytvoří XAML obory názvů WPF ve spravovaném kódu. XAML obory názvů WPF jako programovací objekt jsou definovány <xref:System.Windows.Markup.INameScope> rozhraním a jsou také implementovány pomocí praktické třídy. <xref:System.Windows.NameScope>  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Obory názvů WPF v načtených aplikacích XAML  
 V širším programovacím nebo počítačových kontextech programování často programovací pojmy často zahrnují princip jedinečného identifikátoru nebo názvu, který lze použít pro přístup k objektu. V systémech, které používají identifikátory nebo názvy, definuje namescope hranice, v rámci kterých bude proces nebo technika Hledat, pokud je požadován objekt daného názvu, nebo dojde k vykonání hranic, na kterých je ZAA jedinečnost identifikace názvů. Tyto obecné principy jsou pro XAML obory názvů WPF pravdivé. V jazyce WPF se při načtení stránky v kořenovém elementu stránky XAML vytvoří obory názvů WPF XAML. Každý název zadaný v rámci stránky XAML začínající na kořenu stránky se přidá do relevantního namescope XAML.  
  
 V jazyce WPF XAML elementy, které jsou běžnými kořenovými prvky <xref:System.Windows.Controls.Page>(například <xref:System.Windows.Window>a) vždy ovládají namescope XAML. Pokud <xref:System.Windows.FrameworkElement> prvek jako <xref:System.Windows.Controls.Page> nebo <xref:System.Windows.FrameworkContentElement> je kořenovým prvkem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky v kódu <xref:System.Windows.Controls.Page> , procesor přidá kořen implicitně, aby mohl poskytnout funkční namescope jazyka XAML.  
  
> [!NOTE]
> Akce sestavení WPF vytvoří namescope XAML pro produkci XAML i v případě, že `Name` nejsou `x:Name` definovány žádné atributy nebo v žádném elementu ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značce.  
  
 Pokud se pokusíte použít stejný název dvakrát v namescope XAML, je vyvolána výjimka. Pro WPF XAML, který má kód na pozadí a je součástí zkompilované aplikace, je výjimka vyvolána při sestavení pomocí akcí sestavení WPF při vytváření vygenerované třídy pro stránku během počáteční kompilace kódu. Pro kódování XAML, které není zkompilováno pomocí žádné akce sestavení, mohou být při načtení XAML výjimky související s problémy s XAML namescope vyvolány. Návrháři XAML mohou také odhadnout problémy namescope XAML v době návrhu.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Přidání objektů do stromů objektů za běhu  
 Okamžik, kdy je analyzován XAML, představuje moment v čase, kdy je vytvořen a definován namescope WPF XAML. Přidáte-li objekt do stromové struktury objektů v určitém bodě v čase poté, co byl vytvořen tento stromový postup, `Name` hodnota nebo `x:Name` v novém objektu automaticky neaktualizuje informace v namescope XAML. Chcete-li přidat název pro objekt do namescope WPF XAML po načtení XAML, je nutné zavolat příslušnou implementaci <xref:System.Windows.Markup.INameScope.RegisterName%2A> objektu, který definuje namescope XAML, což je obvykle kořenový adresář stránky XAML. Pokud název není zaregistrován, nelze přidaný objekt odkazovat podle názvu prostřednictvím metod <xref:System.Windows.FrameworkElement.FindName%2A>, jako je, a nelze použít tento název pro cílení animace.  
  
 Nejběžnější scénář pro vývojáře aplikací je, že použijete <xref:System.Windows.FrameworkElement.RegisterName%2A> k registraci názvů do namescope XAML v aktuálním kořenu stránky. <xref:System.Windows.FrameworkElement.RegisterName%2A>je součástí důležitého scénáře pro scénáře, které cílí na objekty pro animace. Další informace najdete v tématu [Přehled scénářů](../graphics-multimedia/storyboards-overview.md).  
  
 Pokud voláte <xref:System.Windows.FrameworkElement.RegisterName%2A> na jiný objekt, než je objekt, který definuje namescope XAML, název je stále zaregistrován pro namescope jazyka XAML, který volá objekt v rámci, jako kdyby byl volán <xref:System.Windows.FrameworkElement.RegisterName%2A> v objektu XAML namescope define Object.  
  
### <a name="xaml-namescopes-in-code"></a>Obory názvů WPF XAML v kódu  
 V kódu můžete vytvořit a potom použít XAML obory názvů WPF. Rozhraní API a koncepty spojené s vytvářením XAML namescope jsou stejné i pro použití čistě kódu, protože procesor XAML pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá tato rozhraní API a koncepty při zpracovávání samotného XAML. Koncepty a rozhraní API existují hlavně k tomu, aby bylo možné najít objekty podle názvu v rámci stromu objektů, které je obvykle definováno částečně nebo zcela v jazyce XAML.  
  
 Pro aplikace, které jsou vytvořeny programově a nikoli z načteného XAML, objekt definující namescope XAML musí implementovat <xref:System.Windows.Markup.INameScope>, nebo <xref:System.Windows.FrameworkElement> být <xref:System.Windows.FrameworkContentElement> odvozenou třídou, aby bylo možné podporovat vytváření namescope XAML na svém instance.  
  
 Také pro všechny prvky, které nejsou načteny a zpracovány procesorem XAML, není ve výchozím nastavení vytvořen nebo inicializován namescope XAML pro objekt. Je nutné explicitně vytvořit nové namescope XAML pro libovolný objekt, na který chcete později zaregistrovat názvy. Chcete-li vytvořit namescope XAML, zavoláte <xref:System.Windows.NameScope.SetNameScope%2A> statickou metodu. Zadejte objekt, který bude vlastníkem jako `dependencyObject` parametr, a jako `value` parametr zavolá <xref:System.Windows.NameScope.%23ctor%2A> nový konstruktor.  
  
 Pokud objekt poskytnutý jako `dependencyObject` pro <xref:System.Windows.NameScope.SetNameScope%2A> <xref:System.Windows.Markup.INameScope> <xref:System.Windows.FrameworkContentElement>není implementace nebo volání <xref:System.Windows.FrameworkElement.RegisterName%2A> u všech podřízených prvků nebude mít žádný vliv. <xref:System.Windows.FrameworkElement> Pokud se nedaří vytvořit nový namescope XAML explicitně, volání <xref:System.Windows.FrameworkElement.RegisterName%2A> vyvolají výjimku.  
  
 Příklad použití rozhraní API XAML namescope v kódu najdete v tématu [definice oboru názvů](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Obory názvů WPF XAML v stylech a šablonách  
 Styly a šablony v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nástroji poskytují možnost opakovaně používat a znovu použít obsah v jednoduchém způsobu. Styly a šablony však mohou obsahovat také prvky s názvy XAML definovanými na úrovni šablony. Stejnou šablonu můžete použít několikrát na stránce. Z tohoto důvodu styly a šablony definují vlastní obory názvů WPF XAML, nezávisle na jakémkoli umístění ve stromu objektů, kde je použit styl nebo šablona.  
  
 Vezměte v úvahu v následujícím příkladu:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 V tomto případě se stejná šablona aplikuje na dvě různá tlačítka. Pokud šablony neobsahovaly diskrétní obory názvů WPF XAML, `TheBorder` název použitý v šabloně způsobí kolizi názvů v namescope XAML. Každé vytvoření instance šablony má vlastní namescope XAML, takže v tomto příkladu by měla být v tomto příkladu každá vytvořená instance XAML namescope šablony obsahovat přesně jeden název.  
  
 Styly také definují vlastní namescope XAML, což většinou umožňuje, aby části scénářů měly přiřazeny konkrétní názvy. Tyto názvy umožňují řídit konkrétní chování ovládacího prvku, které budou cílem prvků daného názvu, a to i v případě, že byla šablona znovu definovaná jako součást přizpůsobení ovládacího prvku.  
  
 Z důvodu samostatného obory názvů WPF jazyka XAML je hledání pojmenovaných prvků v šabloně náročnější než hledání pojmenovaného prvku, který není šablonou na stránce. Nejdříve je nutné určit použitou šablonu tím <xref:System.Windows.Controls.Control.Template%2A> , že získáte hodnotu vlastnosti ovládacího prvku, ve kterém je šablona použita. Pak zavoláte verzi <xref:System.Windows.FrameworkTemplate.FindName%2A>šablony a předáte ovládacímu prvku, kde byla šablona použita, jako druhý parametr.  
  
 Pokud jste autorem ovládacího prvku a generujete konvenci, kde konkrétní pojmenovaný element v použité šabloně je cílem pro chování, které je definováno samotným ovládacím prvkem, můžete použít <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metodu z kódu implementace ovládacího prvku. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> Metoda je chráněna, takže k ní má přístup pouze autor ovládacího prvku.  
  
 Pokud pracujete v rámci šablony a potřebujete získat přístup k namescope XAML, kde je šablona použita, Získejte hodnotu <xref:System.Windows.FrameworkElement.TemplatedParent%2A>a potom zavolejte. <xref:System.Windows.FrameworkElement.FindName%2A> Příklad práce v rámci šablony by byl, pokud píšete implementaci obslužné rutiny události, kde se událost vyvolá z prvku v použité šabloně.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>Obory názvů WPF XAML a rozhraní API související s názvem  
 <xref:System.Windows.FrameworkElement>má <xref:System.Windows.FrameworkElement.FindName%2A>a metody<xref:System.Windows.FrameworkElement.UnregisterName%2A> . <xref:System.Windows.FrameworkElement.RegisterName%2A> Pokud objekt, který zavoláte tyto metody pro vlastní namescope XAML, metody volají do metod relevantního XAML namescope. V opačném případě je kontrolován nadřazený prvek, zda je vlastníkem XAML namescope a tento proces pokračuje rekurzivně, dokud není nalezen namescope XAML (vzhledem k chování procesoru XAML, je zaručeno, že by to byl namescope XAML v kořenu). <xref:System.Windows.FrameworkContentElement>má analogické chování s výjimkou, že <xref:System.Windows.FrameworkContentElement> ne nikdy nebude vlastnit namescope XAML. Metody existují <xref:System.Windows.FrameworkContentElement> , aby bylo možné volání předávat nakonec <xref:System.Windows.FrameworkElement> nadřazenému elementu.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>slouží k namapování nového objektu XAML namescope na existující objekt. Můžete zavolat <xref:System.Windows.NameScope.SetNameScope%2A> více než jednou, aby bylo možné resetovat nebo vymazat namescope XAML, ale to není běžné použití. <xref:System.Windows.NameScope.GetNameScope%2A> Také se obvykle nepoužívá z kódu.  
  
### <a name="xaml-namescope-implementations"></a>Implementace XAML namescope  
 Následující třídy implementují <xref:System.Windows.Markup.INameScope> přímo:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>nepoužívá názvy XAML ani obory názvů WPF; místo toho používá klíče, protože se jedná o implementaci slovníku. Jediný důvod, který <xref:System.Windows.ResourceDictionary> implementuje <xref:System.Windows.Markup.INameScope> , je, aby mohl vyvolat výjimky pro uživatelský kód, které pomohou objasnit rozdíl mezi skutečným namescope <xref:System.Windows.ResourceDictionary> XAML a způsobem, jakým jsou klíče, a také zajistit, aby obory názvů wpfy XAML nebyly aplikovány na <xref:System.Windows.ResourceDictionary> podle nadřazených elementů.  
  
 <xref:System.Windows.FrameworkTemplate>a <xref:System.Windows.Style> implementujte <xref:System.Windows.Markup.INameScope> pomocí explicitních definic rozhraní. Explicitní implementace umožňují, aby se tyto XAML obory názvů WPF chovat bez konvence, pokud jsou k nim <xref:System.Windows.Markup.INameScope> přistupované prostřednictvím rozhraní, což je způsob, jakým jsou předávány XAML obory názvů WPF pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interních procesů. Explicitní definice rozhraní ale nejsou součástí <xref:System.Windows.FrameworkTemplate> konvenčního prostoru rozhraní API a <xref:System.Windows.Style>, protože <xref:System.Windows.Markup.INameScope> zřídka potřebujete volat metody na <xref:System.Windows.FrameworkTemplate> a <xref:System.Windows.Style> přímo a místo toho použít jiné rozhraní API. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>například.  
  
 Následující třídy definují vlastní namescope XAML pomocí <xref:System.Windows.NameScope?displayProperty=nameWithType> pomocné třídy a připojení ke své implementaci XAML namescope <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> prostřednictvím připojené vlastnosti:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Viz také:

- [Obory názvů XAML a mapování oboru názvů pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name – direktiva](../../xaml-services/x-name-directive.md)
