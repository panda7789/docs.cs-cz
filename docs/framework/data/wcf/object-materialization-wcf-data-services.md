---
title: Materializace objektů (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: 68b04ac59d1b73d6e66a5a7836ce1bfe30d9c681
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975195"
---
# <a name="object-materialization-wcf-data-services"></a>Materializace objektů (WCF Data Services)

Při použití dialogového okna **Přidat odkaz na službu** ke využívání informačního kanálu protokolu OData (Open Data Protocol) v klientské aplikaci založené na .NET Framework se pro každý typ entity v datovém modelu, který je vystavený informačním kanálem, vygenerují ekvivalentní datové třídy. Další informace najdete v tématu [generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md). Data entity, která jsou vrácena dotazem, jsou vyhodnocena jako instance jedné z těchto generovaných tříd služby data a klienta. Informace o možnostech sloučení a rozlišení identity pro sledované objekty najdete v tématu [Správa kontextu datové služby](managing-the-data-service-context-wcf-data-services.md).

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] také umožňuje definovat vlastní třídy klientské datové služby místo použití datových tříd generovaných nástrojem. To vám umožňuje používat vlastní datové třídy, označované také jako "obyčejné, staré" objekty CLR (POCO) datové třídy. Při použití těchto typů vlastních datových tříd byste měli mít atribut datové třídy buď <xref:System.Data.Services.Common.DataServiceKeyAttribute>, nebo <xref:System.Data.Services.Common.DataServiceEntityAttribute> a zajistěte, aby názvy typů v klientovi odpovídaly názvům typu v datovém modelu datové služby.

Poté, co Knihovna obdrží zprávu odpovědi na dotaz, materializuje vrácená data z datového kanálu OData do instancí tříd klientských dat služby, které jsou typu dotazu. Obecný proces pro vyhodnocování těchto objektů je následující:

1. Klientská knihovna přečte serializovaný typ z prvku `entry` v kanálu zpráv odpovědi a pokusí se vytvořit novou instanci správného typu, a to jedním z následujících způsobů:

    - Když typ deklarovaný v informačním kanálu má stejný název jako typ <xref:System.Data.Services.Client.DataServiceQuery%601>, vytvoří se nová instance tohoto typu pomocí prázdného konstruktoru.

    - Když typ deklarovaný v informačním kanálu má stejný název jako typ odvozený od typu <xref:System.Data.Services.Client.DataServiceQuery%601>, vytvoří se nová instance tohoto odvozeného typu pomocí prázdného konstruktoru.

    - Pokud typ deklarovaný v informačním kanálu nelze spárovat s typem <xref:System.Data.Services.Client.DataServiceQuery%601> ani žádné odvozené typy, je vytvořena nová instance typu dotazované pomocí prázdného konstruktoru.

    - Pokud je nastavena vlastnost <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A>, je zavolán poskytnutý delegát, který přepíše výchozí mapování typu založeného na názvu a vytvoří novou instanci typu vráceného <xref:System.Func%602> je namísto toho vytvořen. Pokud tento delegát vrátí hodnotu null, je místo toho vytvořena nová instance typu dotazu. Pro podporu scénářů dědičnosti může být nutné přepsat výchozí mapování názvu typu na základě názvu.

2. Klientská knihovna přečte hodnotu identifikátoru URI z prvku `id` `entry`, což je hodnota identity entity. Není-li použita hodnota <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> <xref:System.Data.Services.Client.MergeOption.NoTracking>, je použita hodnota identity ke sledování objektu v <xref:System.Data.Services.Client.DataServiceContext>. Hodnota identity se také používá k zajištění, že se vytvoří jenom jedna instance entity, a to i v případě, že se entita vrátí v odpovědi na dotaz víckrát.

3. Klientská knihovna přečte z položky informačního kanálu vlastnosti a nastaví odpovídající vlastnosti nově vytvořeného objektu. Pokud objekt, který má stejnou hodnotu identity, již v <xref:System.Data.Services.Client.DataServiceContext>dojde, vlastnosti jsou nastaveny na základě <xref:System.Data.Services.Client.MergeOption> nastavení <xref:System.Data.Services.Client.DataServiceContext>. Odpověď může obsahovat hodnoty vlastností, pro které se v typu klienta nevyskytují odpovídající vlastnosti. Pokud k tomu dojde, akce závisí na hodnotě vlastnosti <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> <xref:System.Data.Services.Client.DataServiceContext>. Pokud je tato vlastnost nastavena na `true`, chybějící vlastnost je ignorována. V opačném případě je vyvolána chyba. Vlastnosti se nastaví takto:

    - Skalární vlastnosti jsou nastaveny na odpovídající hodnotu v záznamu zprávy s odpovědí.

    - Komplexní vlastnosti jsou nastaveny na novou instanci komplexního typu, která je nastavena pomocí vlastností komplexního typu z odpovědi.

    - Navigační vlastnosti, které vracejí kolekci souvisejících entit, jsou nastaveny na novou nebo existující instanci <xref:System.Collections.Generic.ICollection%601>, kde `T` je typ související entity. Tato kolekce je prázdná, pokud nebyly do <xref:System.Data.Services.Client.DataServiceContext>načteny související objekty. Další informace najdete v tématu [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md).

      > [!NOTE]
      > Pokud vygenerované klientské datové třídy podporují datovou vazbu, vlastnosti navigace vrátí instance <xref:System.Data.Services.Client.DataServiceCollection%601> třídy místo toho. Další informace najdete v tématu [vázání dat na ovládací prvky](binding-data-to-controls-wcf-data-services.md).

4. Vyvolá se událost <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity>.

5. Klientská knihovna připojí objekt k <xref:System.Data.Services.Client.DataServiceContext>. Objekt není připojen, je-li <xref:System.Data.Services.Client.MergeOption> <xref:System.Data.Services.Client.MergeOption.NoTracking>.

## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
- [Projekce dotazů](query-projections-wcf-data-services.md)
