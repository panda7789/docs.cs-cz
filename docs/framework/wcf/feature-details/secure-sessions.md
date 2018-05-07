---
title: Zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1c7229fba8e30632f08834eb36c1fb177de7a294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="secure-sessions"></a>Zabezpečené relace
Funkce služby Windows Communication Foundation (WCF) je spolehlivé relace, které zaručit, že jsou přijaty zprávy v pořadí, ve kterém byly odeslány. Témata v této části popisují vliv zabezpečení, které je třeba zvážit při vytváření spolehlivé relace. Další informace o spolehlivé relace najdete v tématu [pomocí relace](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Když zosobnění je potřeba na systému Windows XP, použijte zabezpečené relace bez tokenu kontextu zabezpečení stavová (SCT). V případě stavová SCTs používají s zosobnění, <xref:System.InvalidOperationException> je vyvolána výjimka. Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|||  
|-|-|  
|[Zabezpečené konverzace a zabezpečené relace](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Zabezpečené konverzace a zabezpečené relace je shodný. Toto téma vysvětluje, jak zabezpečenou konverzaci pracuje, a kdy a proč používají vzorec.|  
|[Postupy: Vytvoření zabezpečené relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Provede základy vytváření zabezpečené relaci.|  
|[Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Provede kroky k vytvoření webové farmy, která bude spravovat stavu a relace s klienty.|  
|[Důležité informace o zabezpečení pro zabezpečené relace](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|Popisuje důležité informace pro zabezpečené relace.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>Související oddíly  
 [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Navrhování a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Povolení zjišťování opakování zpráv](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Postupy: Vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
