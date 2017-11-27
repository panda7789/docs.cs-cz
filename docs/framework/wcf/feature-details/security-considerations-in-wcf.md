---
title: "Důležité informace o zabezpečení ve službě WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
caps.latest.revision: "49"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c0af5a5d96f20b2ba5118909a3f0c5ba405bdb11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="fdf30-102">Důležité informace o zabezpečení ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="fdf30-102">Security Considerations in WCF</span></span>
<span data-ttu-id="fdf30-103">Témata v této části seznamu různé položky související se zabezpečením vzít v úvahu při navrhování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="fdf30-103">The topics in this section list various security-related items to consider when designing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fdf30-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fdf30-104">In This Section</span></span>  
 [<span data-ttu-id="fdf30-105">Zpřístupnění informací</span><span class="sxs-lookup"><span data-stu-id="fdf30-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="fdf30-106">Popisuje různé způsoby, že informace mohou být odhalena nebo napadení a toto riziko lze snížit.</span><span class="sxs-lookup"><span data-stu-id="fdf30-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="fdf30-107">Zvýšení úrovně oprávnění</span><span class="sxs-lookup"><span data-stu-id="fdf30-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="fdf30-108">Popisuje účinky udělíte oprávnění autorizace útočník nad rámec těch, původně udělena a jak toto riziko lze snížit.</span><span class="sxs-lookup"><span data-stu-id="fdf30-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="fdf30-109">Odmítnutí služby</span><span class="sxs-lookup"><span data-stu-id="fdf30-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="fdf30-110">Popisuje, co se stane, když nelze správně zpracovat zprávy systému a jak ji zmírnit.</span><span class="sxs-lookup"><span data-stu-id="fdf30-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="fdf30-111">Manipulaci</span><span class="sxs-lookup"><span data-stu-id="fdf30-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="fdf30-112">Popisuje změnu zprávy nebo doručení zpráv a jak ji zmírnit.</span><span class="sxs-lookup"><span data-stu-id="fdf30-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="fdf30-113">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="fdf30-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="fdf30-114">Popisuje, co se stane, když útočník zkopíruje datového proudu zpráv mezi dvěma stranami a replays datového proudu k jedné nebo více stran a jak toto riziko lze snížit.</span><span class="sxs-lookup"><span data-stu-id="fdf30-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="fdf30-115">Důležité informace o zabezpečení pro zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="fdf30-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="fdf30-116">Popisuje následující položky, které mají vliv na zabezpečení při implementaci zabezpečených relací.</span><span class="sxs-lookup"><span data-stu-id="fdf30-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="fdf30-117">Nepodporované scénáře</span><span class="sxs-lookup"><span data-stu-id="fdf30-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="fdf30-118">Uvádí různé scénáře, které nepodporují jednotlivé aspekty zabezpečení a by měl být odstraněna nebo považována za.</span><span class="sxs-lookup"><span data-stu-id="fdf30-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fdf30-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="fdf30-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="fdf30-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="fdf30-120">Related Sections</span></span>  
 [<span data-ttu-id="fdf30-121">Informace o zabezpečení a doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="fdf30-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="fdf30-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdf30-122">See Also</span></span>  
 [<span data-ttu-id="fdf30-123">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fdf30-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
