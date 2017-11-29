---
title: "Zabezpečené relace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 724ea72c52296c448ead80a8f357235d625f5842
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="secure-sessions"></a>Zabezpečené relace
Funkce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je spolehlivé relace, které zaručit, jsou přijaty zprávy v pořadí, které byly odeslány. Témata v této části popisují vliv zabezpečení, které je třeba zvážit při vytváření spolehlivé relace. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]spolehlivé relace, najdete v části [pomocí relace](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Když zosobnění je potřeba na systému Windows XP, použijte zabezpečené relace bez tokenu kontextu zabezpečení stavová (SCT). V případě stavová SCTs používají s zosobnění, <xref:System.InvalidOperationException> je vyvolána výjimka. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|||  
|-|-|  
|[Zabezpečené konverzace a zabezpečené relace](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Zabezpečené konverzace a zabezpečené relace je shodný. Toto téma vysvětluje, jak zabezpečenou konverzaci pracuje, a kdy a proč používají vzorec.|  
|[Postupy: vytvoření zabezpečené relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Provede základy vytváření zabezpečené relaci.|  
|[Postupy: Vytvoření kontextu zabezpečení tokenu pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Provede kroky k vytvoření webové farmy, která bude spravovat stavu a relace s klienty.|  
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
 [Postupy: vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
