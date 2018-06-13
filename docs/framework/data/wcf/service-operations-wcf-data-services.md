---
title: Operace služby (služby WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: da8d482fbf506749f9805edcbbaad3c893ad56b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365849"
---
# <a name="service-operations-wcf-data-services"></a>Operace služby (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umožňuje definovat operace služby ve službě data ke zveřejnění metody na serveru. Jako další prostředky služby dat jsou operací služby řešit identifikátory URI. Operace služby umožňují vystavit obchodní logiky v datové služby, jako třeba implementovat logiku ověření pro použití na základě rolí zabezpečení, nebo ke zveřejnění specializovaných dotazování možnosti. Operace služby jsou metody přidat k třídě služby data, která je odvozena od <xref:System.Data.Services.DataService%601>. Podobně jako všechny ostatní datové prostředky služby můžete zadat parametry pro metodu operaci služby. Například následující operace identifikátor URI služby (na základě [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) služba dat) předá hodnotu `London` k `city` parametr:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'  
```  
  
 Definice pro tuto operaci služby je následující:  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
 [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
 Můžete použít <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> z <xref:System.Data.Services.DataService%601> přímý přístup k zdroje dat, který používá službu data. Další informace najdete v tématu [postupy: Definování operace služby](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
 Informace o tom, jak volat operace služby z klientské aplikace rozhraní .NET Framework najdete v tématu [volání operací služby](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).  
  
## <a name="service-operation-requirements"></a>Požadavky na operaci služby  
 Následující požadavky platí při definování operací služby na službu data. Pokud metoda těchto požadavků nesplňuje, nebude vystavit jako operaci služby pro službu data.  
  
-   Operace musí být veřejné instance metodu, která je členem třídě dat služby.  
  
-   Metoda operace může přijímat pouze vstupní parametry. Data odeslaná v textu zprávy nelze přistupovat pomocí služby data.  
  
-   Pokud jsou definovány parametry, musí být typ každý parametr primitivní typ. Žádná data není primitivní typ musí být serializován a předána do parametr řetězce.  
  
-   Metoda musí vrátit jednu z těchto možností:  
  
    -   `void` (`Nothing` v jazyce Visual Basic)  
  
    -   <xref:System.Collections.Generic.IEnumerable%601>  
  
    -   <xref:System.Linq.IQueryable%601>  
  
    -   Typ entity v datovém modelu, že data služby vystavuje.  
  
    -   Primitivní třída jako celé číslo nebo řetězec.  
  
-   Kvůli podpoře možnosti dotazu, jako je například řazení, stránkování a filtrování, by měla vrátit operaci metody služeb <xref:System.Linq.IQueryable%601>. Požadavky k operacím služby, které zahrnují možnosti dotazu byly zamítnuty pro operace, které vrátit pouze <xref:System.Collections.Generic.IEnumerable%601>.  
  
-   Aby bylo možné podporovat, přístup k entit v relaci s použitím navigační vlastnosti, musí vrátit operaci služby <xref:System.Linq.IQueryable%601>.  
  
-   Metoda musí být opatřena poznámkou `[WebGet]` nebo `[WebInvoke]` atribut.  
  
    -   `[WebGet]` umožňuje metoda k vyvolání pomocí požadavek GET.  
  
    -   `[WebInvoke(Method = "POST")]` umožňuje metoda k vyvolání pomocí požadavek POST. Další <xref:System.ServiceModel.Web.WebInvokeAttribute> metody nejsou podporovány.  
  
-   Operace služby, které může být opatřena poznámkou <xref:System.Data.Services.SingleResultAttribute> který určuje, že je vrácená hodnota z metody jedné entity, nikoli kolekci entit. Tento rozdíl určuje výsledný serializaci odpovědi a způsob, ve kterém jsou další navigační vlastnost traversals určený v identifikátoru URI. Například při použití AtomPub serializace, jeden prostředek typ instance reprezentována jako element položky a sady instancí jako element informačního kanálu.  
  
## <a name="addressing-service-operations"></a>Adresování operací služby  
 Operace služby můžete vyřešit tak, že název metody první segment cesty identifikátoru URI. Jako příklad následující identifikátor URI přistupuje `GetOrdersByState` operaci, která vrátí <xref:System.Linq.IQueryable%601> kolekce `Orders` objekty.  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true  
```  
  
 Při volání operace služby, jsou zadány parametry jako možnosti dotazu. Předchozí operace služby přijme parametr řetězec `state` a logickým parametrem `includeItems` určující, zda chcete zahrnout související `Order_Detail` objektů v odpovědi.  
  
 Tady jsou platné návratové typy pro operace služby:  
  
|Platný návratové typy|Identifikátor URI pravidla|  
|------------------------|---------------|  
|`void` (`Nothing` v jazyce Visual Basic)<br /><br /> -nebo-<br /><br /> Typy entit<br /><br /> -nebo-<br /><br /> Primitivní typy|Identifikátor URI musí být jednou cestou segment, který je název operaci služby. Možnosti dotazu nejsou povoleny.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Identifikátor URI musí být jednou cestou segment, který je název operaci služby. Protože výsledný typ není <xref:System.Linq.IQueryable%601> typu nejsou povoleny možnosti dotazu.|  
|<xref:System.Linq.IQueryable%601>|Segmenty cesty dotazu kromě cestu, která je název operace služby jsou povoleny. Povolené jsou i možnosti dotazu.|  
  
 Segmenty cesty další nebo možnosti dotazu mohou být přidány do identifikátoru URI v závislosti na návratový typ operace služby. Například následující identifikátor URI přistupuje `GetOrdersByCity` operaci, která vrátí <xref:System.Linq.IQueryable%601> kolekce `Orders` objekty, které jsou seřazené podle `RequiredDate` v sestupném pořadí, společně s související `Order_Details` objekty:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc  
```  
  
## <a name="service-operations-access-control"></a>Řízení přístupu ke službě Operations  
 Řídí celé služby viditelnost operací služby <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> metodu <xref:System.Data.Services.IDataServiceConfiguration> třída mnohem stejným způsobem, že sada entit viditelnost je řízen pomocí <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> metoda. Například následující řádek kódu v definici datové služby umožňuje přístup k `CustomersByCity` operace služby.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
 [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
> [!NOTE]
>  Operace služby má návratový typ, který je skrytý tak, že omezíte přístup na základní sady entit, operace služby nebudete mít k dispozici pro klientské aplikace.  
  
 Další informace najdete v tématu [postupy: Definování operace služby](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
## <a name="raising-exceptions"></a>Vyvolávání výjimek  
 Doporučujeme vám, že používáte <xref:System.Data.Services.DataServiceException> třídy vždy, když je vyvolána výjimka při provádění service data. To je proto zná běh služby data mapování vlastnosti tohoto objektu výjimka správně do zprávy s odpovědí HTTP. Když zvýšíte <xref:System.Data.Services.DataServiceException> v operaci služby vrácený výjimka je zabalené do <xref:System.Reflection.TargetInvocationException>. Vrátit základní <xref:System.Data.Services.DataServiceException> bez ohraničení <xref:System.Reflection.TargetInvocationException>, je nutné přepsat <xref:System.Data.Services.DataService%601.HandleException%2A> metoda v <xref:System.Data.Services.DataService%601>, rozbalte <xref:System.Data.Services.DataServiceException> z <xref:System.Reflection.TargetInvocationException>a obnoví v něm jako chyba nejvyšší úrovně, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#handleexceptions)]
 [!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#handleexceptions)]  
  
## <a name="see-also"></a>Viz také  
 [Zachycovače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)
