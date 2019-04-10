---
title: Zabezpečené konverzace a zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 9b2c22d6db5a773bfb3f3a41e458b530fc889d71
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224400"
---
# <a name="secure-conversations-and-secure-sessions"></a>Zabezpečené konverzace a zabezpečené relace
Funkce služby Windows Communication Foundation (WCF) je možnost vytvořit zabezpečené relace mezi dva koncové body, které se navzájem ověří a odsouhlaste šifrování a proces digitální podpis. Koncový bod služby může například vyžadovat koncový bod klienta odeslat token zabezpečení na základě certifikátu X.509 pro ověřování. Po ověření klienta koncového bodu služby vrátí zpět do klienta, který potom slouží k zabezpečení všech dalších zpráv v rámci relace token kontextu zabezpečení (SCT). Navázání této relace zabezpečení umožňuje sadu zpráv, které se vyměňují mezi dva koncové body být efektivnější, protože SCT má symetrický klíč. Asymetrické klíče, které certifikáty X.509 jsou založeny na, vyžadují výrazně vyšší výpočetní výkon než symetrického klíče při generování digitálního podpisu nebo sady dat šifrování.  
  
 Zavedení zásad (definované v části 6.2.7 [WS-SecurityPolicy](https://go.microsoft.com/fwlink/?LinkId=99817) standardní) obsahuje kontrolní výrazy zabezpečení zprávy používá k zabezpečení kanálu a ověření klienta před výměnou RVNÍ/SCT a RSTR/SCT. Mají některé standardní vazby WCF `Security.Message.EstablishSecurityContext` slouží vlastnosti, které ovládací prvky, jestli zabezpečené konverzace. Při použití vlastní vazby spuštění je indikován vnoření elementů vazby zabezpečení, buď prostřednictvím [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) v konfiguračním souboru nebo voláním <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> v kódu.  
  
 Další informace o relacích najdete v tématu [s využitím relací](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Viz také:

- [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Postupy: Vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
