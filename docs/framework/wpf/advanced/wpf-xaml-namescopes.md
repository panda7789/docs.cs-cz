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
ms.openlocfilehash: f5a49198d6f55c9a3aa3c7557a96ab791d54351b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366748"
---
# <a name="wpf-xaml-namescopes"></a>Obory názvů WPF XAML
Obory názvů XAML jsou pojem, který identifikuje objekty, které jsou definovány v XAML. Názvy v XAML namescope lze použít k vytvoření relace mezi XAML definované názvy objektů a jejich ekvivalenty instance ve stromu objektů. Obvykle XAML obory názvů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spravovaného kódu jsou vytvořeny při načítání jednotlivých stránek XAML kořeny pro aplikace XAML. Obory názvů XAML jako programovací objekty jsou definovány <xref:System.Windows.Markup.INameScope> rozhraní a jsou také implementováno třídou praktické <xref:System.Windows.NameScope>.  
  
  
  
<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Obory názvů v aplikacích XAML načteno  
 Koncepty programování v širším programování nebo kontextu vědy počítače často zahrnují Princip jedinečný identifikátor nebo název, který můžete použít pro přístup k objektu. Pro systémy, které používají identifikátory nebo názvy namescope definuje hranice v rámci které procesu nebo techniku bude vyhledávání, pokud je požadováno objekt s tímto názvem nebo hranice, ve které je vynucuje jedinečnosti identifikace názvy. Tyto obecné zásady platí pro obory názvů XAML. V WPF obory názvů XAML vytvoří v kořenovém elementu stránky XAML při načtení stránky. Každý název zadaný v rámci stránky XAML počínaje kořenovou stránku se přidá do příslušné namescope XAML.  
  
 V XAML WPF, elementy, které jsou běžné kořenových elementů (například <xref:System.Windows.Controls.Page>, a <xref:System.Windows.Window>) vždy řídit XAML namescope. Pokud element, jako <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> je kořenový element na stránce v kódu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] přidá procesor <xref:System.Windows.Controls.Page> root implicitně tak, aby <xref:System.Windows.Controls.Page> může poskytnout namescope XAML pracovní.  
  
