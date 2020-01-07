---
title: Slovníky sloučených prostředků
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 899955a9f3302e67de4efa0ce0cb6baf6bf0ec5d
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559778"
---
# <a name="merged-resource-dictionaries"></a>Slovníky sloučených prostředků
prostředky [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] podporují funkci sloučeného slovníku prostředků. Tato funkce poskytuje způsob, jak definovat část prostředků [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace mimo kompilovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikace. Prostředky je pak možné sdílet mezi aplikacemi a jsou taky pohodlnější izolované pro lokalizaci.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Představení sloučeného slovníku prostředků  
 V kódu použijte následující syntaxi k představení sloučeného slovníku prostředků na stránku:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Všimněte si, že <xref:System.Windows.ResourceDictionary> element nemá [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md), která je obecně nutná pro všechny položky v kolekci prostředků. Ale další odkaz <xref:System.Windows.ResourceDictionary> v rámci kolekce <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> je zvláštní případ vyhrazený pro tento scénář sloučeného slovníku prostředků. <xref:System.Windows.ResourceDictionary>, který zavádí sloučený slovník prostředků, nemůže mít [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md). Každý <xref:System.Windows.ResourceDictionary> v rámci kolekce <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> obvykle určuje atribut <xref:System.Windows.ResourceDictionary.Source%2A>. Hodnota <xref:System.Windows.ResourceDictionary.Source%2A> by měla být identifikátor URI (Uniform Resource Identifier), který se překládá na umístění souboru prostředků, který se má sloučit. Cíl tohoto identifikátoru URI musí být jiný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor s <xref:System.Windows.ResourceDictionary> jako jeho kořenový element.  
  
> [!NOTE]
> Je možné definovat prostředky v rámci <xref:System.Windows.ResourceDictionary>, který je zadaný jako sloučený slovník, a to buď jako alternativu k určení <xref:System.Windows.ResourceDictionary.Source%2A>, nebo kromě jakýchkoli prostředků, které jsou zahrnuté ze zadaného zdroje. Nejedná se však o běžný scénář. hlavním scénářem pro sloučené slovníky je sloučení prostředků z umístění externích souborů. Chcete-li určit prostředky v rámci značky stránky, je obvykle třeba je definovat v hlavním <xref:System.Windows.ResourceDictionary> a nikoli ve sloučených slovnících.  
  
## <a name="merged-dictionary-behavior"></a>Chování sloučeného slovníku  
 Prostředky ve sloučeném slovníku zabírají umístění v oboru vyhledávání prostředků, které je bezprostředně po rozsahu hlavního slovníku prostředků, do kterého jsou sloučeny. I když klíč prostředku musí být jedinečný v rámci každého jednotlivého slovníku, klíč může existovat několikrát v sadě sloučených slovníků. V takovém případě se vrácený prostředek dostane z posledního slovníku, který byl nalezen postupně v kolekci <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Pokud byla <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekce definována v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], pak pořadí sloučených slovníků v kolekci je pořadí prvků, jak je uvedeno v označení. Pokud je klíč definovaný v primárním slovníku a také ve slovníku, který byl sloučený, povede vrácený prostředek z primárního slovníku. Tato pravidla oboru platí stejně pro statické odkazy na prostředky i pro dynamické odkazy na prostředky.  
  
