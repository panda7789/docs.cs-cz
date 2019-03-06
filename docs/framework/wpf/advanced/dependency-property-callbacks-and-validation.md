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
ms.openlocfilehash: ff7cbd995ba52f3cea712cb02b72f91d40422c33
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363927"
---
# <a name="dependency-property-callbacks-and-validation"></a>Zpětné volání a ověření vlastností závislostí
Toto téma popisuje postup vytvoření vlastnosti závislosti pomocí alternativní vlastní implementace pro vlastnost související funkce, jako je ověření stanovení, zpětná volání, které jsou vyvolány při změně vlastnosti platnou hodnotu a přepsáním možné mimo vlivy na stanovení hodnotu. Toto téma také popisuje scénáře, kde jako rozšíření chování výchozí vlastnost systému s použitím těchto postupů je vhodné.  
  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že chápete základní scénáře implementace vlastnosti závislosti a jak je použito metadat pro vlastnost vlastní závislosti. Zobrazit [vlastní vlastnosti závislosti](custom-dependency-properties.md) a [Metadata vlastností závislosti](dependency-property-metadata.md) pro kontext.  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>Zpětná volání ověření  
 Zpětná volání ověření je vlastnost závislosti přiřadit při první registraci. Zpětné volání pro ověření není součástí metadata vlastnosti; je přímý vstup <xref:System.Windows.DependencyProperty.Register%2A> metody. Proto po vytvoření zpětné volání pro ověření pro vlastnost závislosti je nelze přepsat pomocí novou implementaci.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Tak potřebná zpětná volání jsou implementované tak, že jsou k dispozici hodnotu objektu. Vrátí `true` Pokud zadaná hodnota je platná pro vlastnost; v opačném případě vrátí `false`. Předpokládá se, že vlastnost je nesprávného typu na typ zaregistrovaný v systému vlastností, kontrola typu v rámci zpětných dotazů se obvykle provádí. Tak potřebná zpětná volání jsou používány v systému vlastností v řadě různých operací. To zahrnuje počáteční typ inicializace výchozí hodnotou, Programová změna vyvoláním <xref:System.Windows.DependencyObject.SetValue%2A>, nebo před pokusy pro přepis metadat se nová výchozí hodnota k dispozici. Pokud je vyvolán pomocí některé z těchto operací zpětné volání pro ověření a vrátí `false`, pak bude vyvolána výjimka. Autoři aplikace musí být připravena ke zpracování těchto výjimek. Běžně používá zpětná volání ověření ověřování hodnot výčtu, nebo omezení hodnoty celých čísel nebo hodnot datového typu Double, když vlastnost nastaví měření, které musí být nulová nebo větší.  
  
 Zpětná volání ověření speciálně mají být třídy validátorů, není instance validátorů. Parametry zpětného volání konkrétní nekomunikují <xref:System.Windows.DependencyObject> na které jsou nastaveny vlastnosti pro ověření. Proto ověření zpětná volání nejsou užitečné k vynucování možných závislostí"", které by mohly ovlivnit hodnoty vlastnosti, kde je specifické pro instanci hodnotu vlastnosti závisí na faktorech jako jsou specifické pro instanci hodnoty dalších vlastností, nebo běhový stav.  
  
 Tady je ukázkový kód pro zpětné volání scénář velmi jednoduchého ověření: ověření, která vlastnost, která je <xref:System.Double> primitivní není <xref:System.Double.PositiveInfinity> nebo <xref:System.Double.NegativeInfinity>.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Převeďte hodnotu změnit vlastnost a zpětná volání událostí  
 Převeďte hodnotu zpětná volání předat konkrétní <xref:System.Windows.DependencyObject> instance pro vlastnosti, jako tomu <xref:System.Windows.PropertyChangedCallback> implementace, které jsou vyvolány v systému vlastností pokaždé, když se změní hodnota vlastnosti závislosti. Pomocí těchto dvou zpětných volání v kombinaci, můžete vytvořit řadu vlastnosti prvků, kde budou změny v jedné vlastnosti vynutit přehodnocení jiné vlastnosti nebo konverze za.  
  
 Typický scénář pro použití vazby vlastností závislosti je, když máte uživatelské rozhraní řízené vlastnosti kde element obsahuje jednu vlastnost s každou minimální a maximální hodnotou a třetí vlastnost skutečné nebo aktuální hodnotu. Sem pokud maximální byl upraven tak, že aktuální hodnota překročila maximální nové, byste k vynucení aktuální hodnota nesmí překročit nové maximální a podobné vztah minimálně na aktuální.  
  
 Níže je příliš malá ukázkový kód pro některou ze tří závislosti vlastnosti, které ilustrují tento vztah. Příklad ukazuje způsob, jakým `CurrentReading` vlastnost minimální/maximální/aktuální sadu souvisejících * čtení vlastností je zaregistrovaný. Jak je znázorněno v předchozí části používá ověřování.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Změněná vlastnost zpětného volání pro aktuální slouží k předávání změn na další závislé vlastnosti explicitně vyvoláním zpětných volání coerce hodnoty, které jsou registrovány pro tyto vlastnosti:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Zpětné volání hodnotu coerce zkontroluje hodnoty vlastností, potenciálně závisí na aktuální vlastnost a převede aktuální hodnotu v případě potřeby:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
