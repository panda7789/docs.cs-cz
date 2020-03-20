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
ms.openlocfilehash: c5f7439753037aeb5c2ff558da63e063ad65a5e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186428"
---
# <a name="dependency-property-callbacks-and-validation"></a>Zpětné volání a ověření vlastností závislostí
Toto téma popisuje, jak vytvořit vlastnosti závislostí pomocí alternativních vlastních implementací pro funkce související s vlastnostmi, jako je například určení ověření, zpětná volání, která jsou vyvolána při každé změně efektivní hodnoty vlastnosti, a přepsání možné vnější vlivy na stanovení hodnoty. Toto téma také popisuje scénáře, kde je vhodné rozšířit chování výchozího systému vlastností pomocí těchto technik.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte základním scénářům implementace vlastnosti závislosti a způsobu použití metadat na vlastní vlastnost závislosti. Viz [Vlastní vlastnosti závislostí](custom-dependency-properties.md) a [metadata vlastností závislostí](dependency-property-metadata.md) pro kontext.  
  
<a name="Validation_Callbacks"></a>
## <a name="validation-callbacks"></a>Ověřovací zpětná volání  
 Ověření zpětná volání lze přiřadit k vlastnosti závislosti při první registraci. Zpětné volání ověření není součástí metadat vlastnosti; jedná se o přímý <xref:System.Windows.DependencyProperty.Register%2A> vstup metody. Proto po vytvoření zpětného volání ověření pro vlastnost závislosti, nemůže být přepsána novou implementací.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Zpětná volání jsou implementována tak, aby jim byla poskytnuta hodnota objektu. Vrátí `true` se, pokud je zadaný hodnota platná pro vlastnost; v opačném `false`případě se vrátí . Předpokládá se, že vlastnost je správného typu podle typu registrovaného v systému vlastností, takže kontrola typu v rámci zpětná volání se obvykle neprovádí. Zpětná volání jsou používány systémem vlastností v různých operacích. To zahrnuje počáteční inicializaci typu výchozí hodnotou, <xref:System.Windows.DependencyObject.SetValue%2A>programovou změnu vyvoláním nebo pokusy o přepsání metadat s novou výchozí hodnotou. Pokud je zpětné volání ověření vyvoláno některou `false`z těchto operací a vrátí , bude vyvolána výjimka. Autoři aplikací musí být připraveni ke zpracování těchto výjimek. Běžné použití ověření zpětná volání je ověření výčtu hodnoty nebo omezení hodnoty celá čísla nebo zdvojnásobí při vlastnost nastaví měření, která musí být nula nebo větší.  
  
 Validace zpětná volání konkrétně jsou určeny k třídy validátory, nikoli instance validátory. Parametry zpětného volání nesdělují konkrétní, <xref:System.Windows.DependencyObject> na kterých jsou nastaveny vlastnosti k ověření. Proto zpětná volání ověření nejsou užitečné pro vynucení možné "závislosti", které by mohly ovlivnit hodnotu vlastnosti, kde je hodnota specifické pro instanci vlastnosti závislá na faktorech, jako jsou hodnoty specifické pro instanci jiných vlastností, nebo stavu za běhu.  
  
 Následuje příklad kódu pro velmi jednoduchý scénář ověření zpětného volání: ověření, <xref:System.Double> že vlastnost, která je zadána jako primitivní není <xref:System.Double.PositiveInfinity> nebo <xref:System.Double.NegativeInfinity>.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Události změny hodnoty coerce a události změněné vlastnosti  
 Zpětná volání hodnoty coerce <xref:System.Windows.DependencyObject> předávají konkrétní instanci pro vlastnosti, stejně <xref:System.Windows.PropertyChangedCallback> jako implementace, které jsou vyvolány systémem vlastností při každé změně hodnoty vlastnosti závislosti. Pomocí těchto dvou zpětná volání v kombinaci můžete vytvořit řadu vlastností na prvky, kde změny v jedné vlastnosti vynutí nátlaku nebo přecenění jiné vlastnosti.  
  
 Typický scénář pro použití propojení vlastností závislostí je, když máte vlastnost řízenou uživatelským rozhraním, kde prvek obsahuje jednu vlastnost pro minimální a maximální hodnotu a třetí vlastnost pro skutečnou nebo aktuální hodnotu. Pokud bylo maximum upraveno tak, že aktuální hodnota překročila nové maximum, bylo by nutné donutit aktuální hodnotu, aby nebyla větší než nové maximum a podobný vztah pro minimální až aktuální.  
  
 Následuje velmi stručný příklad kódu pouze pro jednu ze tří vlastností závislostí, které ilustrují tento vztah. Příklad ukazuje, `CurrentReading` jak je registrována vlastnost min/max/aktuální sadu související *čtení vlastností. Používá ověření, jak je znázorněno v předchozí části.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Vlastnost změněna zpětné volání pro Current se používá k předání změny na jiné závislé vlastnosti, explicitní vyvolání příkazu hodnota zpětná volání, které jsou registrovány pro tyto další vlastnosti:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Zpětné volání hodnoty couvat kontroluje hodnoty vlastností, na kterých je aktuální vlastnost potenciálně závislá, a v případě potřeby vylomií aktuální hodnotu:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
