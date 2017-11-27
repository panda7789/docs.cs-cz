---
title: "Přehled služby WCF Data Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3dec2bb71a6e36f7106b29f52504ff5f6a168b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-data-services-overview"></a>Přehled služby WCF Data Services
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umožňuje vytváření a využití služeb dat pro Web nebo intranetu pomocí [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Umožňuje vystavit data jako prostředky, které jsou adresovat pomocí identifikátory URI. To umožňuje přístup a změny dat pomocí sémantiky representational stavu transfer (REST), konkrétně standardních operací protokolu HTTP z GET, PUT, POST a odstranění. Toto téma obsahuje přehled vzory a postupy definované [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a také zařízení poskytovaných [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] využívat výhod [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] v aplikacích založených na rozhraní .NET Framework.  
  
## <a name="address-data-as-resources"></a>Data adres jako prostředky  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]zpřístupní data jako prostředky, které jsou adresovat pomocí identifikátory URI. Cesty prostředku jsou vytvořeným v závislosti na vztah entit konvence datového modelu Entity. V tomto modelu entity představují provozní jednotky dat v doméně aplikace, jako je například zákazníky, objednávky, položky a produkty. Další informace najdete v tématu [datového modelu Entity](../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 V [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], adresa entity prostředky jako sadu entit, který obsahuje instance typy entit. Například identifikátor URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` vrátí všechny objednávky z `Northwind` služba dat, která se vztahují k zákazník s `CustomerID` hodnotu`ALFKI.`  
  
 Výrazy dotazů umožňují provádět operace tradiční dotaz na prostředky, jako je například filtrování, řazení a stránkování. Například identifikátor URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` filtry prostředky vrátit pouze příkazy se nákladní náklady více než 50 $. Další informace najdete v tématu [přístup k prostředkům služby Data](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Vzájemná spolupráce Data Access  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]staví na standardní internetové protokoly, aby datové služby umožňuje vzájemnou spolupráci s aplikacemi, které nepoužívají rozhraní .NET Framework. Protože můžete používat standardní identifikátory URI k datům adresu, přístup k vaší aplikace a data změny pomocí sémantiky representational stavu transfer (REST), konkrétně standardních operací protokolu HTTP z GET, PUT, POST a odstranění. To umožňuje přístup k těmto službám z jakékoli klienta, který lze analyzovat a přístup k datům, která se přenášejí pomocí standardních protokolů HTTP.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definuje sadu rozšíření pro publikování protokol Atom (AtomPub). Požadavky a odpovědi HTTP podporuje více než jeden formát dat pro různé platformy a klientské aplikace. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Kanálu může představovat data v Atom, JavaScript Object Notation (JSON) a jako prostý XML. Výchozí formát při Atom formát informačního kanálu je určen v hlavičce požadavku HTTP. Další informace najdete v tématu [OData: formát Atom](http://go.microsoft.com/fwlink/?LinkID=185794) a [OData: formát JSON](http://go.microsoft.com/fwlink/?LinkID=185795).  
  
 Při publikování dat jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] závisí na jiné existující Internet zařízení pro tyto činnosti jako ukládání do mezipaměti a ověřování. K tomu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] se integruje s existující hostování aplikace a služby, jako je ASP.NET, Windows Communication Foundation (WCF) a Internetové informační služby (IIS).  
  
## <a name="storage-independence"></a>Nezávislost úložiště  
 I když prostředky jsou řešit podle model vztah entit [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vystavit [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bez ohledu na podkladový zdroj dat informační kanály. Po [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] přijme požadavek HTTP pro prostředek, který identifikuje identifikátor URI, je deserializovat požadavek a je předán reprezentace této žádosti [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zprostředkovatele. Tento zprostředkovatel překládá žádosti ve formátu specifická pro zdroj dat a zpracuje požadavek na podkladový zdroj dat. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nezávislost úložiště dosahuje oddělení konceptuální model, který řeší prostředky podle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] z konkrétní schématu zdroje dat, základní.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]se integruje s vám umožní vytvořit datové služby, které zveřejňují relačních dat rozhraní ADO.NET Entity Framework. Nástroje modelu Entity Data Model slouží k vytvoření datového modelu, který obsahuje adresovatelné prostředky jako entity a současně definovat mapování mezi tohoto modelu a tabulek v podkladové databázi. Další informace najdete v tématu [zprostředkovatele Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]také můžete vytvořit datové služby, které vystavují žádné datové struktury, které vracejí implementace <xref:System.Linq.IQueryable%601> rozhraní. Umožňuje vytvořit datové služby, které zveřejňují data z typů rozhraní .NET Framework. Vytvoření, aktualizace a odstranění operace jsou podporované, když je také implementovat <xref:System.Data.Services.IUpdatable> rozhraní. Další informace najdete v tématu [reflexe zprostředkovatele](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).  
  
 Pro ilustraci toho, jak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integruje s tyto zprostředkovatele dat, podívejte se na diagram architektury později v tomto tématu.  
  
## <a name="custom-business-logic"></a>Vlastní obchodní logiky  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje snadno přidat vlastní obchodní logiku ke službě data prostřednictvím operací služby a sběrače. Operace služby jsou metody definované na serveru, které jsou adresovat pomocí identifikátory URI ve stejném tvaru jako datové prostředky. Operace služby můžete také použít syntaxe výrazu dotazu filtru, pořadí a data stránky vrácený operace. Například identifikátor URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` představuje volání operace služby s názvem `GetOrdersByCity` na službě Northwind data, která vrátí objednávky zákazníků z Londýna, stránkovaného s výsledky seřazené podle `OrderDate`. Další informace najdete v tématu [operací služby](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Sběrače povolit vlastní logiky aplikace integraci při zpracování požadavku nebo odpovědi zprávy službou data. Sběrače jsou volány při dotazu, vložení, aktualizace nebo odstranění akce proběhne sadu zadané entity. Interceptoru pak může změnit data, vynucování zásad autorizace ani i ukončit operaci. Interceptoru metody musí být explicitně zaregistrován pro danou entitu sadu, který je zveřejněný prostřednictvím datové služby. Další informace najdete v tématu [sběrače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Knihovny klienta  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definuje sadu uniform vzory pro interakci s datové služby. To představuje příležitost k vytvoření opakovaně použitelné součásti, které jsou založeny na těchto služeb, jako je například klientské knihovny, které usnadňují využívat datové služby.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zahrnuje klientské knihovny pro obě aplikace založené na rozhraní .NET Framework a založená na technologii Silverlight klienta. Tyto knihovny klienta umožňují používat datové služby pomocí rozhraní .NET Framework objekty. Také podporují dotazy založené na objekt a dotazů LINQ načítání souvisejících objektů, změňte sledování a řešení identity. Další informace najdete v tématu [WCF Data Services klientské knihovny](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
 Kromě [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] knihovny klienta zahrnovala s rozhraním .NET Framework a pomocí programu Silverlight, existují další klientské knihovny, které vám umožní využívat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu v klientských aplikacích, jako jsou například aplikace Java, PHP a AJAX. Další informace najdete v tématu [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Přehled architektury  
 Následující diagram znázorňuje [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] architektura pro vystavení [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačních kanálů a použití těchto kanálů v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-povolit klientské knihovny:  
  
 ![Diagram architektury datových služeb WCF](../../../../docs/framework/data/wcf/media/astoriaservicearch.gif "AstoriaServiceArch")  
  
## <a name="see-also"></a>Viz také  
 [Datové služby WCF 4.5](../../../../docs/framework/data/wcf/index.md)  
 [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Definování datových služeb WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Přístup k službě dat (služby WCF Data Services)](http://msdn.microsoft.com/en-us/1e54a2b9-2ec6-4002-b8f8-c1d8df37c350)  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919)
