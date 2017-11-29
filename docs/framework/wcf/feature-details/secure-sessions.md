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
# <a name="secure-sessions"></a><span data-ttu-id="60e05-102">Zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="60e05-102">Secure Sessions</span></span>
<span data-ttu-id="60e05-103">Funkce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je spolehlivé relace, které zaručit, jsou přijaty zprávy v pořadí, které byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="60e05-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="60e05-104">Témata v této části popisují vliv zabezpečení, které je třeba zvážit při vytváření spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="60e05-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="60e05-105">spolehlivé relace, najdete v části [pomocí relace](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="60e05-105"> reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60e05-106">Když zosobnění je potřeba na systému Windows XP, použijte zabezpečené relace bez tokenu kontextu zabezpečení stavová (SCT).</span><span class="sxs-lookup"><span data-stu-id="60e05-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="60e05-107">V případě stavová SCTs používají s zosobnění, <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="60e05-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="60e05-108">[Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="60e05-108"> [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60e05-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="60e05-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="60e05-110">Zabezpečené konverzace a zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="60e05-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="60e05-111">Zabezpečené konverzace a zabezpečené relace je shodný.</span><span class="sxs-lookup"><span data-stu-id="60e05-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="60e05-112">Toto téma vysvětluje, jak zabezpečenou konverzaci pracuje, a kdy a proč používají vzorec.</span><span class="sxs-lookup"><span data-stu-id="60e05-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="60e05-113">Postupy: vytvoření zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="60e05-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="60e05-114">Provede základy vytváření zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="60e05-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="60e05-115">Postupy: Vytvoření kontextu zabezpečení tokenu pro zabezpečenou relaci</span><span class="sxs-lookup"><span data-stu-id="60e05-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="60e05-116">Provede kroky k vytvoření webové farmy, která bude spravovat stavu a relace s klienty.</span><span class="sxs-lookup"><span data-stu-id="60e05-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="60e05-117">Důležité informace o zabezpečení pro zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="60e05-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="60e05-118">Popisuje důležité informace pro zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="60e05-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="60e05-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="60e05-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="60e05-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="60e05-120">Related Sections</span></span>  
 [<span data-ttu-id="60e05-121">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="60e05-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="60e05-122">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="60e05-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="60e05-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="60e05-123">See Also</span></span>  
 [<span data-ttu-id="60e05-124">Postupy: Povolení zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="60e05-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="60e05-125">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="60e05-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="60e05-126">Postupy: vytvoření služby vyžadující relace</span><span class="sxs-lookup"><span data-stu-id="60e05-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
