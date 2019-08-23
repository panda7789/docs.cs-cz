---
title: Zpětné volání a ověření vlastností závislostí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], validation
- coerce value callbacks [WPF]
- callbacks [WPF], validation
- dependency properties [WPF], callbacks
- validation of dependency properties [WPF]
ms.assetid: 48db5fb2-da7f-49a6-8e81-3540e7b25825
ms.openlocfilehash: 7f00961ba100700c68936cc33facfdc758c77d3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940826"
---
# <a name="dependency-property-callbacks-and-validation"></a>Zpětné volání a ověření vlastností závislostí
Toto téma popisuje, jak vytvořit vlastnosti závislosti pomocí alternativních vlastních implementací pro funkce související s vlastnostmi, jako je například určení ověřování, zpětná volání, která jsou vyvolána při změně efektivní hodnoty vlastnosti a přepsání možné vnější vlivy na určení hodnoty. Toto téma také popisuje scénáře, kdy je vhodné rozšířit chování výchozího systému vlastností systémem pomocí těchto technik.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že rozumíte základním scénářům implementace vlastnosti závislosti a způsobu, jakým se aplikují metadata na vlastní vlastnost závislosti. Podívejte se na téma [vlastnosti vlastní závislosti](custom-dependency-properties.md) a [metadata vlastnosti závislosti](dependency-property-metadata.md) pro kontext.  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>Zpětná volání ověření  
 Zpětná volání ověřování lze přiřadit vlastnosti závislosti při prvním registraci. Zpětné volání ověřování není součástí metadat vlastností; Jedná se o přímý vstup <xref:System.Windows.DependencyProperty.Register%2A> metody. Proto Jakmile je pro vlastnost závislosti vytvořeno zpětné volání ověřování, nelze ji přepsat novou implementací.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Zpětná volání jsou implementována tak, aby byla poskytnuta hodnota objektu. Vrátí `true` , pokud je zadaná hodnota pro vlastnost platná. v opačném případě vrátí `false`. Předpokládá se, že vlastnost je správného typu na typ zaregistrovaný v systému vlastností, takže typ kontroly v rámci zpětných volání není obvykle proveden. Zpětná volání jsou používána systémem vlastností v nejrůznějších různých operacích. To zahrnuje inicializaci počátečního typu podle výchozí hodnoty, programového změny vyvoláním <xref:System.Windows.DependencyObject.SetValue%2A>nebo pokusů o přepsání metadat s poskytnutou novou výchozí hodnotou. Pokud je zpětné volání ověřování vyvoláno kteroukoli z těchto operací a vrátí `false`, bude vyvolána výjimka. Aby bylo možné tyto výjimky zpracovat, musí být moduly pro zápis aplikací připravené. Běžné použití zpětných volání ověřování ověřuje hodnoty výčtu nebo omezuje hodnoty celých čísel nebo dvojitých hodnot, pokud vlastnost nastavuje měření, která musí být nulová nebo větší.  
  
 Zpětná volání ověřování jsou určena speciálně pro validátory tříd, nikoli pro validátory instancí. Parametry zpětného volání nekomunikují specificky <xref:System.Windows.DependencyObject> , na kterých jsou nastaveny vlastnosti k ověření. Zpětná volání ověřování nejsou proto užitečná pro vynucování možných "závislostí", které by mohly ovlivnit hodnotu vlastnosti, kde je hodnota vlastnosti specifická pro konkrétní instance závislá na faktorech, jako jsou například hodnoty specifické pro instance jiných vlastností nebo Běhový stav.  
  
 Následuje příklad kódu pro velmi jednoduché ověřování typu zpětného volání: ověřování, že vlastnost, která je zadána jako <xref:System.Double> primitivní <xref:System.Double.PositiveInfinity> , není nebo <xref:System.Double.NegativeInfinity>.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Převede zpětná volání hodnot a události změněné vlastností.  
 Zpětná volání převodních hodnot předají <xref:System.Windows.DependencyObject> konkrétní instanci pro vlastnosti, <xref:System.Windows.PropertyChangedCallback> stejně jako implementace, které jsou vyvolány systémem vlastností při změně hodnoty vlastnosti závislosti. Pomocí těchto dvou zpětných volání v kombinaci můžete vytvořit řadu vlastností pro prvky, kde změny v jedné vlastnosti vynutí vynucení nebo opětovné vyhodnocení jiné vlastnosti.  
  
 Typický scénář pro použití propojení vlastností závislosti je v případě, že máte vlastnost založenou na uživatelském rozhraní, kde element obsahuje jednu vlastnost pro minimální a maximální hodnotu a třetí vlastnost pro skutečnou nebo aktuální hodnotu. Pokud je toto maximum upraveno takovým způsobem, že aktuální hodnota překročila nové maximum, měla by být aktuální hodnota převedena na hodnotu vyšší než nové maximum a podobný vztah pro minimum na hodnotu Current.  
  
 Následuje stručný ukázkový kód pouze pro jednu ze tří vlastností závislosti, které ilustrují tento vztah. Příklad ukazuje, jak `CurrentReading` je zaregistrována vlastnost minimální/maximální/aktuální sady souvisejících vlastností pro čtení. Používá ověření, jak je znázorněno v předchozí části.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Vlastnost, která se změnila zpět pro aktuální, slouží k přeposílání změn na jiné závislé vlastnosti tím, že explicitně vyvolá zpětná volání přenesených hodnot, která jsou registrována pro tyto ostatní vlastnosti:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Zpětné volání s převedenou hodnotou kontroluje hodnoty vlastností, na kterých je aktuální vlastnost potenciálně závislá, a v případě potřeby Převede aktuální hodnotu:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
