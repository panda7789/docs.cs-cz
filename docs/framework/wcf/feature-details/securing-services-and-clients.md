---
title: Zabezpečení služeb a klientů
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: db0a0dcfbe04a7b7dbfabfed59f9b8637d0a2797
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586205"
---
# <a name="securing-services-and-clients"></a>Zabezpečení služeb a klientů
Informace v této části se zaměřují na zabezpečení programování v Windows Communication Foundation (WCF). Obecně to zahrnuje výběr vhodné vazby ze systému, nastavení vlastností elementu zabezpečení a nastavení vlastností chování služby, které určují, jak jsou načteny přihlašovací údaje pro použití buď pomocí služby, nebo klienta. Tyto postupy pokrývají požadavky na zabezpečení většiny uživatelů pro většinu scénářů, jak je znázorněno v [běžných scénářích zabezpečení](common-security-scenarios.md). Pokud váš scénář vyžaduje více možností, napřed si přečtěte [Možnosti zabezpečení s vlastními vazbami](security-capabilities-with-custom-bindings.md). Pokud řešení není zřejmé, přečtěte si téma [rozšíření zabezpečení](../extending/extending-security.md). Pokud vytváříte (nebo pracujete s) systémem, který používá bohatou deklaraci identity, přečtěte si témata v části [autorizace](authorization-in-wcf.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Programování zabezpečení WCF](programming-wcf-security.md)  
 Přehled programovacího modelu používaného pro zabezpečení zpráv.  
  
 [Přehled zabezpečení přenosu](transport-security-overview.md)  
 Přehled, jak zabezpečit zprávy přes přenosovou vrstvu.  
  
 [Zabezpečení zpráv](message-security-in-wcf.md)  
 Shrnuje důvody pro použití zabezpečení na úrovni zprávy v Windows Communication Foundation (WCF).  
  
 [Zabezpečené relace](secure-sessions.md)  
 Diskuze o požadavcích požadovaných při zabezpečení relace WCF.  
  
 [Práce s certifikáty](working-with-certificates.md)  
 Vysvětlení některých běžných úloh, které jsou vyžadovány při použití certifikátů X. 509.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>Související oddíly  
 [Koncepce zabezpečení](security-concepts.md)  
  
 [Rozšíření zabezpečení](../extending/extending-security.md)  
  
 [Běžné scénáře zabezpečení](common-security-scenarios.md)  
  
 [Vazby a zabezpečení](bindings-and-security.md)  
  
 [Možnosti zabezpečení u vlastních vazeb](security-capabilities-with-custom-bindings.md)  
  
 [Rozšíření zabezpečení](../extending/extending-security.md)  
  
 [Autorizace](authorization-in-wcf.md)  
  
## <a name="see-also"></a>Viz také

- [Základní programování WCF](../basic-wcf-programming.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
