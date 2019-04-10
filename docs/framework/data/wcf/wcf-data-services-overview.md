---
title: Přehled služby WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: ca52b725f5fad4b591b95bf6a6dd778c7a72d235
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202037"
---
# <a name="wcf-data-services-overview"></a>Přehled služby WCF Data Services
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umožňuje vytváření a spotřebě datových služeb webu nebo intranetu pomocí [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] umožňuje zpřístupnění vašich dat ve formě prostředky, které jsou adresovat pomocí identifikátorů URI. Umožňuje získat přístup k a data změny pomocí sémantiky representational state Transfer (REST), konkrétně standardní příkazy HTTP z GET, PUT, POST a odstranění. Toto téma obsahuje přehled vzory a postupy určené [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a také zařízení poskytovaných [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] výhod [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] v aplikacích založených na rozhraní .NET Framework.  
  
## <a name="address-data-as-resources"></a>Data adres jako prostředky  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] uvádí data jako prostředky, které jsou adresovat pomocí identifikátorů URI. Cesty prostředků jsou vytvořeny podle konvence relace entity z modelu Entity Data Model. V tomto modelu entity představují jednotky provozních dat v doméně aplikace, jako je například zákazníky, objednávky, položky a produkty. Další informace najdete v tématu [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 V [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], adresa zdroje entity jako sadu entit, která obsahuje instance typů entit. Například identifikátor URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` vrátí všechny objednávky z `Northwind` datovou službu, která se vztahují k zákazníkovi `CustomerID` hodnotu `ALFKI.`  
  
 Výrazy dotazů umožňují provádět tradiční dotazu operací s prostředky, jako je například filtrování, řazení a stránkování. Například identifikátor URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` vyfiltruje prostředky, které vrátí pouze objednávky s cenou freight z více než 50 USD. Další informace najdete v tématu [přístup k prostředkům datové služby](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Interoperabilní Data Access  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] navazuje na standardních protokolů sítě Internet, aby vzájemná spolupráce s aplikací, které nepoužívají rozhraní .NET Framework datové služby. Vzhledem k tomu můžete použít standardní identifikátory URI adresu dat, vaše aplikace získá přístup k a data změny pomocí sémantiky representational state Transfer (REST), konkrétně standardní příkazy HTTP z GET, PUT, POST a odstranění. Umožňuje získat přístup k těmto službám z jakéhokoli klienta, který můžete analyzovat a přístup k datům, která se přenášejí pomocí standardních protokolů HTTP.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] definuje sadu rozšíření protokolu publikování Atom (AtomPub). Požadavky a odpovědi HTTP podporuje ve více než jeden formát dat tak, aby vyhovovaly různé klientské aplikace a platformy. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Informačního kanálu může představovat data v Atom, zápis JSON (JavaScript Object) a jako prostého jazyka XML. Přestože je výchozí formát Atom, formát informačního kanálu je určen v záhlaví požadavku HTTP. Další informace najdete v tématu [OData: Formát Atom](https://go.microsoft.com/fwlink/?LinkID=185794) a [OData: Formát JSON](https://go.microsoft.com/fwlink/?LinkID=185795).  
  
 Při publikování dat jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] závisí na dalších stávajících zařízení Internetu pro tyto operace jako ukládání do mezipaměti a ověřování. K tomu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integruje do stávající hostování aplikací a služeb, jako je ASP.NET, Windows Communication Foundation (WCF) a Internetové informační služby (IIS).  
  
## <a name="storage-independence"></a>Nezávislost úložiště  
 I když prostředky se tak vyřeší, podle modelu relace entity [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vystavit [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bez ohledu na podkladový zdroj dat se předají. Po [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] přijme požadavek HTTP pro prostředek, který určuje identifikátor URI, je deserializovat požadavek a je předán reprezentace této žádosti [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zprostředkovatele. Tento zprostředkovatel přeloží požadavku ve formátu specifická pro zdroj dat a zpracuje požadavek na podkladový zdroj dat. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] nezávislost úložiště dosahuje oddělením konceptuální model, který adresuje prostředky podle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] z konkrétní schématu podkladového zdroje dat.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] se integruje s ADO.NET Entity Framework umožňuje vytvoření datové služby, která zpřístupňují relační data. Nástroje modelu Entity Data Model můžete vytvořit datový model, který obsahuje adresovatelný prostředky jako entity a současně definovat mapování mezi tohoto modelu a tabulky v podkladové databázi. Další informace najdete v tématu [zprostředkovatele Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] také umožňuje vytvoření datové služby, které zpřístupnit žádné datové struktury, která se vrátila implementace rozhraní <xref:System.Linq.IQueryable%601> rozhraní. To umožňuje vytvoření datové služby, které vystavit data z typy rozhraní .NET Framework. Vytvoření, aktualizace a operace odstranění jsou podporovány, pokud je také implementovat <xref:System.Data.Services.IUpdatable> rozhraní. Další informace najdete v tématu [zprostředkovatel reflexe](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).  
  
 Pro ilustraci toho, jak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integruje s poskytovateli těchto dat zobrazit diagram architektury dále v tomto tématu.  
  
## <a name="custom-business-logic"></a>Vlastní obchodní logiky  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umožňuje snadno přidat vlastní obchodní logiky do datové služby pomocí operace služby a zachycovacích dotazů. Operace služby jsou metody definovány na serveru, které jsou ve stejné podobě jako zdroje dat adresovat pomocí identifikátorů URI. Operace služby můžete také použít syntaxe výrazu dotazu filtr, pořadí a stránku data vrácená rozhraním operace. Například identifikátor URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` představuje volání operace služby s názvem `GetOrdersByCity` na datová služba Northwind, která vrací objednávky, zákazníci z Londýna, s stránkovány výsledky seřazené podle `OrderDate`. Další informace najdete v tématu [operací služby](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Sběrače povolit vlastní aplikační logiku a možné integrovat se službou data při zpracování zprávy požadavku nebo odpovědi. Sběrače jsou volány při dotazu, vložení, aktualizaci nebo akci odstranění proběhne sada zadaná entita. Zachycování pak může změnit data, vynucování zásad autorizace nebo dokonce ukončit operaci. Zachycování metody musí být explicitně registrován pro danou sadou entit, který je zveřejněný prostřednictvím datové služby. Další informace najdete v tématu [sběrače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Klientské knihovny  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] definuje sadu jednotné vzorce pro interakci s datovými službami. To představuje příležitost k vytvoření opakovaně použitelné komponenty, které jsou založeny na tyto služby, například knihoven na straně klienta, které usnadňují využívat datové služby.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsahuje klientské knihovny pro obě založených na rozhraní .NET Framework a Silverlight klientské aplikace. Tyto klientské knihovny umožňují pracovat se službami data s využitím objekty rozhraní .NET Framework. Podporují také dotazy založené na objekt a dotazů LINQ, související objekty, načítání řešení change tracking a rozlišení identity. Další informace najdete v tématu [klientské knihovny WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
 Kromě [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] klientských knihoven, které jsou zahrnuty v rozhraní .NET Framework a Silverlight, existují ostatní klientské knihovny, které vám umožní využívat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu v klientských aplikacích, jako jsou třeba aplikace Java, PHP a AJAX. Další informace najdete v tématu [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Přehled architektury  
 Následující diagram znázorňuje [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] architektury pro vystavení [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály a pomocí těchto kanálů v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-povoleno klientské knihovny:  
  
 ![Snímek obrazovky zobrazující diagram architektury služeb WCF Data Services.](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Viz také:

- [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)
- [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Přístup k prostředkům datové služby (WCF Data Services)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
