---
title: Projekce dotazu (služby WCF Data Services)
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
ms.openlocfilehash: 903acaa7493dc83fd6bf50f5a578a067c15e6294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365719"
---
# <a name="query-projections-wcf-data-services"></a>Projekce dotazu (služby WCF Data Services)
Poskytuje mechanismus v projekci [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] ke snížení množství dat v informačním kanálu vrácených dotazem zadáním jenom některé vlastnosti entity jsou vráceny v odpovědi. Další informace najdete v tématu [OData: Vyberte možností dotazu systému ($select)](http://go.microsoft.com/fwlink/?LinkId=186076).  
  
 Toto téma popisuje, jak definovat projekce dotazu, jaké požadavky jsou pro entitu a typy nonentity, provedení aktualizace předpokládané výsledky, vytváření předpokládané typy a uvádí některé aspekty projekce.  
  
## <a name="defining-a-query-projection"></a>Definování projekce dotazu  
 Můžete přidat klauzuli projekce na dotaz buď pomocí `$select` možnost v identifikátoru URI nebo pomocí dotazu [vyberte](~/docs/csharp/language-reference/keywords/select-clause.md) klauzuli ([vyberte](~/docs/visual-basic/language-reference/queries/select-clause.md) v jazyce Visual Basic) v dotazu LINQ. Vrácené entity, které můžete použít k projekci dat na typy entit a typy nonentity na straně klienta. Příklady v tomto tématu ukazují, jak používat `select` klauzuli v dotazu LINQ.  
  
> [!IMPORTANT]
>  Může dojít ke ztrátě dat ve službě dat při ukládání aktualizací, které byly provedeny na předpokládané typy. Další informace najdete v tématu [projekce aspekty](#considerations).  
  
## <a name="requirements-for-entity-and-non-entity-types"></a>Požadavky pro entitu a Nonentity typy  
 Typy entit musí mít jeden nebo více vlastnosti identity, které tvoří klíč entity. Typy entit jsou definovány na klientských počítačích v jednom z následujících způsobů:  
  
-   S použitím <xref:System.Data.Services.Common.DataServiceKeyAttribute> nebo <xref:System.Data.Services.Common.DataServiceEntityAttribute> typu.  
  
-   Pokud má tento typ vlastnost s názvem `ID`.  
  
-   Pokud má vlastnost s názvem typ *typ*`ID`, kde *typu* je název typu.  
  
 Ve výchozím nastavení když projektu výsledků dotazu do typu definované na straně klienta, musí vlastnosti požadované v projekci existovat v typu klienta. Ale pokud zadáte hodnotu `true` pro <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> vlastnost <xref:System.Data.Services.Client.DataServiceContext>, vlastnosti zadané v projekci není nutné dochází k výskytu typ klienta.  
  
### <a name="making-updates-to-projected-results"></a>Provedení aktualizací předpokládané výsledky  
 Pokud projekt výsledků dotazu do typy entit na straně klienta <xref:System.Data.Services.Client.DataServiceContext> můžete sledovat tyto objekty s aktualizacemi k odeslání zpět do dat služby při <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda je volána. Aktualizace, které jsou vytvářeny k datům promítnout do jiných entity typy na straně klienta však nelze odeslat zpět na službu data. Je to proto, že bez klíče k identifikaci entity instance, službu data nelze aktualizovat správné entity v datovém zdroji. Typy entit bez nejsou připojeny ke <xref:System.Data.Services.Client.DataServiceContext>.  
  
 Pokud nedojde k jedné nebo více vlastností typu entity definované ve službě data v typ klienta, do kterého se promítá entity, vloží nové entity nebude obsahovat tyto chybějící vlastnosti. V takovém případě se aktualizace provedené na existující entity **také** obsahovat tyto chybějící vlastnosti. Pokud existuje hodnota pro taková vlastnost, aktualizace vymazán na výchozí hodnotu pro vlastnost, definovaným ve zdroji dat.  
  
### <a name="creating-projected-types"></a>Vytváření předpokládané typy  
 Následující příklad používá anonymní dotaz LINQ, který projekty vlastností souvisejících s adresou `Customers` typu do nového `CustomerAddress` typu, který je definován na straně klienta a je označené jako typ entity:  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressspecific)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressspecific)]  
  
 V tomto příkladu vzor inicializátoru objektu slouží k vytvoření nové instance `CustmerAddress` typ namísto volání konstruktoru. Konstruktory nejsou podporovány při projekci do typy entit, ale je lze použít při projekci do jiné entity a anonymní typy. Protože `CustomerAddress` je typ entity změny můžete provedeny a odeslána zpět do službu data.  
  
 Také data z `Customer` typu se promítá do instance `CustomerAddress` typ entity místo anonymního typu. Projekce do anonymní typy je podporována, ale data je jen pro čtení, protože anonymní typy jsou považovány za typy nonentity.  
  
 <xref:System.Data.Services.Client.MergeOption> Nastavení <xref:System.Data.Services.Client.DataServiceContext> se používají pro překlad identity během projekce dotazu. To znamená, že pokud instance `Customer` typ už v <xref:System.Data.Services.Client.DataServiceContext>, instanci `CustomerAddress` se stejnou identitou bude postupovat podle řešení identity, pravidla, která nastavuje <xref:System.Data.Services.Client.MergeOption>  
  
 Následující tabulka popisuje chování při projekci výsledky na typy entit a nonentity:  
  
