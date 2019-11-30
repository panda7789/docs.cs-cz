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
ms.openlocfilehash: c254a7362c7bc28f4b38fc0189ae0ea763bc90cc
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568850"
---
# <a name="service-operations-wcf-data-services"></a>Operace služby (WCF Data Services)

WCF Data Services umožňuje definovat operace služeb pro datovou službu k vystavení metod na serveru. Podobně jako u jiných prostředků datové služby jsou operace služby adresovány pomocí identifikátorů URI. Operace služeb umožňují zveřejnit obchodní logiku v datové službě, jako je implementace logiky ověřování, pro použití zabezpečení na základě rolí nebo k vystavování specializovaných možností dotazování. Operace služby jsou metody přidané do třídy datové služby, která je odvozena z <xref:System.Data.Services.DataService%601>. Stejně jako všechny ostatní prostředky datové služby můžete do metody operace služby zadávat parametry. Například následující identifikátor URI operace služby (založený na datové službě [rychlý Start](quickstart-wcf-data-services.md) ) předává hodnotu `London` do parametru `city`:

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'
```

Definice této operace služby je následující:

[!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
[!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

<xref:System.Data.Services.DataService%601.CurrentDataSource%2A> <xref:System.Data.Services.DataService%601> můžete použít k přímému přístupu ke zdroji dat, který datová služba používá. Další informace naleznete v tématu [How to: define a Service Operation](how-to-define-a-service-operation-wcf-data-services.md).

Informace o volání operace služby z klientské aplikace .NET Framework naleznete v tématu [Calling Service Operations](calling-service-operations-wcf-data-services.md).

## <a name="service-operation-requirements"></a>Požadavky na operace služby

Při definování operací služby v datové službě platí následující požadavky. Pokud metoda tyto požadavky nesplňuje, nebude vystavena jako operace služby pro datovou službu.

- Operace musí být metoda veřejné instance, která je členem třídy datové služby.

- Metoda operace může přijímat pouze vstupní parametry. Data odesílaná v těle zprávy nejsou k dispozici pro datovou službu.

- Pokud jsou definovány parametry, musí být typ každého parametru primitivního typu. Všechna data neprimitivního typu musí být serializována a předána do řetězcového parametru.

- Metoda musí vracet jednu z následujících možností:

  - `void` (`Nothing` v Visual Basic)

  - <xref:System.Collections.Generic.IEnumerable%601>

  - <xref:System.Linq.IQueryable%601>

  - Typ entity v datovém modelu, který datová služba zpřístupňuje.

  - Primitivní třída, jako je například celé číslo nebo řetězec.

- Aby bylo možné podporovat možnosti dotazů, jako je řazení, stránkování a filtrování, metody operací služby by měly vracet <xref:System.Linq.IQueryable%601>. Požadavky na operace služby, které obsahují možnosti dotazů, jsou odmítnuty pro operace, které vracejí pouze <xref:System.Collections.Generic.IEnumerable%601>.

- Aby bylo možné podporovat přístup k souvisejícím entitám pomocí navigačních vlastností, musí operace služby vracet <xref:System.Linq.IQueryable%601>.

- Metoda musí být opatřena poznámkou s atributem `[WebGet]` nebo `[WebInvoke]`.

  - `[WebGet]` umožňuje vyvolání metody pomocí požadavku GET.

  - `[WebInvoke(Method = "POST")]` umožňuje vyvolání metody pomocí žádosti POST. Jiné metody <xref:System.ServiceModel.Web.WebInvokeAttribute> nejsou podporovány.

- Operace služby může být opatřena poznámkou <xref:System.Data.Services.SingleResultAttribute>, která určuje, že návratová hodnota z metody je jedinou entitou, nikoli kolekcí entit. Tento rozdíl určuje výslednou serializaci odpovědi a způsob, jakým je procházení další navigační vlastnost, která je v identifikátoru URI zastoupena. Například při použití serializace AtomPub je jedna instance typu prostředku reprezentovaná jako element vstupu a sada instancí jako element informačního kanálu.

## <a name="addressing-service-operations"></a>Adresování operací služby

Operace služby můžete řešit umístěním názvu metody do prvního segmentu cesty identifikátoru URI. Příklad: následující identifikátor URI přistupuje k operaci `GetOrdersByState`, která vrací <xref:System.Linq.IQueryable%601> kolekci objektů `Orders`.

```http
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true
```

Při volání operace služby jsou parametry zadány jako možnosti dotazu. Předchozí operace služby akceptuje parametr řetězce `state` a logický parametr `includeItems`, který označuje, zda se mají zahrnout související `Order_Detail` objekty v odpovědi.

Níže jsou uvedené platné návratové typy pro operaci služby:

|Platné návratové typy|Pravidla identifikátoru URI|
|------------------------|---------------|
|`void` (`Nothing` v Visual Basic)<br /><br /> -nebo-<br /><br /> Typy entit<br /><br /> -nebo-<br /><br /> Primitivní typy|Identifikátor URI musí být jeden segment cesty, který je názvem operace služby. Možnosti dotazu nejsou povoleny.|
|<xref:System.Collections.Generic.IEnumerable%601>|Identifikátor URI musí být jeden segment cesty, který je názvem operace služby. Vzhledem k tomu, že typ výsledku není <xref:System.Linq.IQueryable%601> typ, možnosti dotazu nejsou povoleny.|
|<xref:System.Linq.IQueryable%601>|Kromě cesty, která je názvem operace služby, je povolený segment cesty k dotazům. Možnosti dotazu jsou také povoleny.|

Další segmenty cesty nebo možnosti dotazu lze přidat k identifikátoru URI v závislosti na návratový typ operace služby. Například následující identifikátor URI přistupuje k operaci `GetOrdersByCity`, která vrací <xref:System.Linq.IQueryable%601> kolekci `Orders` objektů seřazené podle `RequiredDate` v sestupném pořadí, spolu se souvisejícími `Order_Details` objekty:

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc
```

