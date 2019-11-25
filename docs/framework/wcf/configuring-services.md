---
title: Konfigurace služeb WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 332a88530010197187ca3ea787e152b0c95a5514
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141595"
---
# <a name="configuring-wcf-services"></a>Konfigurace služeb WCF

Po navržení a implementaci kontraktu služby jste připraveni ke konfiguraci služby. Tady je místo, kde definujete a přizpůsobíte, jak je vaše služba vystavena klientům, včetně určení adresy, kde se dá najít, přenos a kódování zpráv, které používá k odesílání a přijímání zpráv, a o typu zabezpečení, které vyžaduje.  
  
 Zde uvedená konfigurace zahrnuje všechny způsoby, imperativně v kódu nebo pomocí konfiguračního souboru, ve kterém můžete definovat a přizpůsobit různé aspekty služby, například zadání adres koncových bodů, používaných přenosů a jejich schémat zabezpečení. V praxi je psaní konfigurace hlavní součástí programování aplikací WCF.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zjednodušená konfigurace](simplified-configuration.md)  
 Počínaje .NET Framework 4 přichází WCF k dispozici nový výchozí konfigurační model, který zjednodušuje požadavky na konfiguraci WCF. Pokud neposkytnete konfiguraci služby WCF pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s výchozími koncovými body, vazbami a chováními.  
  
 [Konfigurace služeb pomocí konfiguračních souborů](configuring-services-using-configuration-files.md)  
 Službu Windows Communication Foundation (WCF) lze konfigurovat pomocí technologie .NET Framework konfigurace. Nejčastěji se prvky XML přidávají do souboru Web. config pro web Internetová informační služba (IIS), který je hostitelem služby WCF. Tyto prvky umožňují změnit podrobnosti, jako jsou adresy koncových bodů (skutečné adresy používané ke komunikaci se službou) na počítačích jednotlivých počítačů.  
  
 [Vazby](bindings.md)  
 Kromě toho WCF zahrnuje několik běžných konfigurací poskytovaných systémem ve formě vazeb, které vám umožní rychle vybrat základní funkce pro komunikaci klientů a služeb, jako jsou třeba přenosy, zabezpečení a kódování zpráv.  
  
 [Koncové body](endpoints.md)  
 Veškerá komunikace se službou WCF probíhá prostřednictvím *koncových bodů* služby. Koncové body obsahují kontrakt, informace o konfiguraci, které jsou zadány ve vazbách, a adresy, které označují, kde se služba nachází, nebo kde získat informace o službě.  
  
 [Zabezpečení služeb](securing-services.md)  
 Pomocí WCF a stávajících mechanismů zabezpečení můžete implementovat do jakékoli služby důvěrnost, integritu, ověřování a autorizaci. Můžete také provést audit na úspěšné a neúspěšné zabezpečení.  
  
 [Vytváření interoperabilních služeb WS-I Basic Profile 1.1](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Požadavky na nasazení služby, která se vzájemně spolupracují se službami a klienty na jakékoli jiné platformě nebo operačním systémem, jsou uvedené ve specifikaci 1,1 profilu WS-I Basic.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>Související oddíly  
 [Základní programovací životní cyklus](basic-programming-lifecycle.md)  
  
 [Navrhování a implementace služeb](designing-and-implementing-services.md)  
  
 [Služby hostování](hosting-services.md)  
  
 [Sestavování klientů](building-clients.md)  
  
 [Úvod do rozšířitelnosti](introduction-to-extensibility.md)  
  
 [Správa a diagnostika](./diagnostics/index.md)  
  
## <a name="see-also"></a>Viz také:

- [Základní programování WCF](basic-wcf-programming.md)
- [Koncepční přehled](conceptual-overview.md)
- [Podrobnosti o funkcích WCF](./feature-details/index.md)
