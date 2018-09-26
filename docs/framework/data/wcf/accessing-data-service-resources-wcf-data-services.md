---
title: Přístup k prostředkům datové služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: d4f4de1fa12418bd56f9680e5414bfe7dd0aa128
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070848"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>Přístup k prostředkům datové služby (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] k vystavení dat jako informační kanál s prostředky, které jsou adresovat pomocí identifikátorů URI. Tyto prostředky jsou reprezentovány podle konvencí relace entity [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md). V tomto modelu entity představují provozní jednotek dat, které jsou datové typy v aplikační doméně, jako je například zákazníky, objednávky, položky a produkty. Entity data je přístupné a změnit pomocí sémantiky representational state Transfer (REST), konkrétně standardní HTTP příkazy GET, PUT, POST a DELETE.  
  
## <a name="addressing-resources"></a>Adresování prostředků  
 V [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], vyřešit všechny data vystavená prostřednictvím datového modelu s použitím identifikátoru URI. Například následující identifikátor URI vrátí informační kanál sady entit zákazníků, který obsahuje záznamy pro všechny instance typu entity zákazníka:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 Entity obsahují speciální vlastnosti volá klíče entit. Klíč entity slouží k jednoznačné identifikaci jedné entity v sadě entit. To umožňuje řešit konkrétní instanci typu entity v sadě entit. Například následující identifikátor URI vrátí záznam pro konkrétní instanci typu entity zákazník, který má klíč hodnotu `ALFKI`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 Vlastnosti primitivních a komplexních instanci entity lze také jednotlivě řešit. Například následující identifikátor URI vrací XML, který obsahuje element `ContactName` hodnota vlastnosti pro konkrétního zákazníka:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 Pokud zahrnete `$value` předchozí identifikátor URI pro koncový bod, je vrácena pouze hodnota primitivní vlastnosti ve zprávě s odpovědí. Následující příklad vrátí pouze řetězec "Marie Marková" bez elementu XML:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 Vztahy mezi entitami jsou definovány v datovém modelu přidružení. Tato přidružení umožňují řešit souvisejících entit pomocí navigačních vlastností instance entity. Navigační vlastnost může vrátit buď jednu související entitu, v případě vztah mnoha k jednomu nebo sadu souvisejících entit v případě vztah jeden mnoho. Například následující identifikátor URI vrátí informační kanál, který je sada všech objednávek, které se týkají určitého zákazníka:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 Vztahy, které jsou obvykle obousměrný, jsou reprezentovány pár navigační vlastnosti. Následující identifikátor URI jako reverse relace je uvedeno v předchozím příkladu, vrátí odkaz na entitu zákazníka, ke kterému patří konkrétní entity pořadí:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Můžete se také pro adresování prostředků na základě výsledků – výrazy dotazů. To umožňuje filtrovat sadu prostředků můžete podle vyhodnocený výraz. Například následující identifikátor URI vyfiltruje prostředky, které vrátí pouze objednávky pro daného zákazníka, které byly dodány od 22. září 1997:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 Další informace najdete v tématu [OData: identifikátor URI konvence](https://go.microsoft.com/fwlink/?LinkId=185564).  
  
## <a name="system-query-options"></a>Možnosti dotazu systému  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] definuje sadu možností dotazu systému, které můžete použít k provedení dotazu tradiční operací s prostředky, jako je například filtrování, řazení a stránkování. Například následující identifikátor URI vrací sadu všech `Order` entity, spolu se souvisejícími `Order_Detail` entity, PSČ, z nichž nekončí řetězcem `100`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 Položky v informačním kanálu vrácené jsou také seřazené podle hodnoty vlastnosti ShipCity objednávek.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje následující [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] možností dotazu systému:  
  
|Možnost dotazu|Popis|  
|------------------|-----------------|  
|`$orderby`|Definuje výchozí pořadí řazení pro entity ve vrácené informační kanál. Následující dotaz objednávek vrácených zákazníky kanálu kraj a Město:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> Další informace najdete v tématu [OData: systému povolena možnost dotazu OrderBy ($orderby)](https://go.microsoft.com/fwlink/?LinkId=186968).|  
|`$top`|Určuje počet entit, které mají být zahrnuty vrácené informační kanál. Následující příklad Přeskočí prvních 10 zákazníků a vrátí další 10:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Další informace najdete v tématu [OData: možností dotazu systému nahoru ($top)](https://go.microsoft.com/fwlink/?LinkId=186969).|  
|`$skip`|Určuje počet entit, chcete-li přeskočit před zahájením vrátit entity v informačním kanálu. Následující příklad Přeskočí prvních 10 zákazníků a vrátí další 10:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Další informace najdete v tématu [OData: možností dotazu systému přeskočit ($skip)](https://go.microsoft.com/fwlink/?LinkId=186971).|  
|`$filter`|Definuje výraz, který filtry, které jsou vráceny v informačním kanálu entity na základě určitých kritérií. Tuto možnost dotazu podporuje sadu logických porovnávací operátory, aritmetické operátory a funkce předdefinovaného dotazu, které se používají k vyhodnocení výrazu filtru. Následující příklad vrátí všechny objednávky, PSČ, z nichž nekončí 100:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> Další informace najdete v tématu [OData: Filtr možností dotazu systému ($filter)](https://go.microsoft.com/fwlink/?LinkId=186972).|  
|`$expand`|Určuje, které související entity jsou vrácené dotazem. Související entity jsou zahrnuty jako informační kanál nebo vložená položka s entitou vrácených dotazem. Následující příklad vrátí objednávky pro zákazníka "ALFKI" spolu s podrobnostmi položky pro jednotlivé objednávky:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> Další informace najdete v tématu [OData: rozbalení možností dotazu systému ($expand)](https://go.microsoft.com/fwlink/?LinkId=186973).|  
|`$select`|Určuje projekci, která definuje vlastnosti entity jsou vráceny v projekci. Ve výchozím nastavení všechny vlastnosti entity jsou vráceny v informačním kanálu. Následující dotaz vrátí pouze tři vlastnosti `Customer` entity:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> Další informace najdete v tématu [OData: Vyberte možností dotazu systému ($select)](https://go.microsoft.com/fwlink/?LinkID=186076).|  
|`$inlinecount`|Požadavky, že počet entit, které jsou vráceny v informačním kanálu bude zahrnuta v informačním kanálu. Další informace najdete v tématu [OData: systému povolena možnost dotazu Inlinecount ($inlinecount)](https://go.microsoft.com/fwlink/?LinkId=186975).|  
  
## <a name="addressing-relationships"></a>Základní adresování relace  
 Kromě adresování sad entit a instancí entit [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] také umožňuje řešit přidružení, které představují vztahy mezi entitami. Tato funkce musí být schopen vytvořit nebo změnit vztah mezi dvěma instancemi entity, jako je například shipper týkající se daného pořadí v ukázkové databázi Northwind. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] podporuje `$link` operátor konkrétně vyřešit přidružení mezi entitami. Následující identifikátor URI je třeba zadat ve zprávě požadavku HTTP PUT změnit na nový shipper shipper pro zadané pořadí.  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 Další informace najdete v tématu [OData: adresování odkazy mezi položkami](https://go.microsoft.com/fwlink/?LinkId=187351).  
  
## <a name="consuming-the-returned-feed"></a>Využívání vrácené informační kanál  
 Identifikátor URI [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prostředků umožňuje data entity adresu určeného službou. Pokud zadáte identifikátor URI do pole Adresa webového prohlížeče [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu reprezentace požadovaný prostředek se vrátí. Další informace najdete v tématu [WCF Data Services – úvodní příručka](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). I když může být užitečné pro testování, prostředek služby data vrací očekávaná data, produkční data služby, které můžete také vytvářet, aktualizovat a odstranit data jsou obecně přístupné kódem aplikace nebo skriptovacích jazyků na webové stránce webový prohlížeč. Další informace najdete v tématu [použití datové služby v klientské aplikaci](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Otevřít web Data protokolu](https://go.microsoft.com/fwlink/?LinkID=182204)