## <a name="service-operations-access-control"></a>Access Control operací služby

Viditelnost operací služby na úrovni služby je řízená metodou <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> na <xref:System.Data.Services.IDataServiceConfiguration> třídě, a to v podstatě stejným způsobem, jako viditelnost sady entit je řízená pomocí metody <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A>. Například následující řádek kódu v definici datové služby umožňuje přístup k operaci `CustomersByCity` služby.

[!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
[!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

> [!NOTE]
> Pokud má operace služby návratový typ, který byl skrytý omezením přístupu na podkladové sady entit, operace služby nebude k dispozici pro klientské aplikace.

Další informace naleznete v tématu [How to: define a Service Operation](how-to-define-a-service-operation-wcf-data-services.md).

## <a name="raising-exceptions"></a>Vyvolávání výjimek

Doporučujeme použít třídu <xref:System.Data.Services.DataServiceException> vždy, když ve spuštění datové služby vyvoláte výjimku. Důvodem je to, že modul runtime datové služby ví, jak správně namapovat vlastnosti tohoto objektu výjimky na zprávu odpovědi HTTP. Když v rámci operace služby vyvoláte <xref:System.Data.Services.DataServiceException>, vrácená výjimka je zabalená do <xref:System.Reflection.TargetInvocationException>. Chcete-li vrátit základní <xref:System.Data.Services.DataServiceException> bez ohraničujícího <xref:System.Reflection.TargetInvocationException>, je nutné přepsat metodu <xref:System.Data.Services.DataService%601.HandleException%2A> v <xref:System.Data.Services.DataService%601>, extrahovat <xref:System.Data.Services.DataServiceException> z <xref:System.Reflection.TargetInvocationException>a vrátit je jako chybu nejvyšší úrovně, jak je uvedeno v následujícím příkladu:

[!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
[!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]

## <a name="see-also"></a>Viz také:

- [Zachycovače](interceptors-wcf-data-services.md)
