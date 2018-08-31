---
title: Projekce dotazů (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: ca989c1cd7baa1eaeb10c65bd9ebef8e400968c3
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255219"
---
# <a name="query-projections-wcf-data-services"></a>Projekce dotazů (WCF Data Services)
Poskytuje mechanismus v projekci [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] snížit objem dat v informačním kanálu vrácených dotazem tak, že určíte, které jsou vráceny pouze určité vlastnosti entity v odpovědi. Další informace najdete v tématu [OData: Vyberte možností dotazu systému ($select)](http://go.microsoft.com/fwlink/?LinkId=186076).  
  
 Toto téma popisuje, jak k definici projekce dotazů, jaké požadavky jsou pro entitu a nonentity typy, což aktualizuje na předpokládané výsledky, vytváření předpokládané typů a jsou uvedeny některé důležité informace o projekci.  
  
## <a name="defining-a-query-projection"></a>Definování projekce dotazu  
 Můžete přidat klauzuli projekce pro dotaz s použitím `$select` možnosti v identifikátoru URI nebo pomocí dotazu [vyberte](~/docs/csharp/language-reference/keywords/select-clause.md) – klauzule ([vyberte](~/docs/visual-basic/language-reference/queries/select-clause.md) v jazyce Visual Basic) v dotazu LINQ. Vrátí entitu, kterou můžete použít k projekci dat do entity typy nebo typy nonentity na straně klienta. Příklady v tomto tématu ukazují, jak používat `select` klauzule v dotazu LINQ.  
  
> [!IMPORTANT]
>  Může dojít ke ztrátě dat ve službě dat při ukládání aktualizací, které byly provedeny na předpokládané typy. Další informace najdete v tématu [projekce aspekty](#considerations).  
  
## <a name="requirements-for-entity-and-non-entity-types"></a>Požadavky pro Entity a typy bez entit  
 Typy entit musí mít jednu nebo více vlastností identity, které společně tvoří klíč entity. Typy entit jsou definovány na klientských počítačích v jednom z následujících způsobů:  
  
-   Použitím <xref:System.Data.Services.Common.DataServiceKeyAttribute> nebo <xref:System.Data.Services.Common.DataServiceEntityAttribute> typu.  
  
-   Pokud má vlastnost s názvem typu `ID`.  
  
-   Pokud má vlastnost s názvem typu *typ*`ID`, kde *typ* je název typu.  
  
 Ve výchozím nastavení při projektu výsledků dotazu do typ definovaný v klientském počítači, musí vlastnosti požadované v projekci existovat v typu klienta. Pokud však zadáte hodnotu `true` pro <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> vlastnost <xref:System.Data.Services.Client.DataServiceContext>, vlastnostmi zadanými v projekci není nutné vyskytuje v typu klienta.  
  
### <a name="making-updates-to-projected-results"></a>Provádění aktualizací na předpokládané výsledky  
 Když projekt výsledků dotazu do typů entit v klientském počítači, <xref:System.Data.Services.Client.DataServiceContext> můžete sledovat tyto objekty s aktualizacemi k odeslání zpět k datům provozu, jestliže <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána. Aktualizace, které se provedly data promítnout do jiných entit typy na straně klienta však nelze odeslat zpět do datové služby. Je to proto, že bez klíče k identifikaci entity instance služby data nelze aktualizovat správné entitu ve zdroji dat. Typy bez entit nejsou připojené k <xref:System.Data.Services.Client.DataServiceContext>.  
  
 Pokud jeden nebo více vlastností typu entity definované ve službě data nejsou dojde k typu klienta, do kterého se plánovaných entity, vloží nové entity nesmí obsahovat tyto chybějící vlastnosti. V takovém případě budou aktualizace, které se provedly existující entity **také** obsahovat tyto chybějící vlastnosti. Když existuje hodnoty těchto vlastností, aktualizace vynuluje ji na výchozí hodnotu pro vlastnost, jak je definováno ve zdroji dat.  
  
### <a name="creating-projected-types"></a>Vytváření předpokládané typů  
 Následující příklad používá anonymní dotaz LINQ, který projekty vlastností souvisejících s adresou `Customers` typ do nového `CustomerAddress` typ, který je definován na straně klienta a atributy retrievable a searchable typ entity:  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressspecific)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressspecific)]  
  
 V tomto příkladu vzor inicializátoru objektu umožňuje vytvořit novou instanci třídy `CustmerAddress` typ namísto volání konstruktoru. Konstruktory nejsou podporovány při projekci na typy entit, ale je možné použít při projekci na jiné entity a anonymní typy. Protože `CustomerAddress` je typ entity, změny můžou provedené a odesílaných zpět do datové služby.  
  
 Kromě toho data z `Customer` typ je promítnout do instance `CustomerAddress` typ entity místo anonymního typu. Projekce do anonymních typů je podporován, ale dat je jen pro čtení, protože anonymní typy se považují za typy nonentity.  
  
 <xref:System.Data.Services.Client.MergeOption> Nastavení <xref:System.Data.Services.Client.DataServiceContext> slouží k rozlišení identity během projekce dotazu. To znamená, že pokud instance `Customer` typu již existuje v <xref:System.Data.Services.Client.DataServiceContext>, instance `CustomerAddress` se stejnou identitou bude následovat rozlišení identity pravidla nastavená organizací <xref:System.Data.Services.Client.MergeOption>  
  
