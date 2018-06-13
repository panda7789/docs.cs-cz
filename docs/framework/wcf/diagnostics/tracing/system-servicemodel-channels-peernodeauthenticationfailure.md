---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 633f497950ab14d7715537eed8f5cc80e7a350a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33479850"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="954ff-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="954ff-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="954ff-103">Bezpečnostní ověření typu handshake s potenciální sousedním nebyla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="954ff-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="954ff-104">Popis</span><span class="sxs-lookup"><span data-stu-id="954ff-104">Description</span></span>  
 <span data-ttu-id="954ff-105">Při pokusu o vytvoření zabezpečeného sousedním připojení dojde k trasování.</span><span class="sxs-lookup"><span data-stu-id="954ff-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="954ff-106">K tomu dochází z důvodu nedostatečné nebo nesprávné přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="954ff-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="954ff-107">PeerChannel rozpozná jeden typ tokenu pro silné identifikaci X.509 – certifikáty, které poskytují model silné identity na základě typu ověřování a autorizace, který může být implementováno.</span><span class="sxs-lookup"><span data-stu-id="954ff-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="954ff-108">PeerChannel taky poskytuje podporu pro jednoduché aplikace pomocí hesla.</span><span class="sxs-lookup"><span data-stu-id="954ff-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="954ff-109">Hesla je možné jenom do relace; položku Povolit nelze použít k provedení ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="954ff-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="954ff-110">Je to proto symetrický token, který sdílet skupiny partnerských uzlů je obtížné a nevhodných používané při ověřování zdroje.</span><span class="sxs-lookup"><span data-stu-id="954ff-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="954ff-111">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="954ff-111">Troubleshooting</span></span>  
 <span data-ttu-id="954ff-112">Zajistěte, aby všechny okolí příslušná zabezpečovací přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="954ff-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="954ff-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="954ff-113">See Also</span></span>  
 [<span data-ttu-id="954ff-114">Zabezpečení protokolem Peer Channel</span><span class="sxs-lookup"><span data-stu-id="954ff-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [<span data-ttu-id="954ff-115">Trasování</span><span class="sxs-lookup"><span data-stu-id="954ff-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="954ff-116">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="954ff-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="954ff-117">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="954ff-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
