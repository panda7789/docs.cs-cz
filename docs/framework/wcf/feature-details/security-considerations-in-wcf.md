---
title: Důležité informace o zabezpečení ve službě WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: 16b3afe9540f3e2953311f602408fce5412be2eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000763"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="5d2b4-102">Důležité informace o zabezpečení ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="5d2b4-102">Security Considerations in WCF</span></span>
<span data-ttu-id="5d2b4-103">Témata v této části obsahují různé položky, které souvisejí se zabezpečením, vzít v úvahu při navrhování aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5d2b4-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d2b4-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5d2b4-104">In This Section</span></span>  
 [<span data-ttu-id="5d2b4-105">Zpřístupnění informací</span><span class="sxs-lookup"><span data-stu-id="5d2b4-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="5d2b4-106">Tento článek popisuje různé způsoby, můžete informace zveřejněn nebo útoku a jak tento problém zmírnit.</span><span class="sxs-lookup"><span data-stu-id="5d2b4-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="5d2b4-107">Zvýšení oprávnění</span><span class="sxs-lookup"><span data-stu-id="5d2b4-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="5d2b4-108">Tento článek popisuje účinky udělení oprávnění útočník autorizace nad rámec těch, nejdřív udělit a jak tento problém zmírnit.</span><span class="sxs-lookup"><span data-stu-id="5d2b4-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="5d2b4-109">Útok DoS</span><span class="sxs-lookup"><span data-stu-id="5d2b4-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="5d2b4-110">Popisuje, co se stane, když není schopen správně zpracovávat zprávy systému a o tom, jak ji zmírnit.</span><span class="sxs-lookup"><span data-stu-id="5d2b4-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="5d2b4-111">Falšování</span><span class="sxs-lookup"><span data-stu-id="5d2b4-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="5d2b4-112">Tento článek popisuje změnu zpráv nebo doručení zpráv a jak ji zmírnit.</span><span class="sxs-lookup"><span data-stu-id="5d2b4-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="5d2b4-113">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="5d2b4-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="5d2b4-114">Tento článek popisuje, co se stane, když útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehrává datový proud do jedné nebo více stran a jak tento problém zmírnit.</span><span class="sxs-lookup"><span data-stu-id="5d2b4-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="5d2b4-115">Důležité informace o zabezpečení pro zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="5d2b4-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="5d2b4-116">Tento článek popisuje následující položky, které mají vliv na zabezpečení při provádění zabezpečených relací.</span><span class="sxs-lookup"><span data-stu-id="5d2b4-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="5d2b4-117">Nepodporované scénáře</span><span class="sxs-lookup"><span data-stu-id="5d2b4-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="5d2b4-118">Uvádí různé scénáře, které nepodporují konkrétní aspekty zabezpečení a mají předejít nebo považovány za.</span><span class="sxs-lookup"><span data-stu-id="5d2b4-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5d2b4-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="5d2b4-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="5d2b4-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5d2b4-120">Related Sections</span></span>  
 [<span data-ttu-id="5d2b4-121">Informace o zabezpečení a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="5d2b4-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="5d2b4-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d2b4-122">See also</span></span>

- [<span data-ttu-id="5d2b4-123">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5d2b4-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