>  Výchozí hodnoty vlastností nejsou převést. Pokud stále obsahuje počáteční výchozí hodnotu vlastnosti, nebo prostřednictvím vymazání jiné hodnoty může dojít k rovna hodnotě výchozí hodnoty vlastnosti <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
 Změnit vlastnost a hodnota coerce zpětná volání jsou součástí vlastností metadat. Proto můžete změnit zpětná volání pro vlastnost závislosti konkrétní jak existuje typ, který je odvozen od typu, který vlastní vlastnosti závislosti tak, že přepíšete metadata pro vlastnosti v typu.  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>Pokročilé vynucení a scénáře zpětného volání  
  
### <a name="constraints-and-desired-values"></a>Omezení a požadované hodnoty  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> Vlastnost systému použije zpětná volání k vynucení hodnotu podle logiky můžete deklarovat, ale která je převedená hodnota místně nastavené vlastnosti zůstanou "požadovanou hodnotu" interně. Pokud omezení jsou založeny na jiné hodnoty vlastností, které může dynamicky měnit během životního cyklu aplikací, vynucení omezení jsou změnit dynamicky také a vlastnost omezené můžete změnit jeho hodnotu chcete získat co nejblíže požadované hodnoty jako nejlépe nová omezení. Hodnota se stanou požadovanou hodnotu, pokud jsou všechna omezení zrušeno. Pokud máte více vlastností, které jsou závislé na sebe navzájem v podobě cyklického můžete potenciálně zavést některé scénáře poměrně složitou závislostí. Například ve scénáři minimální/maximální/aktuální, může rozhodnout pro minimální a maximální být nastavitelná při čekání na uživatele. Pokud ano, můžete potřebovat k vynucení, Maximum je vždy větší než Minimum a naopak. Ale pokud tento převod je aktivní a maximální převede na Minimum, ponechá aktuální unsettable stavu, protože je závislá na obě a je omezen na rozsah mezi hodnotami, které je nula. Potom Pokud jsou upraveny maximální nebo minimální, aktuální bude vypadá to, že "sledovat" jedna z hodnot, protože požadovanou hodnotu aktuální zůstanou uložena a pokouší se kontaktovat na požadovanou hodnotu, jako jsou uvolnit omezení.  
  
 Není nic špatného technicky složitými závislostmi, ale je možné způsobit škody snížený výkon, pokud vyžadují velký počet reevaluations a může být také pro uživatele matoucí pokud jejich přímý vliv na uživatelské rozhraní. Buďte opatrní s změněné vlastnosti a vynucení zpětných volání hodnoty a ujistěte se, že lze považovat jako jednoznačně vynucení Probíhá pokus o a ne "overconstrain".  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Zrušení změny hodnot pomocí CoerceValue  
 Vlastnost systém bude považovat všechny <xref:System.Windows.CoerceValueCallback> , která vrátí hodnotu <xref:System.Windows.DependencyProperty.UnsetValue> jako speciální případ. Tento zvláštní případ znamená, že změna vlastnost, jejímž výsledkem <xref:System.Windows.CoerceValueCallback> volání by měly být zamítnuty vlastnost systému, a v systému vlastností místo toho ohlaste jakékoli předchozí hodnota má vlastnost. Tento mechanismus, může být užitečné zkontrolujte, jestli jsou stále platné pro aktuální stav objektu změny vlastnosti, které byly zahájeny asynchronně a potlačit změny, pokud tomu tak není. Další možností je to možné je můžete selektivně potlačit hodnotu v závislosti na tom, jaká součást vlastnosti je odpovědný za hodnotu ohlašovaný stanovení hodnotu. K tomuto účelu můžete použít <xref:System.Windows.DependencyProperty> předaný zpětnému volání a identifikátor vlastnosti jako vstup pro <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>a následně zpracovat <xref:System.Windows.ValueSource>.  
  
## <a name="see-also"></a>Viz také:
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
