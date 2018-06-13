---
title: Důležité informace o zabezpečení ve službě WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 9d26acf8443967bff36637c482dd3270ef034f40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497526"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="52d98-102">Důležité informace o zabezpečení ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="52d98-102">Security Considerations in WCF</span></span>
<span data-ttu-id="52d98-103">V této části jsou uvedeny různé položky související se zabezpečením vzít v úvahu při navrhování aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="52d98-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52d98-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="52d98-104">In This Section</span></span>  
 [<span data-ttu-id="52d98-105">Zpřístupnění informací</span><span class="sxs-lookup"><span data-stu-id="52d98-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="52d98-106">Popisuje různé způsoby, že informace mohou být odhalena nebo napadení a toto riziko lze snížit.</span><span class="sxs-lookup"><span data-stu-id="52d98-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="52d98-107">Zvýšení oprávnění</span><span class="sxs-lookup"><span data-stu-id="52d98-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="52d98-108">Popisuje účinky udělíte oprávnění autorizace útočník nad rámec těch, původně udělena a jak toto riziko lze snížit.</span><span class="sxs-lookup"><span data-stu-id="52d98-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="52d98-109">Útok DoS</span><span class="sxs-lookup"><span data-stu-id="52d98-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="52d98-110">Popisuje, co se stane, když nelze správně zpracovat zprávy systému a jak ji zmírnit.</span><span class="sxs-lookup"><span data-stu-id="52d98-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="52d98-111">Falšování</span><span class="sxs-lookup"><span data-stu-id="52d98-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="52d98-112">Popisuje změnu zprávy nebo doručení zpráv a jak ji zmírnit.</span><span class="sxs-lookup"><span data-stu-id="52d98-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="52d98-113">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="52d98-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="52d98-114">Popisuje, co se stane, když útočník zkopíruje datového proudu zpráv mezi dvěma stranami a replays datového proudu k jedné nebo více stran a jak toto riziko lze snížit.</span><span class="sxs-lookup"><span data-stu-id="52d98-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="52d98-115">Důležité informace o zabezpečení pro zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="52d98-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="52d98-116">Popisuje následující položky, které mají vliv na zabezpečení při implementaci zabezpečených relací.</span><span class="sxs-lookup"><span data-stu-id="52d98-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="52d98-117">Nepodporované scénáře</span><span class="sxs-lookup"><span data-stu-id="52d98-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="52d98-118">Uvádí různé scénáře, které nepodporují jednotlivé aspekty zabezpečení a by měl být odstraněna nebo považována za.</span><span class="sxs-lookup"><span data-stu-id="52d98-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="52d98-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="52d98-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="52d98-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="52d98-120">Related Sections</span></span>  
 [<span data-ttu-id="52d98-121">Informace o zabezpečení a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="52d98-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="52d98-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="52d98-122">See Also</span></span>  
 [<span data-ttu-id="52d98-123">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="52d98-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
