---
title: Zabezpečené konverzace a zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 887b2e6e6553a910de046950514869907519cf35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746460"
---
# <a name="secure-conversations-and-secure-sessions"></a>Zabezpečené konverzace a zabezpečené relace
Funkce Windows Communication Foundation (WCF) je schopnost vytvářet zabezpečené relace mezi dvěma koncovými body, které jsou vzájemně ověřovány, a souhlasím s procesem šifrování a digitálního podpisu. Koncový bod služby může například vyžadovat, aby koncový bod klienta odesílal token zabezpečení založený na certifikátu X. 509 pro ověřování. Po ověření klienta vrátí koncový bod služby token kontextu zabezpečení (SCT) zpátky klientovi, který se pak použije k zabezpečení všech následných zpráv v rámci relace. Vytvořením této zabezpečené relace povolíte efektivnější vyměňování sady zpráv mezi dvěma koncovými body, protože SCT má symetrický klíč. Asymetrické klíče, na kterých jsou založeny certifikáty X. 509, vyžadují při generování digitálního podpisu nebo šifrování sady dat výrazně větší výpočetní výkon než symetrický klíč.  
  
 Zásada Bootstrap (definovaná v části 6.2.7 standardu [WS-SecurityPolicy](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html) ) obsahuje kontrolní výrazy zabezpečení zprávy použité k zabezpečení kanálu a ověřování klienta před protokolem RST/SCT a RSTR/SCT Exchange. Některé standardní vazby WCF mají vlastnost `Security.Message.EstablishSecurityContext`, která určuje, jestli se používá zabezpečená konverzace. Při použití vlastních vazeb je Bootstrap uvedeno vnořením prvků zabezpečení vazby, a to buď pomocí [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) v konfiguračním souboru, nebo voláním <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> v kódu.  
  
 Další informace o relacích najdete v tématu [použití relací](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Viz také

- [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Postupy: Vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
