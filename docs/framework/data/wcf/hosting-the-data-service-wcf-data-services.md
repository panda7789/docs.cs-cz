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
ms.openlocfilehash: ea60ac132fdd94d4e3a3676891964070b7150857
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780268"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Hostování datové služby (WCF Data Services)
Pomocí WCF Data Services můžete vytvořit službu, která zpřístupňuje data jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informační kanál. Tato datová služba je definována jako třída, která dědí z <xref:System.Data.Services.DataService%601>. Tato třída poskytuje funkce potřebné ke zpracování zpráv požadavků, provádění aktualizací proti zdroji dat a generování zpráv odpovědí podle požadavků OData. Datová služba ale nemůže navazovat a naslouchat síťovému soketu pro příchozí požadavky HTTP. Pro tuto požadovanou funkci datová služba spoléhá na komponentu hostování.

 Hostitel datové služby provádí následující úkoly jménem datové služby:

- Naslouchá žádostem a směruje tyto požadavky na datovou službu.

- Vytvoří instanci datové služby pro každý požadavek.

- Požaduje, aby datová služba zpracovala příchozí požadavek.

- Odešle odpověď jménem datové služby.

 Aby bylo možné zjednodušit hostování datové služby, WCF Data Services je navržena pro integraci s Windows Communication Foundation (WCF). Datová služba poskytuje výchozí implementaci služby WCF, která slouží jako hostitel datové služby v aplikaci ASP.NET. Proto můžete hostovat datovou službu jedním z následujících způsobů:

- V aplikaci ASP.NET.

- Ve spravované aplikaci, která podporuje samoobslužně hostované služby WCF.

- V některém jiném vlastním hostiteli datové služby.

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Hostování datové služby v aplikaci ASP.NET

Při použití dialogového okna **Přidat novou položku** v aplikaci Visual Studio 2015 k definování datové služby v aplikaci ASP.NET generuje nástroj v projektu dva nové soubory. První soubor má `.svc` rozšíření a instruuje modul runtime WCF, jak vytvořit instanci datové služby. Následuje příklad tohoto souboru pro ukázkovou datovou službu Northwind vytvořenou po dokončení [rychlého](quickstart-wcf-data-services.md)startu:

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 Tato direktiva oznamuje aplikaci, aby vytvořila hostitele služby pro třídu pojmenované datové služby pomocí <xref:System.Data.Services.DataServiceHostFactory> třídy.

 Stránka s kódem na pozadí pro `.svc` soubor obsahuje třídu, která je implementací samotné datové služby, která je definována následujícím způsobem pro ukázkovou datovou službu Northwind:

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 Vzhledem k tomu, že se datová služba chová jako služba WCF, datová služba se integruje s ASP.NET a sleduje model webového programování WCF. Další informace najdete v tématu model programování [služeb WCF a ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) a [WCF web http](../../wcf/feature-details/wcf-web-http-programming-model.md).

## <a name="self-hosted-wcf-services"></a>Samoobslužné služby WCF
 Protože zahrnuje implementaci WCF, WCF Data Services podporu samoobslužného hostování datové služby jako služby WCF. Služba může být samoobslužně hostována v libovolné .NET Framework aplikaci, jako je například Konzolová aplikace. Třída, která dědí z <xref:System.ServiceModel.Web.WebServiceHost>, slouží k vytvoření instance datové služby na konkrétní adrese. <xref:System.Data.Services.DataServiceHost>

 Samoobslužné hostování lze použít pro vývoj a testování, protože může usnadnit jeho nasazení a odstraňování potíží. Tento druh hostování ale neposkytuje pokročilé funkce pro hostování a správu, které poskytuje ASP.NET nebo Internetová informační služba (IIS). Další informace najdete v tématu [hostování ve spravované aplikaci](../../wcf/feature-details/hosting-in-a-managed-application.md).

## <a name="defining-a-custom-data-service-host"></a>Definování vlastního hostitele datové služby
 V případech, kdy je implementace hostitele WCF příliš omezující, můžete také definovat vlastního hostitele pro datovou službu. Libovolná třída, <xref:System.Data.Services.IDataServiceHost> která implementuje rozhraní, může být použita jako síťový hostitel pro datovou službu. Vlastní hostitel musí implementovat <xref:System.Data.Services.IDataServiceHost> rozhraní a být schopný zvládnout následující základní zodpovědnosti hostitele datové služby:

- Zadejte datovou službu s kořenovou cestou služby.

- Zpracujte informace hlavičky žádosti a odpovědi příslušné <xref:System.Data.Services.IDataServiceHost> implementaci člena.

- Zpracování výjimek vyvolaných datovou službou.

- Ověřte parametry v řetězci dotazu.

## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Vystavení dat jako služby](exposing-your-data-as-a-service-wcf-data-services.md)
- [Konfigurace datové služby](configuring-the-data-service-wcf-data-services.md)
