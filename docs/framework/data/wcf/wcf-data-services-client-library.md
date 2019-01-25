---
title: Klientské knihovny WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 9af19f2ef552c5871d488c968368a9192bae9edb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656216"
---
# <a name="wcf-data-services-client-library"></a>Klientské knihovny WCF Data Services
Všechny aplikace mohou komunikovat s [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]– na základě dat služby, pokud může odeslat požadavek HTTP a procesu služby [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu, vrací datovou službu. Tato spolupráce umožňuje získat přístup k [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby z široké povolené rozsahu webových aplikací. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsahuje klientské knihovny, které poskytují pohodlnější a pestřejší prostředí programovací spotřebuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály z rozhraní .NET Framework nebo aplikací založené na technologii Silverlight.  
  
 Dva hlavní třídy klientské knihovny jsou <xref:System.Data.Services.Client.DataServiceContext> třídy a <xref:System.Data.Services.Client.DataServiceQuery%601> třídy. <xref:System.Data.Services.Client.DataServiceContext> Třída zapouzdří operace, které jsou podporovány pro zadané datové služby. I když [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby jsou bezstavové, kontext je. Proto můžete použít <xref:System.Data.Services.Client.DataServiceContext> třídy pro uchování stavu na straně klienta mezi interakcemi s datové služby za účelem podpory funkcí, jako je správa změn. Tato třída také spravuje identity a sleduje změny. <xref:System.Data.Services.Client.DataServiceQuery%601> Třída reprezentuje dotazu na sadu konkrétní entity.  
  
 Tato část popisuje, jak pomocí klientských knihoven pro přístup a změnu dat z klientské aplikace rozhraní .NET Framework. Další informace o tom, jak používat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny s aplikací založené na technologii Silverlight, naleznete v tématu [služeb WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=186016). Ostatní klientské knihovny jsou k dispozici, díky kterým můžete využívat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu do jiných typů aplikací. Další informace najdete v tématu [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 Popisuje, jak generovat klientskou knihovnu a tříd klientské datové služby, které jsou založeny na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály.  
  
 [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 Popisuje, jak provádět dotazy pomocí klientské knihovny datové služby z aplikace založené na rozhraní .NET Framework.  
  
 [Načtení odloženého obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 Popisuje, jak načíst další obsah, které nejsou zahrnuty v odpovědi na počáteční dotaz.  
  
 [Aktualizace datové služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 Popisuje postup vytvoření, úprava a odstranění entit a vztahů s využitím klientské knihovny.  
  
 [Asynchronní operace](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 Popisuje zařízení poskytovaných klientských knihoven pro práci s datovou službu v asynchronním režimu.  
  
 [Operace dávkování](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 Popisuje, jak odesílat více požadavků do datové služby v jedné dávce pomocí klientské knihovny.  
  
 [Vazba dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 Popisuje, jak svázat ovládací prvky [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu vrácené službou data.  
  
 [Operace volání služeb](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 Popisuje, jak použít knihovnu klienta k volání operací služby.  
  
 [Správa kontextu datové služby](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 Popisuje možnosti pro správu chování klientské knihovny.  
  
 [Práce s binárními daty](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 Popisuje, jak získávat přístup a měnit binárních dat vrácených datovou službou jako datový proud.  
  
## <a name="see-also"></a>Viz také:
- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
