---
title: Důležité informace o zabezpečení ve službě WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: ed0f018e0151e68afeb9a4747bf8a260faa184b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601033"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="4b222-102">Důležité informace o zabezpečení ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="4b222-102">Security Considerations in WCF</span></span>
<span data-ttu-id="4b222-103">Témata v této části uvádějí různé položky související se zabezpečením, které je potřeba vzít v úvahu při navrhování aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4b222-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b222-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4b222-104">In This Section</span></span>  
 [<span data-ttu-id="4b222-105">Zpřístupnění informací</span><span class="sxs-lookup"><span data-stu-id="4b222-105">Information Disclosure</span></span>](information-disclosure.md)  
 <span data-ttu-id="4b222-106">Tento článek popisuje různé způsoby, jak mohou být informace zveřejněné nebo napadené a jak je zmírnit.</span><span class="sxs-lookup"><span data-stu-id="4b222-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="4b222-107">Zvýšení oprávnění</span><span class="sxs-lookup"><span data-stu-id="4b222-107">Elevation of Privilege</span></span>](elevation-of-privilege.md)  
 <span data-ttu-id="4b222-108">Tento článek popisuje důsledky udělení oprávnění k autorizaci útočníka nad rámec původně udělených a jak ho zmírnit.</span><span class="sxs-lookup"><span data-stu-id="4b222-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="4b222-109">Útok DoS</span><span class="sxs-lookup"><span data-stu-id="4b222-109">Denial of Service</span></span>](denial-of-service.md)  
 <span data-ttu-id="4b222-110">Popisuje, co se stane, když systém nemůže správně zpracovat zprávy a jak ho zmírnit.</span><span class="sxs-lookup"><span data-stu-id="4b222-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="4b222-111">Falšování</span><span class="sxs-lookup"><span data-stu-id="4b222-111">Tampering</span></span>](tampering.md)  
 <span data-ttu-id="4b222-112">Popisuje změny zpráv nebo doručování zpráv a jejich omezení.</span><span class="sxs-lookup"><span data-stu-id="4b222-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="4b222-113">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="4b222-113">Replay Attacks</span></span>](replay-attacks.md)  
 <span data-ttu-id="4b222-114">Tento článek popisuje, co se stane, když útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehraje datový proud na jednu nebo více smluvních stran, a jak to zmírnit.</span><span class="sxs-lookup"><span data-stu-id="4b222-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="4b222-115">Důležité informace o zabezpečení pro zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="4b222-115">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="4b222-116">Popisuje následující položky, které mají vliv na zabezpečení při implementaci zabezpečených relací.</span><span class="sxs-lookup"><span data-stu-id="4b222-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="4b222-117">Nepodporované scénáře</span><span class="sxs-lookup"><span data-stu-id="4b222-117">Unsupported Scenarios</span></span>](unsupported-scenarios.md)  
 <span data-ttu-id="4b222-118">Obsahuje seznam různých scénářů, které nepodporují konkrétní aspekt zabezpečení a je třeba se vyhnout nebo je zvážit.</span><span class="sxs-lookup"><span data-stu-id="4b222-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4b222-119">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="4b222-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="4b222-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4b222-120">Related Sections</span></span>  
 [<span data-ttu-id="4b222-121">Informace o zabezpečení a doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="4b222-121">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="4b222-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b222-122">See also</span></span>

- [<span data-ttu-id="4b222-123">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4b222-123">Security</span></span>](security.md)
