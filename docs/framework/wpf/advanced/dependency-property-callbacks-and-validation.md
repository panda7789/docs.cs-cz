---
title: "Zpětné volání a ověření vlastností závislostí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d1b62c7f49653627c626bce2583b2799df931dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dependency-property-callbacks-and-validation"></a>Zpětné volání a ověření vlastností závislostí
Toto téma popisuje postup vytvoření vlastností závislostí pomocí alternativní vlastních implementací vlastnosti související s funkcí, jako jsou ověřování rozhodnutí, zpětná volání, které jsou spuštěny po změně platnou hodnotu vlastnosti a přepsáním Chcete-li to možné mimo vlivy na hodnotu rozhodnutí. Toto téma taky popisuje scénáře, kde rozšíření na výchozí chování systému vlastnost s použitím těchto postupů je vhodné.  
  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že chápete základní scénáře implementace vlastnost závislosti a jak je použito metadata pro vlastnost vlastní závislosti. V tématu [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) a [metadat vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) pro kontext.  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>Zpětná volání ověření  
 Zpětná volání ověření lze přiřadit k vlastnosti závislosti při první registraci. Zpětné volání pro ověření není součástí metadata vlastnosti; je přímý vstup z <xref:System.Windows.DependencyProperty.Register%2A> metoda. Proto po vytvoření zpětné volání pro ověření pro vlastnost závislosti ho nebude možné přepsat novou implementací.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Zpětná volání se implementují tak, že jsou k dispozici hodnota objektu. Vracejí `true` Pokud zadaná hodnota je platná pro vlastnost; v opačném případě, že budou vracet `false`. Předpokládá se, že vlastnost není správného typu pro typ zaregistrována vlastnosti systému, aby kontrola typu v rámci zpětná volání není provedena normálně. Vlastnost systému v řadě různých operací používají zpětných volání. To zahrnuje počáteční typ inicializace výchozí hodnotou, Programová změna vyvoláním <xref:System.Windows.DependencyObject.SetValue%2A>, nebo se pokusí o přepsání metadat poskytuje novou výchozí hodnotou. Pokud je některý z těchto operací vyvolané zpětné volání pro ověření a vrátí `false`, pak bude vyvolána výjimka. Autoři aplikace musí být připravené zpracování těchto výjimek. Běžně se používají zpětná volání ověření ověřování hodnot výčtu, nebo omezíte hodnoty celá čísla nebo hodnoty Double, když vlastnost nastaví měření, které musí být nula nebo větší.  
  
 Zpětná volání ověření speciálně by měla být validátory třída, není instance validátorů. Parametry zpětného volání nekomunikují konkrétní <xref:System.Windows.DependencyObject> na které jsou nastaveny vlastnosti k ověření. Proto zpětná volání ověření nejsou vhodné pro vynucování možné "závislosti", které by mohly ovlivnit hodnotu vlastnosti specifické pro instanci hodnota vlastnosti, kde jsou závislé na faktorech jako jsou specifické pro instanci hodnotách jiných vlastností, nebo stav běhu.  
  
 Tady je ukázkový kód pro scénář zpětného volání velmi jednoduché ověřování: ověřování, která vlastnost, která je zadán jako <xref:System.Double> primitivní není <xref:System.Double.PositiveInfinity> nebo <xref:System.Double.NegativeInfinity>.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Coerce – hodnota zpětná volání a vlastnost změnit události  
 Coerce – hodnota zpětná volání předat konkrétní <xref:System.Windows.DependencyObject> instance pro vlastnosti, stejně jako <xref:System.Windows.PropertyChangedCallback> implementací, které jsou vyvolány vlastnost systému při každé změně hodnoty vlastnosti závislosti. Pomocí těchto dvou zpětná volání v kombinaci, můžete vytvořit řadu vlastnosti u elementů, kde budou změny v jednu vlastnost vynutit převod nebo přehodnocení jinou vlastnost.  
  
 Typický scénář použití propojení vlastností závislostí je v případě, kde element obsahuje jednu vlastnost každý minimální a maximální hodnoty vlastnost rozhraní řízené uživatele a třetí vlastnost, pro skutečné nebo aktuální hodnotu. Sem pokud maximální byla upravena tak, že aktuální hodnota překročila maximální nové, by chcete coerce aktuální hodnota, která má být větší než nové maximální a podobné vztah pro minimální na aktuální.  
  
 Zde je velmi krátké ukázkový kód pro právě jeden z vlastností tři závislostí, které ilustrují tento vztah. Příklad ukazuje jak `CurrentReading` vlastnost minimální/maximální/aktuální sadu související * čtení vlastnosti je zaregistrován. Ověření používá jak je uvedeno v předchozí části.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Zpětné volání změněné vlastnosti pro aktuální slouží k předávání změnu a další závislé vlastnosti explicitně vyvoláním hodnota coerce zpětná volání, které jsou registrovány těchto vlastností:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Zpětné volání hodnotu coerce zkontroluje hodnoty vlastností, aby potenciálně závisí na aktuální vlastnost a převede aktuální hodnota v případě potřeby:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
