---
title: "Prevence útoků formou opakovaného přehrávání zprávy, když je služba WCF hostovaná ve webové farmě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ecf37ffb87ddfdd483cebcac3f5892bab43dcd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a><span data-ttu-id="5b4ef-102">Prevence útoků formou opakovaného přehrávání zprávy, když je služba WCF hostovaná ve webové farmě</span><span class="sxs-lookup"><span data-stu-id="5b4ef-102">Preventing Replay Attacks When a WCF Service is Hosted in a Web Farm</span></span>
<span data-ttu-id="5b4ef-103">Při použití zabezpečení zpráv WCF brání provedení útoku formou opakovaného vytvořením hodnotu NONCE mimo příchozí zprávy a kontrola interní `InMemoryNonceCache` zobrazíte, když generovaného hodnotu NONCE nachází.</span><span class="sxs-lookup"><span data-stu-id="5b4ef-103">When using message security WCF prevents replay attacks by creating a NONCE out of the incoming message and checking the internal `InMemoryNonceCache` to see if the generated NONCE is present.</span></span> <span data-ttu-id="5b4ef-104">Pokud se jedná, zpráva se zahodí jako opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="5b4ef-104">If it is, the message is discarded as a replay.</span></span> <span data-ttu-id="5b4ef-105">Pokud služby WCF je hostovaná ve webové farmě, protože `InMemoryNonceCache` není sdílená mezi uzly ve webové farmě, služba je ohrožena útoky opakováním.</span><span class="sxs-lookup"><span data-stu-id="5b4ef-105">When a WCF service is hosted in a web farm, since the `InMemoryNonceCache` is not shared across the nodes in the web farm, the service is vulnerable to replay attacks.</span></span>  <span data-ttu-id="5b4ef-106">Tento scénář zmírnit WCF 4.5 poskytuje bod rozšíření, která umožňuje implementovat vlastní sdílené mezipaměti hodnotu NONCE odvozením třídy od abstraktní třídy <xref:System.ServiceModel.Security.NonceCache>.</span><span class="sxs-lookup"><span data-stu-id="5b4ef-106">To mitigate this scenario WCF 4.5 provides an extensibility point that allows you to implement your own shared NONCE cache by deriving a class from the abstract class <xref:System.ServiceModel.Security.NonceCache>.</span></span>  
  
## <a name="noncecache-implementation"></a><span data-ttu-id="5b4ef-107">Implementace NonceCache</span><span class="sxs-lookup"><span data-stu-id="5b4ef-107">NonceCache Implementation</span></span>  
 <span data-ttu-id="5b4ef-108">Pokud chcete implementovat vlastní sdílené mezipaměti hodnotu NONCE, odvození třídy z <xref:System.ServiceModel.Security.NonceCache> a přepsat <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> a <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5b4ef-108">To implement your own shared NONCE cache, derive a class from <xref:System.ServiceModel.Security.NonceCache> and override the <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> and <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> methods.</span></span> <span data-ttu-id="5b4ef-109"><xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A>zkontroluje, zda zadaný hodnotu NONCE existuje v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5b4ef-109"><xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> will check to see if the specified NONCE exists in the cache.</span></span> <span data-ttu-id="5b4ef-110"><xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A>se pokusí přidat hodnotu NONCE do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5b4ef-110"><xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> will attempt to add a NONCE to the cache.</span></span> <span data-ttu-id="5b4ef-111">Jakmile se implementuje třídu, můžete spojit se vytváření instancí instance a jeho k přiřazení <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> pro stranu klienta zjišťování opakování a <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> na straně serveru zjišťování opakování.</span><span class="sxs-lookup"><span data-stu-id="5b4ef-111">Once the class is implemented, you hook it up by instantiating an instance and assigning it to <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> for client-side replay detection and <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> for server-side replay detection.</span></span> <span data-ttu-id="5b4ef-112">Neexistuje žádné mimo podporu konfigurace políčko pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="5b4ef-112">There is no out of the box configuration support for this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b4ef-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b4ef-113">See Also</span></span>  
 [<span data-ttu-id="5b4ef-114">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="5b4ef-114">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="5b4ef-115">Prvek SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5b4ef-115">SymmetricSecurityBindingElement</span></span>](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
