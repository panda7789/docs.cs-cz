---
title: Materializace objektů (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: d45d472a2996c0b501af70a0a2a6d2d669dedb4d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043534"
---
# <a name="object-materialization-wcf-data-services"></a>Materializace objektů (WCF Data Services)

Když použijete dialogové okno **Přidat odkaz na službu** ke využívání [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu v klientské aplikaci založené na .NET Framework, vygenerují se ekvivalentní datové třídy pro každý typ entity v datovém modelu, který je vystavený informačním kanálem. Další informace najdete v tématu [generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Data entity, která jsou vrácena dotazem, jsou vyhodnocena jako instance jedné z těchto generovaných tříd služby data a klienta. Informace o možnostech sloučení a rozlišení identity pro sledované objekty najdete v tématu [Správa kontextu datové služby](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]také umožňuje definovat vlastní třídy služby data klienta namísto použití datových tříd generovaných nástrojem. To vám umožňuje používat vlastní datové třídy, označované také jako "obyčejné, staré" objekty CLR (POCO) datové třídy. Při použití těchto typů vlastních datových tříd byste měli atribut datové třídy použít buď <xref:System.Data.Services.Common.DataServiceKeyAttribute> nebo <xref:System.Data.Services.Common.DataServiceEntityAttribute> , a zajistěte, aby názvy typů u klienta odpovídaly názvům typů v datovém modelu datové služby.

Poté, co Knihovna obdrží zprávu odpovědi na dotaz, materializuje vrácená data z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu do instancí tříd klientské datové služby, které jsou typu dotazu. Obecný proces pro vyhodnocování těchto objektů je následující:

1. Klientská knihovna přečte serializovaný typ z `entry` elementu v kanálu zpráv s odpovědí a pokusí se vytvořit novou instanci správného typu v jednom z následujících způsobů:

    - Pokud typ deklarovaný v informačním kanálu má stejný název jako typ <xref:System.Data.Services.Client.DataServiceQuery%601>, nová instance tohoto typu je vytvořena pomocí prázdného konstruktoru.

    - Pokud typ deklarovaný v informačním kanálu má stejný název jako typ, který je odvozen z typu <xref:System.Data.Services.Client.DataServiceQuery%601>, je vytvořena nová instance tohoto odvozeného typu pomocí prázdného konstruktoru.

    - Pokud typ deklarovaný v informačním kanálu nelze spárovat s typem <xref:System.Data.Services.Client.DataServiceQuery%601> nebo žádné odvozené typy, je vytvořena nová instance typu dotazované pomocí prázdného konstruktoru.

    - Je-li nastavena <xref:System.Func%602> vlastnost,jevolánposkytnutýdelegátpropřepsánívýchozíhomapovánítypuzaloženéhonanázvuamístotohojevytvořenanováinstancetypuvrácenéhofunkcí.<xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> Pokud tento delegát vrátí hodnotu null, je místo toho vytvořena nová instance typu dotazu. Pro podporu scénářů dědičnosti může být nutné přepsat výchozí mapování názvu typu na základě názvu.

2. Klientská knihovna přečte hodnotu identifikátoru URI `id` z prvku `entry`, což je hodnota identity entity. <xref:System.Data.Services.Client.MergeOption.NoTracking> Pokud není použita <xref:System.Data.Services.Client.DataServiceContext>hodnota, použije se hodnota identity ke sledování objektu v. <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> Hodnota identity se také používá k zajištění, že se vytvoří jenom jedna instance entity, a to i v případě, že se entita vrátí v odpovědi na dotaz víckrát.

3. Klientská knihovna přečte z položky informačního kanálu vlastnosti a nastaví odpovídající vlastnosti nově vytvořeného objektu. V případě, že se objekt, který má stejnou hodnotu identity, <xref:System.Data.Services.Client.DataServiceContext>již vyskytuje v rozhraní, jsou vlastnosti nastaveny <xref:System.Data.Services.Client.MergeOption> v závislosti na <xref:System.Data.Services.Client.DataServiceContext>nastavení. Odpověď může obsahovat hodnoty vlastností, pro které se v typu klienta nevyskytují odpovídající vlastnosti. Pokud k tomu dojde, akce závisí na hodnotě <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> vlastnosti. <xref:System.Data.Services.Client.DataServiceContext> Je-li tato vlastnost nastavena `true`na hodnotu, chybějící vlastnost je ignorována. V opačném případě je vyvolána chyba. Vlastnosti se nastaví takto:

    - Skalární vlastnosti jsou nastaveny na odpovídající hodnotu v záznamu zprávy s odpovědí.

    - Komplexní vlastnosti jsou nastaveny na novou instanci komplexního typu, která je nastavena pomocí vlastností komplexního typu z odpovědi.

    - Navigační vlastnosti, které vracejí kolekci souvisejících entit <xref:System.Collections.Generic.ICollection%601>, jsou nastaveny na novou nebo existující instanci, kde `T` je typ související entity. Tato kolekce je prázdná, pokud nebyly do objektu načteny <xref:System.Data.Services.Client.DataServiceContext>související objekty. Další informace najdete v tématu [načítání odloženého obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).

      > [!NOTE]
      > Když generované klientské datové třídy podporují datovou vazbu, vlastnosti navigace vrátí instance <xref:System.Data.Services.Client.DataServiceCollection%601> třídy místo toho. Další informace najdete v tématu [vázání dat na ovládací prvky](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).

4. <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> Událost je vyvolána.

5. Klientská knihovna připojí objekt k <xref:System.Data.Services.Client.DataServiceContext>. Objekt není připojen, pokud <xref:System.Data.Services.Client.MergeOption> je. <xref:System.Data.Services.Client.MergeOption.NoTracking>

## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Projekce dotazů](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)
