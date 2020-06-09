---
title: Zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: cb02adc7514e27175088e7664b12e45bc8ca5cd9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590082"
---
# <a name="secure-sessions"></a>Zabezpečené relace
Funkce Windows Communication Foundation (WCF) je spolehlivých relací, které zaručují, že zprávy jsou přijímány v pořadí, v jakém byly odeslány. Témata v této části popisují důsledky zabezpečení, které je potřeba vzít v úvahu při vytváření spolehlivé relace. Další informace o spolehlivých relacích najdete v tématu [použití relací](../using-sessions.md).  
  
> [!NOTE]
> Pokud je v systému Windows XP vyžadován zosobnění, použijte zabezpečenou relaci bez stavového kontextu zabezpečení (SCT). Pokud se pro zosobnění použijí stavová SCTs, <xref:System.InvalidOperationException> je vyvolána výjimka. Další informace najdete v tématu [nepodporované scénáře](unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|||  
|-|-|  
|[Zabezpečené konverzace a zabezpečené relace](secure-conversations-and-secure-sessions.md)|Zabezpečené konverzace a zabezpečené relace jsou synonyma. Toto téma vysvětluje způsob, jakým funguje zabezpečená konverzace a kdy a proč použít vzor.|  
|[Postupy: Vytvoření zabezpečené relace](how-to-create-a-secure-session.md)|Provede vás základy vytvoření zabezpečené relace.|  
|[Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](how-to-create-a-security-context-token-for-a-secure-session.md)|Provede vás kroky pro vytvoření webové farmy, která bude udržovat stav a relace s klienty.|  
|[Důležité informace o zabezpečení pro zabezpečené relace](security-considerations-for-secure-sessions.md)|Popisuje zvláštní požadavky na zabezpečení relací.|  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>Související oddíly  
 [Relace, vytváření instancí a souběžnost](sessions-instancing-and-concurrency.md)  
  
 [Navrhování a implementace služeb](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Viz také

- [Postupy: Povolení zjišťování opakování zpráv](how-to-enable-message-replay-detection.md)
- [Útoky opakováním](replay-attacks.md)
- [Postupy: Vytvoření služby vyžadující relace](how-to-create-a-service-that-requires-sessions.md)
