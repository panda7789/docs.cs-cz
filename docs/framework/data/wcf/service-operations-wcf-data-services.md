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
ms.openlocfilehash: 4f36081ef1a3eec84f3cc2ced3c629109acd6a38
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894267"
---
# <a name="service-operations-wcf-data-services"></a>Operace služby (WCF Data Services)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje definovat operace služeb pro datovou službu k vystavení metod na serveru. Podobně jako u jiných prostředků datové služby jsou operace služby adresovány pomocí identifikátorů URI. Operace služeb umožňují zveřejnit obchodní logiku v datové službě, jako je implementace logiky ověřování, pro použití zabezpečení na základě rolí nebo k vystavování specializovaných možností dotazování. Operace služby jsou metody přidané do třídy datové služby, která je odvozena <xref:System.Data.Services.DataService%601>z. Stejně jako všechny ostatní prostředky datové služby můžete do metody operace služby zadávat parametry. Například následující identifikátor URI operace služby (založený na datové službě [rychlý Start](quickstart-wcf-data-services.md) ) předává hodnotu `London` `city` parametru:

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'
```

Definice této operace služby je následující:

[!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
[!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

Můžete použít <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> <xref:System.Data.Services.DataService%601> pro přímý přístup ke zdroji dat, který datová služba používá. Další informace najdete v tématu [jak: Definujte operaci](how-to-define-a-service-operation-wcf-data-services.md)služby.

Informace o volání operace služby z klientské aplikace .NET Framework naleznete v tématu [Calling Service Operations](calling-service-operations-wcf-data-services.md).

## <a name="service-operation-requirements"></a>Požadavky na operace služby

Při definování operací služby v datové službě platí následující požadavky. Pokud metoda tyto požadavky nesplňuje, nebude vystavena jako operace služby pro datovou službu.

- Operace musí být metoda veřejné instance, která je členem třídy datové služby.

- Metoda operace může přijímat pouze vstupní parametry. Data odesílaná v těle zprávy nejsou k dispozici pro datovou službu.

- Pokud jsou definovány parametry, musí být typ každého parametru primitivního typu. Všechna data neprimitivního typu musí být serializována a předána do řetězcového parametru.

- Metoda musí vracet jednu z následujících možností:

  - `void`(`Nothing` v Visual Basic)

  - <xref:System.Collections.Generic.IEnumerable%601>

  - <xref:System.Linq.IQueryable%601>

  - Typ entity v datovém modelu, který datová služba zpřístupňuje.

  - Primitivní třída, jako je například celé číslo nebo řetězec.

- Aby bylo možné podporovat možnosti dotazů, jako je řazení, stránkování a filtrování, metody operací služby by měly <xref:System.Linq.IQueryable%601>vracet. Požadavky na operace služby, které obsahují možnosti dotazů, jsou odmítnuty pro operace <xref:System.Collections.Generic.IEnumerable%601>, které vracejí pouze.

- Aby bylo možné podporovat přístup k souvisejícím entitám pomocí navigačních vlastností, musí operace služby <xref:System.Linq.IQueryable%601>vracet.

- Metoda musí být opatřena poznámkou `[WebGet]` s `[WebInvoke]` atributem or.

  - `[WebGet]`umožňuje vyvolání metody pomocí požadavku GET.

  - `[WebInvoke(Method = "POST")]`umožňuje vyvolání metody pomocí požadavku POST. Jiné <xref:System.ServiceModel.Web.WebInvokeAttribute> metody nejsou podporovány.

- Operace služby může být opatřena poznámkou <xref:System.Data.Services.SingleResultAttribute> , která určuje, že návratová hodnota z metody je jedinou entitou, nikoli kolekcí entit. Tento rozdíl určuje výslednou serializaci odpovědi a způsob, jakým je procházení další navigační vlastnost, která je v identifikátoru URI zastoupena. Například při použití serializace AtomPub je jedna instance typu prostředku reprezentovaná jako element vstupu a sada instancí jako element informačního kanálu.

## <a name="addressing-service-operations"></a>Adresování operací služby

Operace služby můžete řešit umístěním názvu metody do prvního segmentu cesty identifikátoru URI. Příklad: následující identifikátor URI přistupuje `GetOrdersByState` k operaci, která <xref:System.Linq.IQueryable%601> vrací kolekci `Orders` objektů.

```http
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true
```

Při volání operace služby jsou parametry zadány jako možnosti dotazu. Předchozí operace služby přijímá parametr `state` řetězce a logický parametr `includeItems` , který označuje, zda se mají zahrnout související `Order_Detail` objekty v odpovědi.

Níže jsou uvedené platné návratové typy pro operaci služby:

|Platné návratové typy|Pravidla identifikátoru URI|
|------------------------|---------------|
|`void`(`Nothing` v Visual Basic)<br /><br /> -nebo-<br /><br /> Typy entit<br /><br /> -nebo-<br /><br /> Primitivní typy|Identifikátor URI musí být jeden segment cesty, který je názvem operace služby. Možnosti dotazu nejsou povoleny.|
|<xref:System.Collections.Generic.IEnumerable%601>|Identifikátor URI musí být jeden segment cesty, který je názvem operace služby. Vzhledem k tomu, že typ <xref:System.Linq.IQueryable%601> výsledku není typ, možnosti dotazu nejsou povoleny.|
|<xref:System.Linq.IQueryable%601>|Kromě cesty, která je názvem operace služby, je povolený segment cesty k dotazům. Možnosti dotazu jsou také povoleny.|

Další segmenty cesty nebo možnosti dotazu lze přidat k identifikátoru URI v závislosti na návratový typ operace služby. Například následující identifikátor URI přistupuje `GetOrdersByCity` k operaci, která <xref:System.Linq.IQueryable%601> vrací kolekci `Orders` objektů seřazené podle `RequiredDate` sestupně v sestupném pořadí, spolu se souvisejícími `Order_Details` objekty:

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc
```

