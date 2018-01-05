---
title: "Konfigurace služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 857ec77e54d6a55bde1a94fd9fd5758ef7a24309
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-services"></a>Konfigurace služeb
Jakmile určené a implementovat vaše kontrakt služby, jste připraveni ke konfiguraci služby. Toto je, kde definice a přizpůsobení, jak je vystaven služby pro klienty, včetně zadání adresy, kde se nachází, zprávy, který se používá k odesílání a přijímání zpráv a typ zabezpečení, která vyžaduje kódování a přenos.  
  
 Konfigurace použitý zde zahrnuje všechny způsoby, imperativní v kódu nebo pomocí konfiguračního souboru, ve kterém můžete definovat a přizpůsobit různé aspekty služby, například určení jeho adresy koncových bodů, přenosy použít a schémata jeho zabezpečení. V praxi, zápis konfigurace je hlavní část programování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikací.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md)  
 Počínaje [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] se dodává s nový model výchozí konfigurace, který zjednodušuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] požadavky na konfiguraci. Pokud nezadáte žádné [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfigurace pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s výchozí koncové body, vazby a chování.  
  
 [Konfigurace služeb pomocí konfiguračních souborů](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služba je konfigurovatelná pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologie konfigurace. Nejčastěji, jsou přidány elementy XML v souboru Web.config pro stránku Internetové informační služby (IIS), který je hostitelem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Prvky umožňují změnit podrobnosti, např. adresy koncových bodů (skutečná adresami používaný ke komunikaci se službou) na základě počítače podle počítače.  
  
 [Vazby](../../../docs/framework/wcf/bindings.md)  
 Kromě toho [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zahrnuje několik běžných konfigurací poskytované systémem ve formě vazby, které vám umožní rychle vybrat nejzákladnější funkce pro jak klientem a službou komunikovat, jako je například přenosy, zabezpečení a kódování zpráv použít.  
  
 [Koncové body](../../../docs/framework/wcf/endpoints.md)  
 Veškerá komunikace s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby dojde k prostřednictvím *koncové body* služby. Koncové body obsahovat kontrakt, informace o konfiguraci, který je uveden v vazeb a adresy, které označují, kde se služba nebo kde můžete získat informace o službě.  
  
 [Zabezpečení služeb](../../../docs/framework/wcf/securing-services.md)  
 Pomocí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a existující mechanismy zabezpečení, můžete implementovat důvěrnost, integritu, ověřování a autorizace do jakékoli služby. Také můžete auditovat pro zabezpečení úspěchy a selhání.  
  
 [Vytváření interoperabilních služeb WS-I Basic Profile 1.1](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Požadavky na nasazení služby, který je vzájemná spolupráce s služeb a klientů na všechny platformy a operačního systému jsou uvedeny v WS-I Basic Profile 1.1 specifikace.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>Související oddíly  
 [Základní programovací životní cyklus](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [Navrhování a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [Služby hostování](../../../docs/framework/wcf/hosting-services.md)  
  
 [Sestavování klientů](../../../docs/framework/wcf/building-clients.md)  
  
 [Úvod do rozšířitelnosti](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [Správa a diagnostika](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a>Viz také  
 [Základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Koncepční přehled](../../../docs/framework/wcf/conceptual-overview.md)  
 [Podrobnosti o funkcích WCF](../../../docs/framework/wcf/feature-details/index.md)
