---
title: Konfigurace služeb WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 81727adbf985986a71cc9f9e2d42a1de0cb1fd76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156504"
---
# <a name="configuring-wcf-services"></a>Konfigurace služeb WCF

Jakmile máte navrženy a implementovány servisní smlouvy, jste připraveni ke konfiguraci služby. To je, kde definování a přizpůsobení, jak je vaše služba zveřejněné klientům, včetně zadání adresy, kde je možné ji najít, přenos a kódování zpráv, které používá k odesílání a přijímání zpráv a typ zabezpečení, které vyžaduje.  
  
 Konfigurace použitý zde zahrnuje všechny způsoby, jak, imperativně v kódu nebo pomocí konfiguračního souboru, ve kterém můžete definovat a přizpůsobení různé aspekty služby, jako je například zadání adresy koncového bodu, přenosy použít a schémata jeho zabezpečení. V praxi, zápis konfigurace je velkou část programování WCF aplikací.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md)  
 Počínaje [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF se dodává s novou výchozí konfiguraci modelu, která zjednodušuje požadavky na konfiguraci WCF. Pokud nezadáte žádnou konfiguraci WCF pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s výchozí koncové body, vazby a chování.  
  
 [Konfigurace služeb pomocí konfiguračních souborů](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 Služba Windows Communication Foundation (WCF) se dají konfigurovat pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologie konfigurace. Nejčastěji jsou přidány elementy XML v souboru Web.config pro web Internetové informační služby (IIS), který je hostitelem služby WCF. Prvky umožňují změnit podrobnosti, jako jsou adresy koncových bodů (skutečné adresy používaný ke komunikaci se službou service) pro počítače podle počítače.  
  
 [Vazby](../../../docs/framework/wcf/bindings.md)  
 Kromě toho WCF obsahuje několik běžných konfigurací poskytované systémem ve formě vazby, které umožňují rychle vybrat základní funkce pro komunikaci klienta a služby, jako jsou přenosy, zabezpečení a zprávy použít kódování.  
  
 [Koncové body](../../../docs/framework/wcf/endpoints.md)  
 Vyvolá se veškerá komunikace se službou WCF přes *koncové body* služby. Koncové body obsahovat kontrakt, informace o konfiguraci, která je zadána ve vazbách a adresy, které označují, kam chcete najít službu nebo kde můžete získat informace o službě.  
  
 [Zabezpečení služeb](../../../docs/framework/wcf/securing-services.md)  
 Pomocí technologie WCF a stávající mechanismy zabezpečení, můžete implementovat důvěrnost, integritu, ověřování a autorizace na libovolnou službu. Také můžete auditovat zabezpečení úspěchy a selhání.  
  
 [Vytváření interoperabilních služeb WS-I Basic Profile 1.1](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Požadavky na nasazení služby, který je vzájemná spolupráce s služeb a klientů na jakoukoli platformu nebo operační systém jsou uvedeny v WS-I Basic Profile 1.1 specifikace.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>Související oddíly  
 [Základní programovací životní cyklus](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [Navrhování a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [Služby hostování](../../../docs/framework/wcf/hosting-services.md)  
  
 [Sestavování klientů](../../../docs/framework/wcf/building-clients.md)  
  
 [Úvod do rozšíření](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [Správa a diagnostika](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a>Viz také:

- [Základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Koncepční přehled](../../../docs/framework/wcf/conceptual-overview.md)
- [Podrobnosti o funkcích WCF](../../../docs/framework/wcf/feature-details/index.md)