|Akce|Typ entity|Typ bez Entity|  
|------------|-----------------|----------------------|  
|Vytvoření nové instance předpokládané pomocí inicializátory, jako v následujícím příkladu:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithinitializer)]
 [!code-vb[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithinitializer)]|Podporováno|Podporováno|  
|Vytvoření nové instance předpokládané pomocí konstruktorů, jako v následujícím příkladu:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithconstructor)]
 [!code-vb[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithconstructor)]|A <xref:System.NotSupportedException> je vyvolána.|Podporováno|  
|Projekce používání k transformaci hodnotu vlastnosti, jako v následujícím příkladu:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithtransform)]
 [!code-vb[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithtransform)]<br /><br /> Tato transformace není podporována pro typy entit, protože může vést k záměně a potenciálně přepsal dat ve zdroji dat, který patří k jiné entitě.|A <xref:System.NotSupportedException> je vyvolána.|Podporováno|  
  
<a name="considerations"></a>   
## <a name="projection-considerations"></a>Aspekty projekce  
 Při definování projekce dotazu, platí následující další aspekty.  
  
-   Když definujete vlastní informační kanály pro formát Atom, musí se ujistěte, že všechny vlastnosti entity, které mají vlastní mapování definovaná jsou zahrnuty v projekci. Vlastnost namapované entity není obsažen v projekci, může dojít ke ztrátě dat. Další informace najdete v tématu [kanálu přizpůsobení](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
-   Při vložení provedení předpokládané typ, který neobsahuje všechny vlastnosti entity v datovém modelu služby dat, vlastnosti nejsou zahrnuty v projekci na straně klienta jsou nastaveny na výchozí hodnoty.  
  
-   Při aktualizace provedení předpokládané typ, který neobsahuje všechny vlastnosti entity v datovém modelu datové služby, existující hodnoty, které nejsou zahrnuty v projekci na straně klienta, budou přepsány Neinicializovaný výchozí hodnoty.  
  
-   Pokud projekci obsahuje komplexní vlastnost, musí být vrácen celý komplexní objekt.  
  
-   Pokud projekci zahrnuje vlastnost navigace, souvisejících objektů, které jsou načteny implicitně bez nutnosti volání <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metoda. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Metoda není podporována pro použití v předpokládané dotazu.  
  
-   Dotazy projekce dotazu na straně klienta jsou převedeny na použití `$select` dotaz v identifikátoru URI požadavku možnost. Pokud je dotaz s projekce spustit pro předchozí verze [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] nepodporujícím `$select` volbu dotazu, je vrácena chyba. K tomu může dojít také při <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> z <xref:System.Data.Services.DataServiceBehavior> pro data služby nastavena na hodnotu <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Další informace najdete v tématu [verze datové služby](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
 Další informace najdete v tématu [postup: výsledky dotazu projektu](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
