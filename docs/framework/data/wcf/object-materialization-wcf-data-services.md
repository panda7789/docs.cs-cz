---
title: Materializace objektů (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: f4789b3bfd5f9810a9abc870518add9b4a0a045b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645536"
---
# <a name="object-materialization-wcf-data-services"></a>Materializace objektů (WCF Data Services)
Při použití **přidat odkaz na službu** dialogové okno k využívání [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu v aplikaci klienta na základě rozhraní .NET Framework, ekvivalentní datové třídy jsou generovány pro každý typ entity v datovém modelu, který je zveřejněn prostřednictvím informačního kanálu. Další informace najdete v tématu [generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Entity dat vrácených dotazem je vyhodnocena na instanci jednoho z těchto tříd generované klientské datové služby. Informace o možnosti sloučení a řešení identity u sledovaných objektů najdete v tématu [Správa kontextu datové služby](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] také vám umožní definovat vlastní tříd klientské datové služby spíše než použití tříd nástroj generovaná data. To vám umožní použít vaše vlastní třídy dat, označované také jako "prostý starého objektu CLR" datových tříd (POCO). Při použití těchto typů vlastních datových tříd, by měl atribut datové třídy s oběma <xref:System.Data.Services.Common.DataServiceKeyAttribute> nebo <xref:System.Data.Services.Common.DataServiceEntityAttribute> a ujistěte se, že typ názvy pro názvy typů shoda klientů v datovém modelu datové služby.  
  
 Po knihovny obdrží odpověď dotaz, to bude realizována vrácená data z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu do instancí klientská data třídy služeb, které nejsou typu dotazu. Obecný postup pro materializaci tyto objekty je následujícím způsobem:  
  
1. Klientská knihovna načte serializovaný typ z `entry` element v kanálu zprávy s odpovědí a pokusí se vytvořit novou instanci správný typ, v jednom z následujících způsobů:  
  
    - Pokud typ deklarovaný v informačním kanálu má stejný název jako typ <xref:System.Data.Services.Client.DataServiceQuery%601>, s použitím prázdného konstruktoru je vytvořena nová instance tohoto typu.  
  
    - Pokud typ deklarovaný v informačním kanálu má stejný název jako typ, který je odvozen z typu <xref:System.Data.Services.Client.DataServiceQuery%601>, s použitím prázdného konstruktoru je vytvořena nová instance tohoto typu odvozený.  
  
    - Pokud typ deklarovaný v informačním kanálu nejde spárovat typu <xref:System.Data.Services.Client.DataServiceQuery%601> nebo všechny odvozené typy, je vytvořena nová instance typu poslal dotaz s použitím prázdného konstruktoru.  
  
    - Když <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> je hodnota nastavena, zadaný delegát se nazývá přepsat výchozí mapování typu založeného na názvu a novou instanci typu vrácené <xref:System.Func%602> místo toho se vytvoří. Pokud tento delegát vrátí hodnotu null, místo toho je vytvořena nová instance typu poslal dotaz. Může být nezbytné pro přepsání výchozí mapování názvu typu založeného na názvu pro zajištění podpory scénářů dědičnosti.  
  
2. Klientská knihovna přečte hodnotu identifikátoru URI z `id` elementu `entry`, což je hodnota identity entity. Pokud <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> hodnotu <xref:System.Data.Services.Client.MergeOption.NoTracking> je použít, hodnotu identity se používá ke sledování objektů v <xref:System.Data.Services.Client.DataServiceContext>. Hodnota identity slouží také k zajištění, že pouze jedné entity je vytvořena instance, i v případě, že entity je v odpovědi na dotaz vrátil více než jednou.  
  
3. Klientská knihovna čtení vlastností z položky informačního kanálu a nastavte odpovídající vlastnosti na nově vytvořený objekt. Pokud objekt, který má stejnou hodnotu identity již probíhá <xref:System.Data.Services.Client.DataServiceContext>, jsou nastaveny na základě vlastnosti <xref:System.Data.Services.Client.MergeOption> nastavení <xref:System.Data.Services.Client.DataServiceContext>. Odpověď může obsahovat hodnoty vlastností, u kterých nedojde odpovídající vlastnost v typu klienta. Když k tomu dojde, akce závisí na hodnotě <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> vlastnost <xref:System.Data.Services.Client.DataServiceContext>. Pokud je tato vlastnost nastavena na `true`, chybí vlastnost se ignoruje. V opačném případě je vyvolána k chybě. Vlastnosti nastavené takto:  
  
    - Skalární vlastnosti jsou nastaveny na odpovídající hodnotu v položce ve zprávě s odpovědí.  
  
    - Komplexní vlastnosti jsou nastaveny na novou instanci komplexní typ, které se nastavují s vlastností komplexního typu z odpovědi.  
  
    - Navigační vlastnosti, které vracejí kolekce související entity jsou nastavené na nový nebo stávající instance systému <xref:System.Collections.Generic.ICollection%601>, kde `T` je typ entity v relaci. Tato kolekce je prázdné, pokud byly načteny související objekty do <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [načítání odložené obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
        > [!NOTE]
        >  Když data třídy generovaného klienta podporují vytváření datových vazeb, navigačních vlastností vrátit instanci <xref:System.Data.Services.Client.DataServiceCollection%601> namísto třídy. Další informace najdete v tématu [vazba dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
4. <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> Událost se vyvolá.  
  
5. Klientská knihovna připojí objekt, který má <xref:System.Data.Services.Client.DataServiceContext>. Objekt není připojený, kdy <xref:System.Data.Services.Client.MergeOption> je <xref:System.Data.Services.Client.MergeOption.NoTracking>.  
  
## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Projekce dotazů](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)