> Výchozí hodnoty vlastností nejsou vykonavovány. Hodnota vlastnosti rovnající se výchozí hodnotě může nastat, pokud hodnota vlastnosti stále má své původní výchozí hodnoty, nebo vymazáním jiných hodnot pomocí <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
 Hodnota coerce a zpětná volání změněné vlastnosti jsou součástí metadat vlastnosti. Proto můžete změnit zpětná volání pro konkrétní vlastnost závislosti, protože existuje na typu, který je odvozen z typu, který vlastní vlastnost závislosti, přepsáním metadat pro tuto vlastnost na vašem typu.  
  
<a name="Advanced"></a>
## <a name="advanced-coercion-and-callback-scenarios"></a>Pokročilé scénáře nátlaku a zpětného volání  
  
### <a name="constraints-and-desired-values"></a>Omezení a požadované hodnoty  
 Zpětná <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> volání budou použita systémem vlastností k dosazení hodnoty v souladu s logikou, kterou deklarujete, ale vykonaná hodnota místně nastavené vlastnosti si zachová "požadovanou hodnotu" interně. Pokud jsou omezení založena na jiných hodnotách vlastností, které se mohou během doby trvání aplikace dynamicky měnit, budou omezení nátlaku dynamicky také změněna a omezující vlastnost může změnit svou hodnotu tak, aby se přiblížila požadované hodnotě jako s ohledem na nová omezení. Hodnota se stane požadovanou hodnotou, pokud jsou zrušena všechna omezení. Můžete potenciálně zavést některé poměrně složité scénáře závislostí, pokud máte více vlastností, které jsou závislé na sobě navzájem cyklickým způsobem. Například v min/max/aktuální scénář můžete zvolit minimální a maximální být uživatel nastavitelný. Pokud ano, možná budete muset dotálet, že maximum je vždy větší než minimum a naopak. Ale pokud je aktivní, a Maximální nátlaku na minimum, opustí Current v unsettable stavu, protože je závislá na obou a je omezena na rozsah mezi hodnotami, což je nula. Potom, pokud maximální nebo minimální jsou upraveny, Current se zdá, že "následovat" jednu z hodnot, protože požadovaná hodnota Current je stále uložena a pokouší se dosáhnout požadované hodnoty jako omezení jsou uvolněny.  
  
 Není nic technicky špatného s komplexní závislosti, ale mohou být mírné poškození výkonu, pokud vyžadují velký počet přehodnocení a může být také matoucí pro uživatele, pokud ovlivňují uživatelské prostředí přímo. Buďte opatrní se změnou vlastnosti a ve snaze o zpětná volání hodnoty a ujistěte se, že pokus o nátlak může být považován za jednoznačně, jak je to možné, a není "přetížení".  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Použití funkce CoerceValue ke zrušení změn hodnoty  
 Systém vlastností bude <xref:System.Windows.CoerceValueCallback> považovat všechny, které vrátí hodnotu <xref:System.Windows.DependencyProperty.UnsetValue> jako zvláštní případ. Tento zvláštní případ znamená, že změna <xref:System.Windows.CoerceValueCallback> vlastnosti, která vyústila v volání by měla být odmítnuta systémem vlastností a že systém vlastností by měl místo toho hlásit jakoukoli předchozí hodnotu vlastnosti. Tento mechanismus může být užitečné zkontrolovat, že změny vlastnosti, které byly zahájeny asynchronně jsou stále platné pro aktuální stav objektu a potlačit změny, pokud tomu tak není. Dalším možným scénářem je, že můžete selektivně potlačit hodnotu v závislosti na tom, která složka stanovení hodnoty vlastnosti je zodpovědná za vykazovanou hodnotu. Chcete-li to provést, <xref:System.Windows.DependencyProperty> můžete použít předané v zpětnévolání <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>a identifikátor <xref:System.Windows.ValueSource>vlastnosti jako vstup pro , a potom zpracovat .  
  
## <a name="see-also"></a>Viz také

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