> Výchozí hodnoty vlastností nejsou přiřazeny. Hodnota vlastnosti, která se rovná výchozí hodnotě, může nastat, pokud hodnota vlastnosti stále má počáteční výchozí hodnotu, nebo pomocí mazání jiných hodnot <xref:System.Windows.DependencyObject.ClearValue%2A>pomocí.  
  
 Zpětná volání přeměněných hodnot a vlastností jsou součástí metadat vlastností. Proto můžete změnit zpětná volání pro konkrétní vlastnost závislosti, protože existuje u typu, který je odvozen z typu, který vlastní vlastnost závislosti, přepsáním metadat pro tuto vlastnost typu.  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>Pokročilé scénáře vynucení a zpětného volání  
  
### <a name="constraints-and-desired-values"></a>Omezení a požadované hodnoty  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> Zpětná volání budou použita systémem vlastností k přenesení hodnoty v souladu s logikou, kterou deklarujete, ale převedená hodnota vlastnosti lokálně uchová stále "požadovanou hodnotu" interně. Pokud jsou omezení založena na dalších hodnotách vlastností, které se mohou dynamicky měnit během životního cyklu aplikace, jsou omezení vynuceně měněna dynamicky a omezená vlastnost může změnit její hodnotu tak, aby se co nejblíže požadované hodnotě. je možné vydávat nová omezení. Hodnota se změní na požadovanou hodnotu, pokud jsou všechna omezení vyvolána. V případě, že máte více vlastností, které jsou na sobě vzájemně závislé, můžete začlenit některé poměrně složité scénáře závislosti. Například ve scénáři min/max/current se můžete rozhodnout, že nastavit uživatele jako minimální a maximální hodnotu. Pokud ano, může být nutné, aby toto maximum bylo vždy větší než minimum a naopak. Pokud je však tato konverze aktivní a maximum se převede na minimum, zůstane aktuální v nastavitelných stavech, protože je závislý na obou a je omezený na rozsah mezi hodnotami, což je nula. Když se pak hodnota maximum nebo minimum upraví, zobrazí se u položky "sledovat" jednu z hodnot, protože požadovaná hodnota Current je stále uložená a pokouší se dosáhnout požadované hodnoty, protože jsou omezení vydaná.  
  
 Nedošlo k žádné technické chybě se složitými závislostmi, ale může se jednat o mírné zvýšení výkonu, pokud vyžadují velký počet přehodnocení a může být také matoucí pro uživatele, pokud mají vliv na uživatelské rozhraní přímo. Buďte opatrní se změnou vlastnosti a převedli zpětná volání hodnot a zajistěte, aby se převedená konverze mohla považovat za nejednoznačnou možnou hodnotu a nepředstavuje "omezení".  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Zrušení změn hodnot pomocí CoerceValue  
 Systém vlastností zpracuje všechny <xref:System.Windows.CoerceValueCallback> , které vrací hodnotu <xref:System.Windows.DependencyProperty.UnsetValue> jako zvláštní případ. Tento zvláštní případ znamená, že změna vlastnosti, která je výsledkem <xref:System.Windows.CoerceValueCallback> volání metody, by měla být zamítnutá systémem vlastností a že by měl systém vlastností místo toho hlásit jakoukoli předchozí hodnotu, kterou vlastnost měla. Tento mechanismus může být užitečný pro kontrolu, že změny vlastnosti, které byly iniciovány asynchronně, jsou pro aktuální stav objektu stále platné, a změny se potlačí, pokud ne. Dalším možným scénářem je, že můžete selektivně potlačit hodnotu v závislosti na tom, která součást určení hodnot vlastností zodpovídá za nahlášenou hodnotu. Chcete-li to provést, můžete použít <xref:System.Windows.DependencyProperty> předaný příkaz ke zpětnému volání a identifikátor vlastnosti jako <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>vstup pro a poté zpracovat <xref:System.Windows.ValueSource>.  
  
## <a name="see-also"></a>Viz také:

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
