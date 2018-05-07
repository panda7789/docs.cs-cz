---
title: Zabezpečené konverzace a zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c87f53bcaa167dd7b3b039c70129efca43742c1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="secure-conversations-and-secure-sessions"></a>Zabezpečené konverzace a zabezpečené relace
Funkce služby Windows Communication Foundation (WCF) je možnost k vytvoření zabezpečených relací mezi dva koncové body, které vzájemné ověření a odsouhlaste proces digitální podpis a šifrování. Koncový bod služby může například vyžadovat koncový bod klienta odeslat token zabezpečení na základě certifikátu X.509. certifikát pro ověřování. Po ověření klienta koncový bod služby tokenu kontextu zabezpečení (SCT) vrátí zpět do klienta, která se pak použije k zabezpečení všechny následné zprávy v rámci relace. Vytvoření této zabezpečené relace umožňuje sadu zpráv, které se vyměňují mezi dva koncové body být efektivnější, protože SCT má symetrického klíče. Asymetrické klíče, které certifikáty X.509 vycházejí, vyžadují podstatně víc výpočetní výkon než symetrického klíče, při generování digitálního podpisu nebo sadu dat šifrování.  
  
 Zavedení zásad (definované v oddílu 6.2.7 [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standardní) obsahuje kontrolní výrazy zabezpečení zprávy používá k zabezpečení kanálu a ověřit před výměnou RVNÍ/SCT a RSTR/SCT klienta. Mají některé standardní vazby WCF `Security.Message.EstablishSecurityContext` ovládacích prvků, které jestli zabezpečené konverzace vlastnost se používá. Při použití vlastní vazby službou bootstrap nástroje je indikován vnoření prvky zabezpečení vazeb, buď prostřednictvím [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) v konfiguračním souboru nebo voláním <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> v kódu.  
  
 Další informace o relacích najdete v tématu [pomocí relace](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Viz také  
 [Relace, vytváření instancí a souběžnost](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Postupy: Vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