>  Nejsou má výchozí hodnoty vlastností. Hodnotu vlastnosti, která je stejná jako výchozí hodnota může dojít, pokud stále svou počáteční výchozí hodnotu vlastnosti, nebo prostřednictvím vymazání dalších hodnot s <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
 Změnit hodnotu coerce a vlastnost zpětná volání jsou součástí metadat vlastností. Proto můžete změnit zpětných volání pro vlastnost konkrétní závislosti uložených na typ, který je odvozen z typu, který vlastní vlastnost závislosti přepsáním metadata pro tuto vlastnost na typ vašeho.  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>Scénáře zpětného volání a pokročilé převod  
  
### <a name="constraints-and-desired-values"></a>Omezení a požadované hodnoty  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> Zpětná volání se použije v systému vlastnost k coerce hodnotu v souladu logiku je deklarovat, ale coerced hodnotu místně nastavte vlastnost stále zachovají "požadovanou hodnotu" interně. Jsou-li u dalších hodnot vlastností, které mohou změnit dynamicky během životního cyklu aplikace omezení, omezení převod se změní dynamicky také, a vlastnost omezené můžete změnit její hodnota získat co nejblíže požadovanou hodnotu jako nejlépe nové omezení. Hodnota se stane požadovanou hodnotu, pokud jsou všechna omezení zrušeno. Pokud máte více vlastností, které jsou na sobě závislé cyklické způsobem lze potenciálně zavádět některé scénáře poměrně složitá závislostí. Ve scénáři, Min nebo Max nebo aktuální, například může rozhodnout pro minimální a maximální možné nastavit uživatele. Pokud ano, možná budete muset coerce, že maximální počet je vždy větší a než minimální a naopak. Ale pokud tento převod je aktivní, a maximální převede na minimální, jeho aktuální ponechá v unsettable stavu, protože závisí na obou a je omezená na rozsahu od hodnoty, které je nulová. Poté pokud jsou upraveny maximální nebo minimální, aktuální zobrazí jako "následovat" jednu z hodnot, protože požadovanou hodnotu aktuální je pořád uložená a pokouší se kontaktovat požadovanou hodnotu, jako jsou snížit omezení.  
  
 Není co technicky problém se složitým závislostem, ale mohou být výkon mírnou úkor vyžadovat velké množství reevaluations, když a může být také pro uživatele matoucí Pokud přímo ovlivňují uživatelského rozhraní. Buďte opatrní se změněné vlastnosti a coerce zpětná volání hodnotu a ujistěte se, že lze zacházet jako jednoznačně převod probíhají pokusy o navázání a není "overconstrain".  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Pomocí CoerceValue zrušit změny hodnot  
 Vlastnost systém bude považovat všechny <xref:System.Windows.CoerceValueCallback> , vrátí hodnotu <xref:System.Windows.DependencyProperty.UnsetValue> zvláštním způsobem. Tento zvláštní případ znamená, že změnu vlastnosti, jejichž výsledkem <xref:System.Windows.CoerceValueCallback> volané odmítl vlastnosti systému, a vlastnost systému měli místo toho sestavy jakékoli předchozí hodnotu vlastnosti měl. Tento mechanismus může být vhodné, zkontrolujte, jestli jsou stále platné pro aktuální stav objektu změny vlastnosti, které byly zahájeny asynchronně a není-li potlačit změny. Další možný způsob je můžete selektivně potlačit hodnotu podle toho, která komponenta vlastnosti je zodpovědná za hodnotu nehlásí hodnota rozhodnutí. K tomuto účelu můžete použít <xref:System.Windows.DependencyProperty> předaná zpětného volání a identifikátor vlastnosti jako vstup pro <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>a pak zpracování <xref:System.Windows.ValueSource>.  
  
## <a name="see-also"></a>Viz také  
 [Přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Metadata vlastnosti závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Vlastnosti vlastní závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
