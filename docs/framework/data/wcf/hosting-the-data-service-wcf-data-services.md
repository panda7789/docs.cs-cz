---
title: Hostující službu Data (služby WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: d3adf45e0876ae63b111a53461eee9aeee519b5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362847"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Hostující službu Data (služby WCF Data Services)
Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], můžete vytvořit službu, která zveřejňuje data jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu. Tato služba dat je definovaný jako třída, která dědí z <xref:System.Data.Services.DataService%601>. Tato třída poskytuje funkci požadovanou ke zpracování zpráv žádostí, provádění aktualizací na zdroji dat a vygenerování odpovědí na zprávy, podle požadavků [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Datové služby však nelze vytvořit vazbu k a naslouchání soketu sítě pro příchozí požadavky HTTP. Tato funkce vyžaduje službu data využívá hostitelská komponenta.  
  
 Hostitel služby dat provádí tyto úlohy jménem službu data:  
  
-   Čeká na požadavky a směruje tyto požadavky na službu data.  
  
-   Vytvoří instanci služby dat pro každý požadavek.  
  
-   Požadavky, že služba data zpracovat příchozí žádosti.  
  
-   Odešle odpověď jménem službu data.  
  
 Pro zjednodušení hostování datové služby, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] slouží k integraci s Windows Communication Foundation (WCF). Služba data poskytuje výchozí implementaci WCF, který slouží jako hostitel služby data v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace. Proto je možné hostovat datové služby v jednom z následujících způsobů:  
  
-   V [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.  
  
-   Ve spravované aplikaci, která podporuje samoobslužné hostované služby WCF.  
  
-   V některých dalších vlastních dat hostitele služby.  
  
## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Hostitelská služba dat v aplikaci ASP.NET  
 Při použití **přidat novou položku** dialogové okno v sadě Visual Studio k definování datové služby v aplikaci ASP.NET, nástroj vygeneruje dva nové soubory v projektu. První soubor má `.svc` rozšíření a dá pokyn modulu runtime WCF, jak vytvořit instanci službu data. Následuje příklad tohoto souboru pro službu Northwind ukázková data vytvořit při dokončení [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 Tato direktiva informuje aplikace pro vytvoření hostitele služby pro třídu s názvem dat služby pomocí <xref:System.Data.Services.DataServiceHostFactory> třídy.  
  
 Na stránce kódu pro `.svc` soubor obsahuje třídu, která je implementace služby data samostatně, který je definován následujícím způsobem pro službu Northwind ukázková data:  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 Protože chová se jako služby WCF data service, službu data se integruje s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a dodržuje programovací model WCF Web. Další informace najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) a [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).  
  
## <a name="self-hosted-wcf-services"></a>Služby WCF s vlastním hostováním  
 Vzhledem k tomu, že její součástí jsou WCF implementaci [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporovat samoobslužné hostování datové služby jako služby WCF. Služba může být v jednom vlastním hostováním [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace, jako je například aplikace konzoly. <xref:System.Data.Services.DataServiceHost> Třídy, která dědí z <xref:System.ServiceModel.Web.WebServiceHost>, se používá k vytvoření instance služby data na konkrétní adrese.  
  
 Vlastní hostování slouží pro vývoj a testování vzhledem k tomu, že ho můžete usnadňují nasazení a řešení potíží s službu. Tento druh hostování však neposkytuje pokročilé funkce pro správu a hostování poskytované [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] nebo internetové informační služby (IIS). Další informace najdete v tématu [hostování ve spravované aplikaci](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
## <a name="defining-a-custom-data-service-host"></a>Definování vlastních dat hostitele služby  
 V případech, kde je příliš omezující implementace hostitele WCF můžete také definovat vlastní hostitele pro datové služby. Všechny třídy, která implementuje <xref:System.Data.Services.IDataServiceHost> rozhraní slouží jako hostitel sítě pro datové služby. Vlastní hostitel musí implementovat <xref:System.Data.Services.IDataServiceHost> rozhraní a být schopna zpracovávat následující základní zodpovědnosti hostitele data služeb:  
  
-   Zadejte službu data s kořenovou cestou za službu.  
  
-   Zpracovat informace o hlavičky požadavku a odpovědi na příslušné <xref:System.Data.Services.IDataServiceHost> implementaci prvku.  
  
-   Zpracování výjimek vyvolaných službu data.  
  
-   Ověření parametrů v řetězci dotazu.  
  
## <a name="see-also"></a>Viz také  
 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Vystavení dat jako služby](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)  
 [Konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