> [!NOTE]
>  Akce sestavení WPF vytvořit namescope XAML pro produkční prostředí XAML i když žádné `Name` nebo `x:Name` atributy jsou definovány ve všech elementů [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 Pokud se pokusíte použít stejný název v jakékoli obor namescope XAML dvakrát, je vyvolána výjimka. Pro WPF XAML, který je použití modelu code-behind a je součástí kompilovanou aplikaci, je výjimka vyvolána v okamžiku sestavení akcemi sestavení WPF, při vytváření generované třídy stránky během kompilace počáteční značky. Výjimky související s problémy namescope XAML pro XAML, který není kód zkompilován s žádnou akci sestavení, může být vyvolána při načtení XAML. Návrháři XAML může také předvídat problémy namescope XAML v době návrhu.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Přidání objektů do objektu modulu Runtime stromů  
 V okamžiku, který je analyzovány XAML představuje okamžik v čase, který je vytvořen a definovaný obor namescope WPF XAML. Pokud chcete přidat objekt stromu objektů v bodě v čase po XAML, který vytvořil stromu byl analyzován, `Name` nebo `x:Name` hodnotu na nový objekt se neaktualizuje automaticky informace v XAML namescope. Chcete-li přidat název pro objekt do WPF XAML namescope po načtení XAML, musí volat odpovídající provádění <xref:System.Windows.Markup.INameScope.RegisterName%2A> na objekt, který definuje obor namescope XAML, který je obvykle kořenové stránky XAML. Pokud název není zaregistrovaný, přidání objektu nelze odkazovat podle názvu prostřednictvím metod, jako <xref:System.Windows.FrameworkElement.FindName%2A>, a nemůžete použít tento název pro cílení na animace.  
  
 Nejběžnější scénář pro vývojáře aplikací je, že použijete <xref:System.Windows.FrameworkElement.RegisterName%2A> k registraci názvů do namescope XAML v kořenovém adresáři aktuální stránky. <xref:System.Windows.FrameworkElement.RegisterName%2A> je součástí scénáře důležité pro scénáře této cílové objektů pro animace. Další informace najdete v tématu [přehled scénářů](../graphics-multimedia/storyboards-overview.md).  
  
 Při volání <xref:System.Windows.FrameworkElement.RegisterName%2A> u objektu jiného než objekt, který definuje obor namescope XAML, název je stále zaregistrovaná namescope XAML, volání objektů uložených v rámci, jako by měly volat <xref:System.Windows.FrameworkElement.RegisterName%2A> na XAML namescope definice objektu.  
  
### <a name="xaml-namescopes-in-code"></a>Obory názvů XAML v kódu  
 Můžete vytvořit a pak použijte obory názvů XAML v kódu. Rozhraní API a koncepty v XAML namescope vytvoření shodné i pro použití čistého kódu, protože procesor XAML pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá tato rozhraní API a koncepty při zpracování XAML, samotného. Koncepty a rozhraní API existují především pro účely schopnost najít objekty podle názvu v rámci stromu objektů, který je obvykle definován částečně nebo zcela v XAML.  
  
 Pro aplikace, které jsou vytvořené prostřednictvím kódu programu a ne z XAML načteno, musí implementovat objekt, který definuje obor namescope XAML <xref:System.Windows.Markup.INameScope>, nebo se <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy, aby bylo možné podporovat vytváření XAML namescope na jeho instance.  
  
 Také pro libovolný element, který není načteny a zpracovány procesorem XAML, namescope XAML pro objekt není vytvořena nebo ve výchozím nastavení inicializována. Musíte explicitně vytvořit nový obor namescope XAML pro libovolný objekt, který máte v úmyslu registraci názvů na později. Pokud chcete vytvořit obor namescope XAML, zavolejte statickou <xref:System.Windows.NameScope.SetNameScope%2A> metody. Zadejte objekt, který bude jej jako vlastní `dependencyObject` parametr a nový <xref:System.Windows.NameScope.%23ctor%2A> volání konstruktoru, jako `value` parametru.  
  
 Pokud je objekt zadán jako `dependencyObject` pro <xref:System.Windows.NameScope.SetNameScope%2A> není <xref:System.Windows.Markup.INameScope> implementaci <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, volání <xref:System.Windows.FrameworkElement.RegisterName%2A> na všech podřízených elementů nebude mít žádný efekt. Pokud chcete vytvořit nový obor namescope XAML explicitně, pak zavolá do <xref:System.Windows.FrameworkElement.RegisterName%2A> vyvolá výjimku.  
  
 Příklad použití XAML namescope rozhraní API v kódu, naleznete v tématu [definování rozsahu názvů](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Obory názvů XAML v styly a šablony  
 Styly a šablony v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytují možnost opakovaně používat a znovu zásadu použijte obsah přímo. Ale – styly a šablony může taky obsahovat elementy s názvy XAML, které jsou definované na úrovni šablony. Tento stejné šablony může na stránce použít více než jednou. Z tohoto důvodu definování vlastní XAML obory názvů, nezávisle na jakékoliv umístění ve stromu objektů, je použití stylu nebo šablony – styly a šablony.  
  
 Vezměte v úvahu v následujícím příkladu:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Stejné šablony se tady platí pro dvě různá tlačítka. Pokud šablony neměla samostatné obory názvů XAML `TheBorder` název použitý v šabloně by způsobila kolizi názvů v XAML namescope. Každá instance šablona má svůj vlastní obor namescope XAML, takže v tomto příkladu každá instance šablona XAML namescope by obsahovat přesně jeden název.  
  
 Styly také definovat své vlastní obor namescope XAML, většinou tak, aby součástí scénářů může mít konkrétní názvy přiřazené. Tyto názvy aktivuje ovládací prvek konkrétní chování, které se zaměří na elementy s tímto názvem, i v případě, že šablona byla znovu definovali jako součást přizpůsobení ovládacího prvku.  
  
 Z důvodu XAML samostatné obory názvů, hledání elementů pojmenovaných v šabloně je náročnější než hledání bez použití šablon s názvem elementu na stránce. Je potřeba nejprve určit použitá šablona tím, že získáme <xref:System.Windows.Controls.Control.Template%2A> hodnota vlastnosti ovládacího prvku, pokud je šablona použita. Potom, voláte verze šablony <xref:System.Windows.FrameworkTemplate.FindName%2A>, předávání ovládací prvek, ve kterém byla šablona použita jako druhý parametr.  
  
 Pokud jste autorem ovládacího prvku a generují konvenci, kde je konkrétní element v šabloně použité s názvem cíl pro chování, který je reprezentován samotný ovládací prvek, můžete použít <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metody v kódu implementaci ovládacího prvku. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> Je chráněný, tedy pouze autor ovládacího prvku k němu má přístup.  
  
 Pokud pracujete v rámci šablony a nemusí, aby získali XAML namescope, ve kterém je šablona použita, získání hodnoty <xref:System.Windows.FrameworkElement.TemplatedParent%2A>a pak vyvolejte <xref:System.Windows.FrameworkElement.FindName%2A> existuje. Příkladem práce v rámci šablony může být při psaní implementaci obslužné rutiny události kde událost, bude vyvolána z prvku v použitá šablona.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>Obory názvů XAML a rozhraní API související s názvem  
 <xref:System.Windows.FrameworkElement> má <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> a <xref:System.Windows.FrameworkElement.UnregisterName%2A> metody. Pokud objekt, který tyto metody volat na vlastní obor namescope XAML, volání metody do metody relevantní namescope XAML. V opačném případě nadřazeného elementu je zaškrtnuté políčko vlastní obor namescope XAML, a tento proces pokračuje rekurzivně, dokud nebude nalezen XAML namescope (kvůli chování procesoru XAML, že je zaručeně namescope XAML v kořenovém adresáři). <xref:System.Windows.FrameworkContentElement> se podobá chování, s výjimkou, která žádné <xref:System.Windows.FrameworkContentElement> se někdy vlastní obor namescope XAML. Metody existovat na <xref:System.Windows.FrameworkContentElement> tak, aby volání může být přeposílán nakonec položky <xref:System.Windows.FrameworkElement> nadřazeného elementu.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> slouží k mapování nový obor namescope XAML na existující objekt. Můžete volat <xref:System.Windows.NameScope.SetNameScope%2A> více než jednou. aby bylo možné resetovat nebo zrušte XAML namescope, ale to není běžné použití. Navíc <xref:System.Windows.NameScope.GetNameScope%2A> se obvykle nepoužívá z kódu.  
  
### <a name="xaml-namescope-implementations"></a>Implementace Namescope XAML  
 Následující třídy implementují <xref:System.Windows.Markup.INameScope> přímo:  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> nepoužívá XAML názvy nebo obory názvů; používá klíče místo, protože se jedná implementaci slovníku. Pouze důvodu <xref:System.Windows.ResourceDictionary> implementuje <xref:System.Windows.Markup.INameScope> je tak může vyvolat výjimky do uživatelského kódu, které pomohou vyjasnit, rozdíl mezi true XAML namescope a jak <xref:System.Windows.ResourceDictionary> zpracovává klíče a také, aby zajistil, že obory názvů XAML se nepoužije <xref:System.Windows.ResourceDictionary> nadřazené prvky.  
  
 <xref:System.Windows.FrameworkTemplate> a <xref:System.Windows.Style> implementovat <xref:System.Windows.Markup.INameScope> prostřednictvím explicitního rozhraní definice. Explicitní implementace povolit tyto obory názvů XAML konvenčně chovat, když jsou přístupné prostřednictvím <xref:System.Windows.Markup.INameScope> rozhraní, které je, jak se předávají obory názvů XAML pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interních procesů. Definice explicitního rozhraní, které nejsou součástí konvenční plochy rozhraní API, ale <xref:System.Windows.FrameworkTemplate> a <xref:System.Windows.Style>, protože zřídka potřebné k volání <xref:System.Windows.Markup.INameScope> metody <xref:System.Windows.FrameworkTemplate> a <xref:System.Windows.Style> přímo a místo toho byste použili další rozhraní API například <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Následující třídy definují vlastní obor namescope XAML pomocí <xref:System.Windows.NameScope?displayProperty=nameWithType> pomocná třída a připojení k její implementaci namescope XAML prostřednictvím <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> přidružená vlastnost:  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Viz také:
- [Obory názvů XAML a mapování oboru názvů pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name – direktiva](../../xaml-services/x-name-directive.md)
