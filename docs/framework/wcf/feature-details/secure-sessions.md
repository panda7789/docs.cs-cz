---
title: Zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: d511a45d990e441c5dcfd8405794ec937c0278d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966072"
---
# <a name="secure-sessions"></a>Zabezpečené relace
Funkce Windows Communication Foundation (WCF) je spolehlivých relací, které zaručují, že zprávy jsou přijímány v pořadí, v jakém byly odeslány. Témata v této části popisují důsledky zabezpečení, které je potřeba vzít v úvahu při vytváření spolehlivé relace. Další informace o spolehlivých relacích najdete v tématu [použití relací](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
> Pokud je v systému Windows XP vyžadován zosobnění, použijte zabezpečenou relaci bez stavového kontextu zabezpečení (SCT). Pokud se pro zosobnění použijí stavová SCTs, <xref:System.InvalidOperationException> je vyvolána výjimka. Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|||  
|-|-|  
|[Zabezpečené konverzace a zabezpečené relace](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Zabezpečené konverzace a zabezpečené relace jsou synonyma. Toto téma vysvětluje způsob, jakým funguje zabezpečená konverzace a kdy a proč použít vzor.|  
|[Postupy: Vytvoření zabezpečené relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Provede vás základy vytvoření zabezpečené relace.|  
|[Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Provede vás kroky pro vytvoření webové farmy, která bude udržovat stav a relace s klienty.|  
|[Důležité informace o zabezpečení pro zabezpečené relace](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|Popisuje zvláštní požadavky na zabezpečení relací.|  
  
## <a name="reference"></a>Reference  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>Související oddíly  
 [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Navrhování a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Povolit detekci opakovaného přehrání zprávy](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Postupy: Vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
