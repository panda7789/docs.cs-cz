---
title: "Objekt Materialization (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f671d3b41e0812916d1db342c211f2db6456ede3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-materialization-wcf-data-services"></a>Objekt Materialization (služby WCF Data Services)
Při použití **přidat odkaz na službu** dialogovém okně můžete využívat [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu v aplikaci klienta na základě rozhraní .NET Framework, ke každému typu entity v datovém modelu, který je zveřejněný prostřednictvím informačního kanálu se generují ekvivalentní datové třídy. Další informace najdete v tématu [generování dat služby klientské knihovny](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Data entity, který je vrácen dotazu je vyhodnocena do instance jednoho z těchto tříd služby data generovaného klienta. Informace o možnostech sloučení a řešení identity sledovaných objektů najdete v tématu [Správa služby kontextu dat](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]také umožňuje definovat vaše vlastní třídy klienta dat služby místo použití tříd nástroj generovaná data. To umožňuje používat vlastní datové třídy, také známé jako "prostý starý CLR objektu" (objektů POCO) datových tříd. Při použití těchto typů vlastních datových tříd, má atribut třída dat pomocí <xref:System.Data.Services.Common.DataServiceKeyAttribute> nebo <xref:System.Data.Services.Common.DataServiceEntityAttribute> a ujistěte se, že typ názvy na názvy typů shody klienta v datovém modelu datové služby.  
  
 Po knihovny obdrží zprávu odpovědi dotazu, se bude realizována vrácená data z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu do instance dat klienta třídy služeb, které jsou typu dotazu. Obecný postup pro vyhodnocování tyto objekty vypadá takto:  
  
1.  Klientská knihovna čte serializovaných typu z `entry` element v kanálu zprávu odpovědi a pokusy o vytvoření nové instance správného typu, v jednom z následujících způsobů:  
  
    -   Pokud typ deklarován v informačním kanálu má stejný název jako typ <xref:System.Data.Services.Client.DataServiceQuery%601>, je vytvořena nová instance tohoto typu pomocí prázdného konstruktoru.  
  
    -   Pokud typ deklarován v informačním kanálu má stejný název jako typ, který je odvozen z typu <xref:System.Data.Services.Client.DataServiceQuery%601>, pomocí prázdného konstruktoru je vytvořena nová instance tohoto odvozeného typu.  
  
    -   Pokud typ deklarován v informačním kanálu nelze namapovat na typ <xref:System.Data.Services.Client.DataServiceQuery%601> nebo všechny odvozené typy, novou instanci třídy dotazovaný typ je vytvořená pomocí prázdného konstruktoru.  
  
    -   Když <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> vlastnost nastavena, zadaný delegát nazývá přepsat výchozí mapování na základě názvu typu a novou instanci třídy typ vrácený <xref:System.Func%602> místo toho je vytvořena. Pokud tento delegát vrátí hodnotu null, místo toho je vytvořena nová instance typu předmětem dotazu. Může být nezbytné přepsat výchozí mapování názvu na základě názvu typu pro podporu dědičnosti scénářů.  
  
2.  Klientská knihovna čte hodnota z identifikátoru URI `id` element `entry`, což je hodnota identity entity. Pokud <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> hodnotu <xref:System.Data.Services.Client.MergeOption.NoTracking> se používá, hodnotu identity slouží ke sledování objektu ve <xref:System.Data.Services.Client.DataServiceContext>. Zaručit, že pouze jedna entita instance je vytvořen i v případě, že entita je v odpovědi na dotaz vrátil více než jednou. je také použít hodnotu identity.  
  
3.  Klientská knihovna načte vlastnosti ze zadaného informačního kanálu a nastavte odpovídající vlastnosti na nově vytvořený objekt. Pokud objekt, který už má stejnou hodnotu identity dojde v <xref:System.Data.Services.Client.DataServiceContext>, vlastnosti jsou nastavené na základě <xref:System.Data.Services.Client.MergeOption> nastavit <xref:System.Data.Services.Client.DataServiceContext>. Odpovědi může obsahovat hodnoty vlastností, pro které nedojde odpovídající vlastnosti v typu klienta. V takovém případě akce závisí na hodnotu <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> vlastnost <xref:System.Data.Services.Client.DataServiceContext>. Pokud je tato vlastnost nastavená na `true`, chybí vlastnost je ignorována. Jinak je vyvolána k chybě. Vlastnosti jsou nastaveny takto:  
  
    -   Skalární vlastnosti jsou nastaveny na odpovídající hodnotu v položce ve zprávě s odpovědí.  
  
    -   Komplexní vlastnosti jsou nastaveny na novou instanci komplexního typu, které lze nastavit s vlastnostmi komplexní typ z odpovědi.  
  
    -   Navigační vlastnosti, které vrací kolekce entit v relaci jsou nastaveny na nový nebo existující instanci systému <xref:System.Collections.Generic.ICollection%601>, kde `T` je typ entity v relaci. Tato kolekce je prázdný, pokud souvisejících objektů, které byly načteny do <xref:System.Data.Services.Client.DataServiceContext>. Další informace najdete v tématu [načítání odložení obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
        > [!NOTE]
        >  Při datové třídy generovaného klienta podporovat datové vazby, navigačních vlastností vrátit instanci <xref:System.Data.Services.Client.DataServiceCollection%601> třídy místo. Další informace najdete v tématu [vazby dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
4.  <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> Událost se vyvolá.  
  
5.  Klientská knihovna připojí objekt, který má <xref:System.Data.Services.Client.DataServiceContext>. Objekt není připojený, kdy <xref:System.Data.Services.Client.MergeOption> je <xref:System.Data.Services.Client.MergeOption.NoTracking>.  
  
## <a name="see-also"></a>Viz také  
 [Dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Projekce dotazu](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)
