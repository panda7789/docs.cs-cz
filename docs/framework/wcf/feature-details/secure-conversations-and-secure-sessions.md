---
title: Zabezpečené konverzace a zabezpečené relace
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: 13
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 502064ce30f6e117168834643a116d3983811fb8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="secure-conversations-and-secure-sessions"></a>Zabezpečené konverzace a zabezpečené relace
Funkce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je možnost k vytvoření zabezpečených relací mezi dva koncové body, které vzájemné ověření a odsouhlaste proces digitální podpis a šifrování. Koncový bod služby může například vyžadovat koncový bod klienta odeslat token zabezpečení na základě certifikátu X.509. certifikát pro ověřování. Po ověření klienta koncový bod služby tokenu kontextu zabezpečení (SCT) vrátí zpět do klienta, která se pak použije k zabezpečení všechny následné zprávy v rámci relace. Vytvoření této zabezpečené relace umožňuje sadu zpráv, které se vyměňují mezi dva koncové body být efektivnější, protože SCT má symetrického klíče. Asymetrické klíče, které certifikáty X.509 vycházejí, vyžadují podstatně víc výpočetní výkon než symetrického klíče, při generování digitálního podpisu nebo sadu dat šifrování.  
  
 Zavedení zásad (definované v oddílu 6.2.7 [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standardní) obsahuje kontrolní výrazy zabezpečení zprávy používá k zabezpečení kanálu a ověřit před výměnou RVNÍ/SCT a RSTR/SCT klienta. Některé [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mít standardní vazby `Security.Message.EstablishSecurityContext` ovládacích prvků, které jestli zabezpečené konverzace vlastnost se používá. Při použití vlastní vazby službou bootstrap nástroje je indikován vnoření prvky zabezpečení vazeb, buď prostřednictvím [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) v konfiguračním souboru nebo voláním <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> v kódu.  
  
 Další informace o relacích najdete v tématu [pomocí relace](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Viz také  
 [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Postupy: Vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
