---
title: Slovníky sloučených prostředků
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 466a18a58acfebf6d779a1d0eba3d2637743806e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911728"
---
# <a name="merged-resource-dictionaries"></a>Slovníky sloučených prostředků
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]prostředky podporují funkci sloučeného slovníku prostředků. Tato funkce poskytuje způsob, jak definovat část [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prostředků v aplikaci mimo kompilovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikace. Prostředky je pak možné sdílet mezi aplikacemi a jsou taky pohodlnější izolované pro lokalizaci.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Představení sloučeného slovníku prostředků  
 V kódu použijte následující syntaxi k představení sloučeného slovníku prostředků na stránku:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Všimněte si, <xref:System.Windows.ResourceDictionary> že element nemá direktivu [x:Key –](../../xaml-services/x-key-directive.md), která je obecně nutná pro všechny položky v kolekci prostředků. Ale další <xref:System.Windows.ResourceDictionary> odkaz <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> v rámci kolekce je zvláštní případ vyhrazený pro tento scénář sloučeného slovníku prostředků. Modul <xref:System.Windows.ResourceDictionary> , který zavádí sloučený slovník prostředků, nemůže mít [direktivu x:Key –](../../xaml-services/x-key-directive.md). Obvykle každý <xref:System.Windows.ResourceDictionary> <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> v rámci kolekce Určuje <xref:System.Windows.ResourceDictionary.Source%2A> atribut. Hodnota <xref:System.Windows.ResourceDictionary.Source%2A> by měla [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] být, která se překládá na umístění souboru prostředků, který se má sloučit. Cíl, který [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] musí být jiný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor, s <xref:System.Windows.ResourceDictionary> jako jeho kořenovým elementem.  
  
> [!NOTE]
> Je možné definovat prostředky v rámci <xref:System.Windows.ResourceDictionary> , které jsou zadány jako sloučený slovník, a to buď jako alternativu k určení <xref:System.Windows.ResourceDictionary.Source%2A>, nebo kromě jakýchkoli prostředků, které jsou zahrnuty ze zadaného zdroje. Nejedná se však o běžný scénář. hlavním scénářem pro sloučené slovníky je sloučení prostředků z umístění externích souborů. Chcete-li určit prostředky v rámci značky stránky, je obvykle třeba je definovat v Main <xref:System.Windows.ResourceDictionary> a nikoli ve sloučených slovnících.  
  
## <a name="merged-dictionary-behavior"></a>Chování sloučeného slovníku  
 Prostředky ve sloučeném slovníku zabírají umístění v oboru vyhledávání prostředků, které je bezprostředně po rozsahu hlavního slovníku prostředků, do kterého jsou sloučeny. I když klíč prostředku musí být jedinečný v rámci každého jednotlivého slovníku, klíč může existovat několikrát v sadě sloučených slovníků. V takovém případě bude vrácený prostředek z posledního slovníku nalezeného v <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekci postupně. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Pokud byla <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekce definována v, pak pořadí sloučených slovníků v kolekci je pořadí prvků, jak je uvedeno v označení. Pokud je klíč definovaný v primárním slovníku a také ve slovníku, který byl sloučený, povede vrácený prostředek z primárního slovníku. Tato pravidla oboru platí stejně pro statické odkazy na prostředky i pro dynamické odkazy na prostředky.  
  
### <a name="merged-dictionaries-and-code"></a>Sloučené slovníky a kód  
 Sloučené slovníky lze do `Resources` slovníku přidat prostřednictvím kódu. Výchozí hodnota, která je <xref:System.Windows.ResourceDictionary> zpočátku prázdná pro libovolnou `Resources` vlastnost, má také výchozí vlastnost, která <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> je zpočátku prázdná. Chcete-li přidat sloučený slovník prostřednictvím kódu <xref:System.Windows.ResourceDictionary>, získáte odkaz na požadovaný primární objekt, získejte jeho <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> hodnotu vlastnosti a zavolejte `Add` na obecný `Collection` , který je obsažen v <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Objekt, který přidáte, musí být nový <xref:System.Windows.ResourceDictionary>. V kódu není nastavena <xref:System.Windows.ResourceDictionary.Source%2A> vlastnost. Místo toho je nutné získat <xref:System.Windows.ResourceDictionary> objekt buď vytvořením jednoho nebo načtením. Jedním ze způsobů, jak načíst <xref:System.Windows.ResourceDictionary> existující volání <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> na existující [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] datový proud souboru <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> , který má <xref:System.Windows.ResourceDictionary> kořen, pak přetypování návratové hodnoty <xref:System.Windows.ResourceDictionary>do.  
  
### <a name="merged-resource-dictionary-uris"></a>Identifikátory URI sloučeného slovníku prostředků  
 Existuje několik postupů, jak zahrnout sloučený slovník prostředků, který je určen [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] formátem, který budete používat. V podstatě řečeno, tyto techniky lze rozdělit do dvou kategorií: prostředky, které jsou kompilovány jako součást projektu, a prostředky, které nejsou kompilovány jako součást projektu.  
  
 Pro prostředky, které jsou kompilovány jako součást projektu, můžete použít relativní cestu, která odkazuje na umístění prostředku. Relativní cesta je vyhodnocena během kompilace. Váš prostředek musí být definován jako součást projektu jako akce sestavení prostředku. Pokud zahrnete soubor Resource. XAML do projektu jako prostředek, nemusíte kopírovat soubor prostředků do výstupního adresáře, prostředek je již obsažen v kompilované aplikaci. Můžete také použít akci sestavení obsahu, ale je nutné zkopírovat soubory do výstupního adresáře a také nasadit soubory prostředků ve stejném vztahu cesty ke spustitelnému souboru.  
  
> [!NOTE]
> Nepoužívejte akci sestavení vloženého prostředku. Vlastní akce sestavení je pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace podporována, ale <xref:System.Windows.ResourceDictionary.Source%2A> řešení <xref:System.Resources.ResourceManager>nezahrnuje, a proto nemůže oddělit jednotlivé prostředky z datového proudu. Vložený prostředek můžete i nadále používat pro jiné účely, pokud jste také použili <xref:System.Resources.ResourceManager> pro přístup k prostředkům.  
  
 Související technikou je použít k [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru identifikátor URI balíku a odkazovat na něj jako na zdroj. Identifikátor URI balíčku umožňuje odkazy na komponenty odkazovaných sestavení a další techniky. Další informace o identifikátorech URI balíčku naleznete v tématu [prostředky aplikace WPF, obsah a datové soubory](../app-development/wpf-application-resource-content-and-data-files.md).  
  
 U prostředků, které nejsou kompilovány jako součást projektu, je identifikátor URI vyhodnocen za běhu. Pro odkazování na soubor prostředků můžete použít společný přenos URI, jako je soubor: nebo http:. Nevýhodou použití nezkompilovaného přístupu k prostředkům je tento soubor: přístup vyžaduje další kroky nasazení a http: předpokládá se, že přístup vychází z zóny zabezpečení Internetu.  
  
### <a name="reusing-merged-dictionaries"></a>Znovu použít sloučené slovníky  
 Sloučené slovníky prostředků mezi aplikacemi můžete opakovaně používat nebo sdílet, protože slovník prostředků, který se má sloučit, může být [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]odkazován pomocí všech platných. Přesně to, jak to uděláte, bude záviset na strategii nasazení aplikace a na tom, který model aplikace sledujete. Výše uvedená strategie sady identifikátorů URI poskytuje způsob, jak běžně nastavovat sloučený prostředek napříč více projekty během vývoje sdílením odkazu na sestavení. V tomto scénáři jsou prostředky pořád distribuované klientem a aspoň jedna z aplikací musí nasadit odkazované sestavení. Také je možné odkazovat na sloučené prostředky prostřednictvím distribuovaného identifikátoru URI, který používá protokol HTTP.  
  
 Zápis sloučených slovníků jako místních souborů aplikace nebo do místního sdíleného úložiště je další možný scénář nasazení sloučeného slovníku nebo aplikace.  
  
### <a name="localization"></a>Lokalizace  
 Pokud jsou prostředky, které je nutné lokalizovat, izolované na slovníky, které jsou sloučeny do primárních slovníků a jsou uchovány jako volné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], lze tyto soubory lokalizovat samostatně. Tato technika je zjednodušenou alternativou pro lokalizaci sestavení satelitních prostředků. Podrobnosti najdete v tématu [Přehled globalizace a lokalizace WPF](wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ResourceDictionary>
- [Prostředky XAML](xaml-resources.md)
- [Prostředky a kód](resources-and-code.md)
- [Prostředek, obsah a datové soubory aplikace WPF](../app-development/wpf-application-resource-content-and-data-files.md)
