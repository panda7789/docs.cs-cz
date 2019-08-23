---
title: Zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: d511a45d990e441c5dcfd8405794ec937c0278d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966072"
---
# <a name="secure-sessions"></a><span data-ttu-id="c31bf-102">Zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="c31bf-102">Secure Sessions</span></span>
<span data-ttu-id="c31bf-103">Funkce Windows Communication Foundation (WCF) je spolehlivých relací, které zaručují, že zprávy jsou přijímány v pořadí, v jakém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="c31bf-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="c31bf-104">Témata v této části popisují důsledky zabezpečení, které je potřeba vzít v úvahu při vytváření spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="c31bf-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="c31bf-105">Další informace o spolehlivých relacích najdete v tématu [použití relací](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="c31bf-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c31bf-106">Pokud je v systému Windows XP vyžadován zosobnění, použijte zabezpečenou relaci bez stavového kontextu zabezpečení (SCT).</span><span class="sxs-lookup"><span data-stu-id="c31bf-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="c31bf-107">Pokud se pro zosobnění použijí stavová SCTs, <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c31bf-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="c31bf-108">Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="c31bf-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c31bf-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c31bf-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="c31bf-110">Zabezpečené konverzace a zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="c31bf-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="c31bf-111">Zabezpečené konverzace a zabezpečené relace jsou synonyma.</span><span class="sxs-lookup"><span data-stu-id="c31bf-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="c31bf-112">Toto téma vysvětluje způsob, jakým funguje zabezpečená konverzace a kdy a proč použít vzor.</span><span class="sxs-lookup"><span data-stu-id="c31bf-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="c31bf-113">Postupy: Vytvoření zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="c31bf-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="c31bf-114">Provede vás základy vytvoření zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="c31bf-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="c31bf-115">Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci</span><span class="sxs-lookup"><span data-stu-id="c31bf-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="c31bf-116">Provede vás kroky pro vytvoření webové farmy, která bude udržovat stav a relace s klienty.</span><span class="sxs-lookup"><span data-stu-id="c31bf-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="c31bf-117">Důležité informace o zabezpečení pro zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="c31bf-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="c31bf-118">Popisuje zvláštní požadavky na zabezpečení relací.</span><span class="sxs-lookup"><span data-stu-id="c31bf-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="c31bf-119">Reference</span><span class="sxs-lookup"><span data-stu-id="c31bf-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="c31bf-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c31bf-120">Related Sections</span></span>  
 [<span data-ttu-id="c31bf-121">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="c31bf-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="c31bf-122">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="c31bf-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="c31bf-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c31bf-123">See also</span></span>

- [<span data-ttu-id="c31bf-124">Postupy: Povolit detekci opakovaného přehrání zprávy</span><span class="sxs-lookup"><span data-stu-id="c31bf-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="c31bf-125">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="c31bf-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [<span data-ttu-id="c31bf-126">Postupy: Vytvoření služby vyžadující relace</span><span class="sxs-lookup"><span data-stu-id="c31bf-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
