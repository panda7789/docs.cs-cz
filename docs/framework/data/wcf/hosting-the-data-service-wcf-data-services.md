---
title: Hostování datové služby (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: e738fa1feebdd91bdb84484340b31e599d7f5f76
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765570"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Hostování datové služby (WCF Data Services)
Pomocí služeb WCF Data Services, můžete vytvořit službu, která zveřejňuje data jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu. Tato služba dat je definován jako třída, která dědí z <xref:System.Data.Services.DataService%601>. Tato třída poskytuje funkci požadovanou ke zpracování zpráv požadavků, provádění aktualizací na zdroji dat a vygenerování zprávy odpovědi, podle požadavků OData. Datové služby však nelze svázat a síťových soketů naslouchat příchozím požadavkům HTTP. Pro tato požadované funkce, která využívá datová služba hostitelská komponenta.

 Hostitele datové služby se provádí tyto úlohy jménem datové služby:

- Čeká na požadavky a směrovat tyto žádosti do datové služby.

- Vytvoří instance služby data pro každý požadavek.

- Požadavky, že datové služby zpracování příchozího požadavku.

- Odešle odpověď jménem datové služby.

 Pro zjednodušení, který je hostitelem datové služby, služeb WCF Data Services slouží k integraci s Windows Communication Foundation (WCF). Data service poskytuje výchozí implementaci WCF, která slouží jako hostitele datové služby v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace. Proto může hostovat datové služby v jednom z následujících způsobů:

- V [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.

- Ve spravované aplikaci, která podporuje v místním prostředí služby WCF.

- V některých jiných vlastního hostitele datové služby.

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Hostující datovou službu v aplikaci ASP.NET

Při použití **přidat novou položku** dialogového okna v sadě Visual Studio 2015 k definování datových služeb v aplikaci ASP.NET, nástroj vygeneruje dva nové soubory v projektu. První soubor musí `.svc` rozšíření a předá instrukci modul runtime WCF na tom, jak vytvořit instanci datové služby. Následuje příklad tohoto souboru pro datová služba Northwind ukázka vytvořit při dokončení [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 Tato direktiva řekne aplikaci vytvořit hostitele služby pro třídu pojmenované datové služby pomocí <xref:System.Data.Services.DataServiceHostFactory> třídy.

 Na stránce použití modelu code-behind pro `.svc` soubor obsahuje třídu, která je implementace data samotné služby, která je definovaná následujícím způsobem pro ukázková datová služba Northwind:

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 Protože datové služby se chová jako služba WCF, datové služby se integruje s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a následuje programovacího modelu WCF Web. Další informace najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) a [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).

## <a name="self-hosted-wcf-services"></a>Služby WCF v místním prostředí
 Protože zahrnuje implementace WCF služby WCF Data Services podporují datové služby jako služba WCF s vlastním hostováním. Služba může být v libovolném v místním prostředí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace, jako je například konzolové aplikace. <xref:System.Data.Services.DataServiceHost> Třída, která dědí z <xref:System.ServiceModel.Web.WebServiceHost>, se používá k vytvoření instance služby data na konkrétní adrese.

 Hostování na vlastním lze použít pro vývoj a testování vzhledem k tomu, že se zjednoduší nasazení a řešení potíží se službou. Tento typ hostování však neposkytuje poskytuje pokročilé funkce pro hostování a správu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] nebo internetové informační služby (IIS). Další informace najdete v tématu [hostování ve spravované aplikaci](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).

## <a name="defining-a-custom-data-service-host"></a>Definování hostitele vlastní datové služby
 V případech, kde je příliš omezující implementace hostitele WCF můžete také definovat vlastní hostitele datové služby. Všechny třídy, která implementuje <xref:System.Data.Services.IDataServiceHost> rozhraní může sloužit jako síťovým hostitelem datové služby. Musí implementovat vlastního hostitele <xref:System.Data.Services.IDataServiceHost> rozhraní a být schopná zpracovat tyto základní povinnosti hostitele datové služby:

- Zadejte datové služby s kořenovou cestou za služby.

- Zpracovat informace hlavičky požadavku a odpovědi na příslušné <xref:System.Data.Services.IDataServiceHost> implementace členu.

- Zpracování výjimek vyvolaných datové služby.

- Ověření parametrů v řetězci dotazu.

## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Vystavení dat jako služby](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [Konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
