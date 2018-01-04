---
title: "Zabezpečené konverzace a zabezpečené relace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d519640c40daf248a01a19f0450f3aea8de6cc04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="secure-conversations-and-secure-sessions"></a><span data-ttu-id="66f4b-102">Zabezpečené konverzace a zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="66f4b-102">Secure Conversations and Secure Sessions</span></span>
<span data-ttu-id="66f4b-103">Funkce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je možnost k vytvoření zabezpečených relací mezi dva koncové body, které vzájemné ověření a odsouhlaste proces digitální podpis a šifrování.</span><span class="sxs-lookup"><span data-stu-id="66f4b-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to establish secure sessions between two endpoints that authenticate each other and agree upon an encryption and digital signature process.</span></span> <span data-ttu-id="66f4b-104">Koncový bod služby může například vyžadovat koncový bod klienta odeslat token zabezpečení na základě certifikátu X.509. certifikát pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="66f4b-104">For example, the service endpoint might require a client endpoint to send a security token based upon an X.509 certificate for authentication.</span></span> <span data-ttu-id="66f4b-105">Po ověření klienta koncový bod služby tokenu kontextu zabezpečení (SCT) vrátí zpět do klienta, která se pak použije k zabezpečení všechny následné zprávy v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="66f4b-105">Once the client is authenticated, the service endpoint returns a security context token (SCT) back to the client that is then used to secure all subsequent messages within the session.</span></span> <span data-ttu-id="66f4b-106">Vytvoření této zabezpečené relace umožňuje sadu zpráv, které se vyměňují mezi dva koncové body být efektivnější, protože SCT má symetrického klíče.</span><span class="sxs-lookup"><span data-stu-id="66f4b-106">Establishing this secure session enables the set of messages that are exchanged between the two endpoints to be more efficient, because the SCT has a symmetric key.</span></span> <span data-ttu-id="66f4b-107">Asymetrické klíče, které certifikáty X.509 vycházejí, vyžadují podstatně víc výpočetní výkon než symetrického klíče, při generování digitálního podpisu nebo sadu dat šifrování.</span><span class="sxs-lookup"><span data-stu-id="66f4b-107">Asymmetric keys, which X.509 certificates are based upon, require significantly more computational power than symmetric keys when generating a digital signature or encrypting a set of data.</span></span>  
  
 <span data-ttu-id="66f4b-108">Zavedení zásad (definované v oddílu 6.2.7 [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standardní) obsahuje kontrolní výrazy zabezpečení zprávy používá k zabezpečení kanálu a ověřit před výměnou RVNÍ/SCT a RSTR/SCT klienta.</span><span class="sxs-lookup"><span data-stu-id="66f4b-108">The bootstrap policy (defined in section 6.2.7 of the [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standard) contains the message security assertions used to secure the channel and authenticate the client prior to the RST/SCT and RSTR/SCT exchange.</span></span> <span data-ttu-id="66f4b-109">Některé [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mít standardní vazby `Security.Message.EstablishSecurityContext` ovládacích prvků, které jestli zabezpečené konverzace vlastnost se používá.</span><span class="sxs-lookup"><span data-stu-id="66f4b-109">Certain [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standard bindings have a `Security.Message.EstablishSecurityContext` property which controls whether secure conversation is used.</span></span> <span data-ttu-id="66f4b-110">Při použití vlastní vazby službou bootstrap nástroje je indikován vnoření prvky zabezpečení vazeb, buď prostřednictvím [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) v konfiguračním souboru nebo voláním <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> v kódu.</span><span class="sxs-lookup"><span data-stu-id="66f4b-110">When using custom bindings the bootstrap is indicated by nesting security binding elements, either through [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) in the configuration file, or by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> in code.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="66f4b-111">relace, viz [pomocí relace](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="66f4b-111"> sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f4b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="66f4b-112">See Also</span></span>  
 [<span data-ttu-id="66f4b-113">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="66f4b-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="66f4b-114">Postupy: Vytvoření služby vyžadující relace</span><span class="sxs-lookup"><span data-stu-id="66f4b-114">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