Následující část popisuje chování při projekci výsledků do entity a nonentity typů:  

**Vytvoření nové instance předpokládané pomocí inicializátory**

- Příklad:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithinitializer)]

- Typ entity: podporováno

- Typ entity bez: podporováno

**Vytvoření nové instance předpokládané pomocí konstruktorů**

- Příklad: 

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithconstructor)]

- Typ entity: A <xref:System.NotSupportedException> je vyvolána.

- Typ entity bez: podporováno

**Použití projekce transformace hodnoty vlastnosti**

- Příklad:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithtransform)]
   
- Typ entity: Tato transformace není podporována pro typy entity, protože to může vést k záměně a potenciálně přepisovat data ve zdroji dat, který patří do jiné entity. A <xref:System.NotSupportedException> je vyvolána.

- Typ entity bez: podporováno  
  
<a name="considerations"></a>   
## <a name="projection-considerations"></a>Důležité informace o projekce  
 Při definování projekce dotazu, platí následující další aspekty.  
  
-   Když definujete vlastní informační kanály pro formát Atom, musíte zkontrolovat, že všechny vlastnosti entity, které mají vlastní mapování definovaná jsou zahrnuty v projekci. Vlastnost mapované entity není obsažen v projekci, může dojít ke ztrátě dat. Další informace najdete v tématu [přizpůsobení informačního kanálu](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
-   Při vkládání do očekávaného typu, který neobsahuje všechny vlastnosti entity v datovém modelu služby data si vlastnosti nejsou zahrnuty v projekci na straně klienta jsou nastaveny na výchozí hodnoty.  
  
-   Když jsou provedeny aktualizace očekávaného typu, který neobsahuje všechny vlastnosti entity v datovém modelu datové služby, bude přepsán existující hodnoty, které nejsou zahrnuty v projekci na straně klienta neinicializované výchozí hodnoty.  
  
-   Při projekci zahrnuje komplexní vlastnost, musí být vrácena celá komplexního objektu.  
  
-   Při projekci obsahuje vlastnost navigace, jsou implicitně načteny související objekty bez nutnosti volat <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Metoda není podporována pro použití v předpokládané dotazu.  
  
-   Dotaz projekce dotazů na straně klienta jsou přeloženy na použití `$select` možnosti v identifikátoru URI požadavku dotazu. Při spouštění dotazů s projekce se oproti předchozí verzi [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , který není podporován `$select` povolena možnost dotazu, je vrácena chyba. K tomu může dojít také při <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> z <xref:System.Data.Services.DataServiceBehavior> dat služby je nastavena na hodnotu <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Další informace najdete v tématu [Správa verzí datové služby](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
 Další informace najdete v tématu [postupy: výsledky dotazu projektu](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
