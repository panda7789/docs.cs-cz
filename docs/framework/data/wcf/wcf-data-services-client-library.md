---
title: Klientská knihovna pro WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 95ca3ab8768b59b52640cfd17d230a544a8b2052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365511"
---
# <a name="wcf-data-services-client-library"></a>Klientská knihovna pro WCF Data Services
Všechny aplikace mohou komunikovat s [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]-založené služba dat v případě, že může posílat proces a požadavek HTTP [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu, vrátí datové služby. Tato interoperabilita umožňuje přístup k [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby z široké povoleno rozsahu webových aplikací. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zahrnuje knihovny klienta, které poskytují bohatší programovací prostředí spotřebuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály v rozhraní .NET Framework nebo aplikace programu Silverlight.  
  
 Jsou dvě hlavní třídy klientské knihovny <xref:System.Data.Services.Client.DataServiceContext> třídy a <xref:System.Data.Services.Client.DataServiceQuery%601> třídy. <xref:System.Data.Services.Client.DataServiceContext> Třída zapouzdří operace, které jsou podporovány službě zadaná data. I když [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jsou bezstavové služby, není kontextu. Proto můžete použít <xref:System.Data.Services.Client.DataServiceContext> třídy pro uchování stavu na straně klienta mezi interakce s službu data za účelem podpory funkcí, jako například Správa změn. Tato třída také spravuje identit a sleduje změny. <xref:System.Data.Services.Client.DataServiceQuery%601> Třída reprezentuje dotazu oproti sadě konkrétní entity.  
  
 Tato část popisuje postup používání klientské knihovny pro přístup a měnit data z klientské aplikace rozhraní .NET Framework. Další informace o tom, jak používat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna pro s aplikací založená na technologii Silverlight, najdete v části [datové služby WCF (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016). Ostatní klientské knihovny jsou k dispozici které umožňují využívat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu v jiné typy aplikací. Další informace najdete v tématu [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 Popisuje, jak generovat klientské knihovny a třídy klienta dat služby, které jsou založeny na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály.  
  
 [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 Popisuje, jak dotazovat služby data z aplikace založené na rozhraní .NET Framework pomocí knihovny klienta.  
  
 [Načtení odloženého obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 Popisuje, jak načíst dalšího obsahu, které nejsou zahrnuty v odpovědi počátečního dotazu.  
  
 [Aktualizace datové služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 Popisuje, jak vytvářet, upravovat a odstraňovat entity a vztahy s použitím knihovny klienta.  
  
 [Asynchronní operace](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 Popisuje poskytované systémem klientské knihovny pro práci se službou dat v asynchronním režimu.  
  
 [Operace dávkování](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 Popisuje, jak k odesílání více požadavků na službu data v jedné dávce pomocí knihovny klienta.  
  
 [Vazba dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 Popisuje postup vytvoření vazby ovládacích prvků k [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu vrácený datové služby.  
  
 [Operace volání služeb](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 Popisuje postup používání klientské knihovny pro volání operací služby.  
  
 [Správa kontextu datové služby](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 Popisuje možnosti pro správu chování klientské knihovny.  
  
 [Práce s binárními daty](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 Popisuje, jak získávat přístup a měnit binární data vrácená službou data jako datový proud.  
  
## <a name="see-also"></a>Viz také  
 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