## <a name="service-operations-access-control"></a>Access Control operací služby

Viditelnost operací služby pro nejrůznější služby je ovládána <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> metodou <xref:System.Data.Services.IDataServiceConfiguration> třídy v podstatě stejným způsobem, jako viditelnost sady entit <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> je ovládána pomocí metody. Například následující řádek kódu v definici datové služby umožňuje přístup k `CustomersByCity` operaci služby.

[!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
[!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

> [!NOTE]
> Pokud má operace služby návratový typ, který byl skrytý omezením přístupu na podkladové sady entit, operace služby nebude k dispozici pro klientské aplikace.

Další informace najdete v tématu [jak: Definujte operaci](how-to-define-a-service-operation-wcf-data-services.md)služby.

## <a name="raising-exceptions"></a>Vyvolávání výjimek

Doporučujeme použít <xref:System.Data.Services.DataServiceException> třídu vždy, když vyvoláte výjimku při spuštění datové služby. Důvodem je to, že modul runtime datové služby ví, jak správně namapovat vlastnosti tohoto objektu výjimky na zprávu odpovědi HTTP. Při vyvolání <xref:System.Data.Services.DataServiceException> operace služby je vrácená výjimka zabalena <xref:System.Reflection.TargetInvocationException>do. Chcete-li vrátit <xref:System.Data.Services.DataServiceException> základ bez <xref:System.Reflection.TargetInvocationException>ohraničujícího <xref:System.Data.Services.DataService%601.HandleException%2A> , je nutné <xref:System.Data.Services.DataService%601>přepsat <xref:System.Reflection.TargetInvocationException>metodu v, extrahovat <xref:System.Data.Services.DataServiceException> z a, a vrátit ji jako chybu nejvyšší úrovně, jak je uvedeno v následujícím příkladu:

[!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
[!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]

## <a name="see-also"></a>Viz také:

- [Zachycovače](interceptors-wcf-data-services.md)
