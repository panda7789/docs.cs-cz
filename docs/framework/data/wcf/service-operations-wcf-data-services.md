---
title: Operace služby (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: 2a043e71e15de8ffbd4a0e7296545b7af35a3e3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916640"
---
# <a name="service-operations-wcf-data-services"></a>Operace služby (WCF Data Services)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] slouží k definování operace služby ve službě data ke zveřejnění metody na serveru. Operace služby jako ostatní prostředky služby data jsou vyřešeny identifikátorů URI. Operace služby umožňují vám umožní vystavit obchodní logiku v datové služby, jako například do implementace logiky ověření na základě rolí zabezpečení, nebo k vystavení specializovaných možnostmi dotazování. Operace služeb se přidá k třídě datové služby, která je odvozena z metody <xref:System.Data.Services.DataService%601>. Stejně jako všechny ostatní prostředkům datové služby můžete zadat parametry pro metodu operaci služby. Například následující operace identifikátor URI služby (na základě [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) datové služby) předá hodnotu `London` k `city` parametr:

```
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'
```

Definice pro tuto operaci služby vypadá takto:

[!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
[!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

Můžete použít <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> z <xref:System.Data.Services.DataService%601> přímý přístup k zdroji dat, která používá datové služby. Další informace najdete v tématu [jak: Definování operace služby](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).

Informace o tom, jak volat operace služby z klientské aplikace rozhraní .NET Framework najdete v tématu [volání operací služby](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).

## <a name="service-operation-requirements"></a>Požadavky na operaci služby

Při definování operace služby na datové služby se vztahují následující požadavky. Pokud metoda těchto požadavků nesplňuje, nebude vystavit jako operace služby pro službu data.

- Operace musí být veřejná instance metodu, která je členem skupiny třídě datové služby.

- Metoda operace může přijímat pouze vstupní parametry. Datová služba je nepřístupný data odeslaná v textu zprávy.

- Pokud parametry jsou definované, každý parametr typu musí být primitivního typu. Všechna data z jiného než primitivního typu, musí být serializován a předaná do parametru řetězce.

- Metoda musí vracet jednu z následujících akcí:

  - `void` (`Nothing` v jazyce Visual Basic)

  - <xref:System.Collections.Generic.IEnumerable%601>

  - <xref:System.Linq.IQueryable%601>

  - Typ entity v datovém modelu, které data služba zpřístupňuje.

  - Základní třída jako celé číslo nebo řetězec.

- Kvůli podpoře možnosti dotazu, jako je například řazení, stránkování a filtrování, metody operace služby by měly vrátit <xref:System.Linq.IQueryable%601>. Požadavky k operacím služby, které zahrnují možnosti dotazu byly zamítnuty pro operace, které vracejí pouze <xref:System.Collections.Generic.IEnumerable%601>.

- Za účelem podpory přístupu k související entity pomocí navigačních vlastností, musí vrátit operace služby <xref:System.Linq.IQueryable%601>.

- Metoda musí být komentována atributem `[WebGet]` nebo `[WebInvoke]` atribut.

  - `[WebGet]` povoluje metody, která byla vyvolána pomocí požadavek GET.

  - `[WebInvoke(Method = "POST")]` povoluje metody, která byla vyvolána pomocí požadavku POST. Další <xref:System.ServiceModel.Web.WebInvokeAttribute> metody nejsou podporovány.

- Operace služby může být komentována atributem <xref:System.Data.Services.SingleResultAttribute> , která určuje, že návratová hodnota z metody je jedna entita, nikoli kolekci entit. Toto rozlišení přikazuje výsledný serializace odpovědi a způsob, ve kterém jsou reprezentovány další navigační vlastnost procházení v identifikátoru URI. Například při použití AtomPub serializace, typu instance jednoho prostředku je vyjádřena jako element vstupu a sadu instancí jako prvek informačního kanálu.

## <a name="addressing-service-operations"></a>Základní adresování operací služby

Operace služby můžete vyřešit tak, že název metody v první segment cesty identifikátoru URI. Jako příklad přistupuje k následující identifikátor URI `GetOrdersByState` operace, která se vrátí <xref:System.Linq.IQueryable%601> kolekce `Orders` objekty.

```
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true
```

Při volání operace služby, parametry jsou dodávány jako možnosti dotazu. Předchozí operace služby přijímá parametr řetězec `state` a parametr logické hodnoty `includeItems` , která označuje, zda zahrnout související `Order_Detail` objektů v odpovědi.

Následují platná návratové typy pro operace služby:

|Platné typy vrácených hodnot|Identifikátor URI pravidla|
|------------------------|---------------|
|`void` (`Nothing` v jazyce Visual Basic)<br /><br /> -nebo-<br /><br /> Typy entit<br /><br /> -nebo-<br /><br /> Primitivní typy|Identifikátor URI musí být jedinou cestou segment, který je název operace služby. Možnosti dotazu nejsou povoleny.|
|<xref:System.Collections.Generic.IEnumerable%601>|Identifikátor URI musí být jedinou cestou segment, který je název operace služby. Protože je typ výsledku <xref:System.Linq.IQueryable%601> typu nejsou povoleny možnosti dotazu.|
|<xref:System.Linq.IQueryable%601>|Segmenty cesty dotazu kromě cestu, která je název operace služby jsou povoleny. Možnosti dotazu jsou také povoleny.|

Na identifikátor URI v závislosti na návratový typ operace služby můžou přidávat další segmenty nebo možnosti dotazu. Například následující identifikátor URI přistupuje `GetOrdersByCity` operace, která vrací <xref:System.Linq.IQueryable%601> kolekce `Orders` objekty seřazené podle `RequiredDate` v sestupném pořadí, spolu s související `Order_Details` objekty:

```
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc
```

## <a name="service-operations-access-control"></a>Řízení přístupu ke službě Operations

Řídí viditelnost celé služby operací služby <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> metodu na <xref:System.Data.Services.IDataServiceConfiguration> třídy v podstatě stejným způsobem, že sada entit viditelnosti je řízen pomocí <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> metoda. Například následující řádek kódu v definici datové služby umožňuje přístup k `CustomersByCity` operace služby.

[!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
[!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

> [!NOTE]
> Operace služby má návratový typ, který je skrytý tak, že omezíte přístup k podkladové sady entit, operace služby nebudou mít k dispozici klientské aplikace.

Další informace najdete v tématu [jak: Definování operace služby](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).

## <a name="raising-exceptions"></a>Vyvolání výjimek

Doporučujeme použít <xref:System.Data.Services.DataServiceException> třídy pokaždé, když se vyvolat výjimku za běhu služba data. Totiž ví, modul runtime služby data jak správně mapy – vlastnosti tohoto objektu výjimky pro zprávy s odpovědí HTTP. Při vyvolávání <xref:System.Data.Services.DataServiceException> v operaci služby, je obalen výjimky vrácené <xref:System.Reflection.TargetInvocationException>. Vrátit základní <xref:System.Data.Services.DataServiceException> bez nadřazený <xref:System.Reflection.TargetInvocationException>, je nutné přepsat <xref:System.Data.Services.DataService%601.HandleException%2A> metoda ve <xref:System.Data.Services.DataService%601>, extrahovat <xref:System.Data.Services.DataServiceException> z <xref:System.Reflection.TargetInvocationException>a vraťte jej jako chyba nejvyšší úrovně, jako v následujícím příkladu:

[!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
[!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]

## <a name="see-also"></a>Viz také:

- [Zachycovače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)
