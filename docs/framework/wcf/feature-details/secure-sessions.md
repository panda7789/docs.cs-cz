---
title: Zabezpečené relace
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
author: BrucePerlerMS
ms.openlocfilehash: 09c261afb2c64a46fc1f4619c4ec6b2e87b3fbbf
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027322"
---
# <a name="secure-sessions"></a><span data-ttu-id="1b56a-102">Zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="1b56a-102">Secure Sessions</span></span>
<span data-ttu-id="1b56a-103">Funkce služby Windows Communication Foundation (WCF) je spolehlivé relace, které zaručuje, že jsou zprávy přijímány v pořadí, ve kterém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="1b56a-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="1b56a-104">Témata v této části popisují vliv zabezpečení můžete zvážit při vytváření spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="1b56a-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="1b56a-105">Další informace o spolehlivých relací najdete v tématu [s využitím relací](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="1b56a-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b56a-106">Když zosobnění je potřeba na Windows XP, použijte k tomu zabezpečenou relaci bez tokenu kontextu zabezpečení stavové (SCT).</span><span class="sxs-lookup"><span data-stu-id="1b56a-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="1b56a-107">Když zosobnění, se používají stavové SCTs <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1b56a-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="1b56a-108">Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="1b56a-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b56a-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1b56a-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="1b56a-110">Zabezpečené konverzace a zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="1b56a-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="1b56a-111">Zabezpečené konverzace a zabezpečené relace je shodný.</span><span class="sxs-lookup"><span data-stu-id="1b56a-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="1b56a-112">Toto téma popisuje způsob, jakým funguje zabezpečené konverzace a kdy a proč k použití vzoru.</span><span class="sxs-lookup"><span data-stu-id="1b56a-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="1b56a-113">Postupy: Vytvoření zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="1b56a-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="1b56a-114">Vás provede základy práce vytváření zabezpečenou relaci.</span><span class="sxs-lookup"><span data-stu-id="1b56a-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="1b56a-115">Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci</span><span class="sxs-lookup"><span data-stu-id="1b56a-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="1b56a-116">Vás provede kroky k vytvoření webové farmy, která bude spravovat stav a relace s klienty.</span><span class="sxs-lookup"><span data-stu-id="1b56a-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="1b56a-117">Důležité informace o zabezpečení pro zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="1b56a-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="1b56a-118">Popisuje důležité informace pro zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="1b56a-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="1b56a-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1b56a-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="1b56a-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1b56a-120">Related Sections</span></span>  
 [<span data-ttu-id="1b56a-121">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="1b56a-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="1b56a-122">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="1b56a-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b56a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b56a-123">See Also</span></span>  
 [<span data-ttu-id="1b56a-124">Postupy: Povolení zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="1b56a-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="1b56a-125">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="1b56a-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="1b56a-126">Postupy: Vytvoření služby vyžadující relace</span><span class="sxs-lookup"><span data-stu-id="1b56a-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