### <a name="merged-dictionaries-and-code"></a>Sloučené slovníky a kód  
 Sloučené slovníky lze do `Resources` slovníku přidat prostřednictvím kódu. Výchozí hodnota, zpočátku prázdná <xref:System.Windows.ResourceDictionary>, která existuje pro vlastnost `Resources`, má také výchozí výchozí hodnotu, která je zpočátku prázdná <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> vlastnosti kolekce. Chcete-li přidat sloučený slovník prostřednictvím kódu, získáte odkaz na požadovaný primární <xref:System.Windows.ResourceDictionary>, získáte hodnotu vlastnosti <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> a zavoláte `Add` na obecné `Collection`, který je obsažen v <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Objekt, který přidáte, musí být nový <xref:System.Windows.ResourceDictionary>. V kódu není nastavena vlastnost <xref:System.Windows.ResourceDictionary.Source%2A>. Místo toho musíte získat <xref:System.Windows.ResourceDictionary> objekt buď vytvořením jednoho nebo načtením. Jedním ze způsobů, jak načíst existující <xref:System.Windows.ResourceDictionary> pro volání <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> v existujícím streamu souborů [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], který má kořenový adresář <xref:System.Windows.ResourceDictionary>, a poté přetypování <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> návratové hodnoty na <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>Identifikátory URI sloučeného slovníku prostředků  
 Existuje několik postupů, jak zahrnout sloučený slovník prostředků, který je určen formátem identifikátoru URI (Uniform Resource Identifier), který budete používat. V podstatě řečeno, tyto techniky lze rozdělit do dvou kategorií: prostředky, které jsou kompilovány jako součást projektu, a prostředky, které nejsou kompilovány jako součást projektu.  
  
 Pro prostředky, které jsou kompilovány jako součást projektu, můžete použít relativní cestu, která odkazuje na umístění prostředku. Relativní cesta je vyhodnocena během kompilace. Váš prostředek musí být definován jako součást projektu jako akce sestavení prostředku. Pokud zahrnete soubor Resource. XAML do projektu jako prostředek, nemusíte kopírovat soubor prostředků do výstupního adresáře, prostředek je již obsažen v kompilované aplikaci. Můžete také použít akci sestavení obsahu, ale je nutné zkopírovat soubory do výstupního adresáře a také nasadit soubory prostředků ve stejném vztahu cesty ke spustitelnému souboru.  
  
> [!NOTE]
> Nepoužívejte akci sestavení vloženého prostředku. Vlastní akce sestavení je podporována pro aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ale řešení <xref:System.Windows.ResourceDictionary.Source%2A> nezahrnuje <xref:System.Resources.ResourceManager>, a proto nemůže oddělit jednotlivé prostředky z datového proudu. Vložený prostředek můžete i nadále používat pro jiné účely, pokud jste také použili <xref:System.Resources.ResourceManager> pro přístup k prostředkům.  
  
 Související technikou je použít identifikátor URI balíčku k souboru [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a odkazovat na něj jako na zdroj. Identifikátor URI balíčku umožňuje odkazy na komponenty odkazovaných sestavení a další techniky. Další informace o identifikátorech URI balíčku naleznete v tématu [prostředky aplikace WPF, obsah a datové soubory](../app-development/wpf-application-resource-content-and-data-files.md).  
  
 U prostředků, které nejsou kompilovány jako součást projektu, je identifikátor URI vyhodnocen za běhu. Pro odkazování na soubor prostředků můžete použít společný přenos URI, jako je soubor: nebo http:. Nevýhodou použití nezkompilovaného přístupu k prostředkům je tento soubor: přístup vyžaduje další kroky nasazení a http: předpokládá se, že přístup vychází z zóny zabezpečení Internetu.  
  
### <a name="reusing-merged-dictionaries"></a>Znovu použít sloučené slovníky  
 Sloučené slovníky prostředků mezi aplikacemi můžete opakovaně používat nebo sdílet, protože ke sloučení slovníku prostředků se dá odkazovat prostřednictvím libovolného platného identifikátoru URI (Uniform Resource Identifier). Přesně to, jak to uděláte, bude záviset na strategii nasazení aplikace a na tom, který model aplikace sledujete. Výše uvedená strategie sady identifikátorů URI poskytuje způsob, jak běžně nastavovat sloučený prostředek napříč více projekty během vývoje sdílením odkazu na sestavení. V tomto scénáři jsou prostředky pořád distribuované klientem a aspoň jedna z aplikací musí nasadit odkazované sestavení. Také je možné odkazovat na sloučené prostředky prostřednictvím distribuovaného identifikátoru URI, který používá protokol HTTP.  
  
 Zápis sloučených slovníků jako místních souborů aplikace nebo do místního sdíleného úložiště je další možný scénář nasazení sloučeného slovníku nebo aplikace.  
  
### <a name="localization"></a>Lokalizace  
 Pokud jsou prostředky, které je nutné lokalizovat, izolované na slovníky, které jsou sloučeny do primárních slovníků, a jsou uchovány jako volné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], lze tyto soubory lokalizovat samostatně. Tato technika je zjednodušenou alternativou pro lokalizaci sestavení satelitních prostředků. Podrobnosti najdete v tématu [Přehled globalizace a lokalizace WPF](wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ResourceDictionary>
- [Prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Prostředky a kód](resources-and-code.md)
- [Prostředek, obsah a datové soubory aplikace WPF](../app-development/wpf-application-resource-content-and-data-files.md)
