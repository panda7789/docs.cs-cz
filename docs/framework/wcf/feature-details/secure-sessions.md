---
title: Zabezpečené relace
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: 14
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 068615510d7e1d73ae260441ccef6536ee6ff317
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="secure-sessions"></a><span data-ttu-id="2692a-102">Zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="2692a-102">Secure Sessions</span></span>
<span data-ttu-id="2692a-103">Funkce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je spolehlivé relace, které zaručit, jsou přijaty zprávy v pořadí, které byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="2692a-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="2692a-104">Témata v této části popisují vliv zabezpečení, které je třeba zvážit při vytváření spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="2692a-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="2692a-105">Další informace o spolehlivé relace najdete v tématu [pomocí relace](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="2692a-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2692a-106">Když zosobnění je potřeba na systému Windows XP, použijte zabezpečené relace bez tokenu kontextu zabezpečení stavová (SCT).</span><span class="sxs-lookup"><span data-stu-id="2692a-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="2692a-107">V případě stavová SCTs používají s zosobnění, <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2692a-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="2692a-108">Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="2692a-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2692a-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2692a-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="2692a-110">Zabezpečené konverzace a zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="2692a-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="2692a-111">Zabezpečené konverzace a zabezpečené relace je shodný.</span><span class="sxs-lookup"><span data-stu-id="2692a-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="2692a-112">Toto téma vysvětluje, jak zabezpečenou konverzaci pracuje, a kdy a proč používají vzorec.</span><span class="sxs-lookup"><span data-stu-id="2692a-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="2692a-113">Postupy: Vytvoření zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="2692a-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="2692a-114">Provede základy vytváření zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="2692a-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="2692a-115">Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci</span><span class="sxs-lookup"><span data-stu-id="2692a-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="2692a-116">Provede kroky k vytvoření webové farmy, která bude spravovat stavu a relace s klienty.</span><span class="sxs-lookup"><span data-stu-id="2692a-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="2692a-117">Důležité informace o zabezpečení pro zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="2692a-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="2692a-118">Popisuje důležité informace pro zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="2692a-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="2692a-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2692a-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="2692a-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2692a-120">Related Sections</span></span>  
 [<span data-ttu-id="2692a-121">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="2692a-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="2692a-122">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="2692a-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="2692a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="2692a-123">See Also</span></span>  
 [<span data-ttu-id="2692a-124">Postupy: Povolení zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="2692a-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="2692a-125">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="2692a-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="2692a-126">Postupy: Vytvoření služby vyžadující relace</span><span class="sxs-lookup"><span data-stu-id="2692a-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
