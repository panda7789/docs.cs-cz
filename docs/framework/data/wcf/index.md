---
title: "Datové služby WCF 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5b27a51dcec17f72b86e77a7ee2ab773aec1dc3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-data-services-45"></a>Datové služby WCF 4.5
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)](dříve označované jako "ADO.NET Data Services") je součástí rozhraní .NET Framework, který umožňuje vytvářet služby, které používají [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] vystavení a spotřebování data prostřednictvím webu nebo intranetu pomocí sémantika [representational stavu Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919). [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]zpřístupní data jako prostředky, které jsou adresovat pomocí identifikátory URI. Data se získat přístup a změnit pomocí standardních operací protokolu HTTP z GET, PUT, POST a odstranění. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]používá pravidla vztah entit [datového modelu Entity](../../../../docs/framework/data/adonet/entity-data-model.md) vystavit prostředky jako sady entit, které jsou spojené přidružení.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]používá [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol pro adresování a aktualizaci prostředky. Tímto způsobem můžete přistupovat z libovolného klienta, který podporuje tyto služby [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]můžete k vyžádání a zapisovat data k prostředkům pomocí známých přenos formáty: Atom, sadu standardy výměna a aktualizace dat jako soubor XML a JavaScript Object Notation (JSON) formátu exchange založený na textu dat, který je hojně používá v aplikaci AJAX.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]můžou zpřístupnit data, která pochází z různých zdrojů jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály. Nástroje sady Visual Studio vytvářet usnadňují [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby pomocí datový model ADO.NET Entity Framework. Můžete také vytvořit [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály na základě třídy společných language runtime (CLR) a data i pozdní vazbou nebo netypové.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]také obsahuje sadu klientské knihovny, jednu pro obecné klientské aplikace rozhraní .NET Framework a druhou speciálně pro aplikace programu Silverlight. Tyto knihovny klienta poskytují programovací model na základě objektů při přístupu [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu z prostředích, jako je rozhraní .NET Framework a program Silverlight.  
  
## <a name="where-should-i-start"></a>Kde mám začít?  
 V závislosti na vašem zájmu, zvažte Začínáme s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] v jednom z následujících témat.  
  
 Chcete rovnou...  
 -   [Rychlý start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [Rychlý start Silverlight](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [Rychlý start Silverlight pro vývoj pro Windows Phone](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 Právě ukázat nějaký kód...  
 -   [Rychlý start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [Postupy: Provádění dotazů v datové službě](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [Postupy: Vytvoření vazby dat na elementy Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 Chci vědět více o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]...  
 -   [Dokument White Paper: Úvod OData](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Otevřít web Data protokolu](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [OData: SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [OData: Nejčastější dotazy](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 Chci videí, některé...  
 -   [Průvodce začátečníka služby WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [Videa vývojáře služeb WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [OData: Vývojáři webové stránky](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 Chcete vidět začátku do konce ukázky  
 -   [Ukázky dokumentace na MSDN ukázky Galerie služeb WCF Data Services](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [Další WCF Data Services ukázek v Galerii ukázek webu MSDN](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [OData: SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 Jak zajistíte jejich integraci se sadou Visual Studio?  
 -   [Generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [Vytvoření datové služby](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [Zprostředkovatel Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 Co můžete dělat s ní?  
 -   [Přehled](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [Dokument White Paper: Úvod OData](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Scénáře aplikací](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 Chci používat Silverlight...  
 -   [Rychlý start Silverlight](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [Začínáme s programem Silverlight](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 Chcete vytvořit aplikaci pro Windows Phone...  
 -   [Rychlý start Silverlight pro vývoj pro Windows Phone](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [Klient Open Data Protocol (OData) pro Windows Phone](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 Chcete použít LINQ...  
 -   [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [Aspekty LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [Postupy: Provádění dotazů v datové službě](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 Potřebuji některé další informace...  
 -   [Blog týmu služby WCF Data](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [Prostředky](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [Středisku pro vývojáře WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [Otevřít web Data protokolu](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 Poskytuje přehled funkcí a funkcí, které jsou k dispozici v [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [Co je nového ve službě WCF Data Services](http://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 Popisuje nové funkce [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] a podporu pro nové [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkce.  
  
 [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 Popisuje, jak vystavení a spotřebování [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 Popisuje, jak vytvořit a nakonfigurovat službu data, která zveřejňuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály.  
  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 Popisuje, jak pomocí klientské knihovny využívat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály z klientské aplikace rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 [Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919)
