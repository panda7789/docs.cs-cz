---
title: Přístup k prostředkům služby dat (služby WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: f1af991d7db9bfeeb0737e65a0517629f359f4a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365326"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>Přístup k prostředkům služby dat (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] vystavit data jako informační kanál s prostředky, které jsou adresovat pomocí identifikátory URI. Tyto prostředky jsou reprezentované podle pravidla vztah entit [datového modelu Entity](../../../../docs/framework/data/adonet/entity-data-model.md). V tomto modelu entity představují provozní jednotky dat, které jsou datové typy v doméně aplikace, jako je například zákazníky, objednávky, položky a produkty. Entity data se získat přístup a změnit pomocí sémantiky representational stavu transfer (REST), konkrétně standardní HTTP příkazy GET, PUT, POST a DELETE.  
  
## <a name="addressing-resources"></a>Přidělování prostředků  
 V [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], adresa žádná data vystavené datového modelu s použitím identifikátoru URI. Například následující identifikátor URI vrací informačního kanálu, který je zákazníkům sady entit, který obsahuje položky pro všechny instance typu entity zákazníka:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 Entity mít speciální vlastnosti názvem klíče entit. Klíč entity slouží k jednoznačné identifikaci jedné entity v sadu entit. To umožňuje vyřešit konkrétní instanci typu entity v sadě entit. Například následující identifikátor URI vrátí záznam pro konkrétní instanci typu entity zákazníka, který má hodnotu klíče `ALFKI`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 Jednoduché a komplexní vlastnosti entity instance lze také jednotlivě řešit. Například následující identifikátor URI vrací elementu XML, který obsahuje `ContactName` hodnota vlastnosti pro konkrétního zákazníka:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 Pokud zahrnete `$value` koncového bodu v předchozí identifikátor URI, je vrácena pouze hodnota primitivní vlastnost ve zprávě s odpovědí. Následující příklad vrátí jenom řetězec "Marie Anders" bez XML element:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 Relace mezi entitami jsou definovány v datovém modelu přidružení. Tato přidružení umožňují adres entit v relaci s použitím navigační vlastnosti instance entity. Navigační vlastnost může vrátit buď jedné související entity, v případě relaci n: 1 nebo u sady entit v relaci, v případě vztah jeden mnoho. Například následující identifikátor URI vrací informačního kanálu, který je sada všechny příkazy, které se vztahují na konkrétního zákazníka:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 Vztahy, které jsou obvykle obousměrný, jsou reprezentovány pár navigační vlastnosti. Následující identifikátor URI jako zpětného relace ukazuje předchozí příklad, vrátí odkaz na entitu zákazníka, do které patří konkrétní entitu pořadí:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Můžete se také pro adresování prostředků na základě výsledků dotazu výrazů. Díky tomu je možné filtrovat sady prostředky v závislosti na vyhodnocený výraz. Například následující identifikátor URI filtry prostředky vrátit pouze objednávky zadané zákazníka, které byly součástí od 22. září 1997:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 Další informace najdete v tématu [OData: identifikátor URI konvence](http://go.microsoft.com/fwlink/?LinkId=185564).  
  
## <a name="system-query-options"></a>Možnosti dotazu systému  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] definuje sadu možností dotazu systému, které můžete použít k provádění operací tradiční dotaz na prostředky, jako je například filtrování, řazení a stránkování. Například následující identifikátor URI vrací sadu všech `Order` entity, společně s související `Order_Detail` entity, poštovní kódy, které není končit `100`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 Položek v informačním kanálu vrácený jsou také seřazené podle hodnoty vlastnosti MěstoPříjemce objednávky.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje následující [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] možností dotazu systému:  
  
|Možnost dotazu|Popis|  
|------------------|-----------------|  
|`$orderby`|Definuje výchozí pořadí řazení pro entity v vrácený informačního kanálu. Následující dotaz pořadí vrácených zákazníkům kanálu kraj a Město:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> Další informace najdete v tématu [OData: možnost dotazu OrderBy systému ($orderby)](http://go.microsoft.com/fwlink/?LinkId=186968).|  
|`$top`|Určuje počet entit, které chcete zahrnout do vrácený informačního kanálu. Následující příklad Přeskočí prvních 10 zákazníků a vrátí další 10:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Další informace najdete v tématu [OData: možností dotazu systému horní ($top)](http://go.microsoft.com/fwlink/?LinkId=186969).|  
|`$skip`|Určuje počet entit, tak, aby přeskočil předtím, než začnete vrácení entit v informačním kanálu. Následující příklad Přeskočí prvních 10 zákazníků a vrátí další 10:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Další informace najdete v tématu [OData: možností dotazu systému přeskočit ($skip)](http://go.microsoft.com/fwlink/?LinkId=186971).|  
|`$filter`|Určuje výraz, který filtry, vrátí entity v informačním kanálu závislosti na konkrétních kritériích. Tuto možnost dotazu podporuje sadu logické relační operátory, aritmetické operátory a předdefinovaný dotaz funkce, které se používají k vyhodnocení výrazu filtru. Následující příklad vrací všechny objednávky poštovní kódy, které není končit 100:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> Další informace najdete v tématu [OData: možnost dotazu Filter systému ($filter)](http://go.microsoft.com/fwlink/?LinkId=186972).|  
|`$expand`|Určuje, které entit v relaci jsou vrácených dotazem. Entit v relaci jsou zahrnuty jako informačního kanálu nebo vložené položky s entitou vrácených dotazem. Následující příklad vrátí pořadí pro zákazníka "ALFKI" spolu s podrobnosti o položkách pro každé pořadí:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> Další informace najdete v tématu [OData: rozbalte možností dotazu systému ($expand)](http://go.microsoft.com/fwlink/?LinkId=186973).|  
|`$select`|Určuje projekci, která definuje vlastnosti entity, jsou vráceny v projekci. Ve výchozím nastavení jsou vráceny všechny vlastnosti entity v informačním kanálu. Následující dotaz vrátí jenom tři vlastnosti `Customer` entity:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> Další informace najdete v tématu [OData: Vyberte možností dotazu systému ($select)](http://go.microsoft.com/fwlink/?LinkID=186076).|  
|`$inlinecount`|Požadavky, že počet entit, vrátí se v informačním kanálu být součástí informačního kanálu. Další informace najdete v tématu [OData: možnost dotazu Inlinecount systému ($inlinecount)](http://go.microsoft.com/fwlink/?LinkId=186975).|  
  
## <a name="addressing-relationships"></a>Adresování relace  
 Kromě adresování sad entit a instancí entit [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] taky umožňuje adres přidružení, které představují vztahy mezi entitami. Tato funkce je potřeba mít k vytvoření nebo změně vztah mezi dvě instance entity, jako je například odesílatel, která souvisí s danou pořadí v ukázková databáze Northwind. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] podporuje `$link` operátor konkrétně vyřešit přidružení mezi entitami. Následující identifikátor URI je třeba zadat ve zprávě požadavku HTTP PUT změnit na nový odesílatel odesílatel pro zadané pořadí.  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 Další informace najdete v tématu [OData: adresování propojení mezi položky](http://go.microsoft.com/fwlink/?LinkId=187351).  
  
## <a name="consuming-the-returned-feed"></a>Využívání vrácený informačního kanálu  
 Identifikátor URI [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prostředků umožňuje adresu data entity zveřejněné službou. Když zadejte identifikátor URI do adresního řádku webového prohlížeče, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu reprezentace požadovaný prostředek je vrácen. Další informace najdete v tématu [WCF Data Services rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). I když webový prohlížeč může být užitečné pro testování, zdroj dat služby vrací očekávaná data, provozní data služby, které mohou také vytvářet, aktualizovat a odstranit data jsou obecně dostupné přes kód aplikace nebo skriptovací jazyky na webové stránce. Další informace najdete v tématu [pomocí datové služby v aplikaci klienta](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Otevřít web Data protokolu](http://go.microsoft.com/fwlink/?LinkID=182204)
