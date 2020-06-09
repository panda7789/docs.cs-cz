---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: cb7019f1e4b47bde7c98b0109afa7b0125b7ef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84577302"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="9e419-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="9e419-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="9e419-103">Bezpečnostní Metoda handshake s potenciálním sousedem nebyla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9e419-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9e419-104">Popis</span><span class="sxs-lookup"><span data-stu-id="9e419-104">Description</span></span>  
 <span data-ttu-id="9e419-105">K tomuto trasování dojde při pokusu o navázání zabezpečeného sousedního připojení.</span><span class="sxs-lookup"><span data-stu-id="9e419-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="9e419-106">K tomu může dojít z důvodu nedostatečných nebo nesprávných přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="9e419-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="9e419-107">PeerChannel rozpoznává jeden typ tokenu pro silnou identifikaci, a to pomocí certifikátů X. 509, které poskytují model silné identity na základě typu ověřování a autorizace, které lze implementovat.</span><span class="sxs-lookup"><span data-stu-id="9e419-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="9e419-108">PeerChannel také poskytuje podporu pro jednoduché aplikace pomocí hesel.</span><span class="sxs-lookup"><span data-stu-id="9e419-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="9e419-109">Hesla se dají použít jenom k povolení položky pro relaci. nelze je použít k ověření zprávy.</span><span class="sxs-lookup"><span data-stu-id="9e419-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="9e419-110">Důvodem je to, že symetrický token, který má skupinu partnerských vztahů, je obtížné a nevhodný pro použití při ověřování zdroje.</span><span class="sxs-lookup"><span data-stu-id="9e419-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9e419-111">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="9e419-111">Troubleshooting</span></span>  
 <span data-ttu-id="9e419-112">Ujistěte se, že všechny sousední sousedi mají příslušná zabezpečovací pověření.</span><span class="sxs-lookup"><span data-stu-id="9e419-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e419-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e419-113">See also</span></span>

- [<span data-ttu-id="9e419-114">Zabezpečení protokolem Peer Channel</span><span class="sxs-lookup"><span data-stu-id="9e419-114">Peer Channel Security</span></span>](../../feature-details/peer-channel-security.md)
- [<span data-ttu-id="9e419-115">Trasování</span><span class="sxs-lookup"><span data-stu-id="9e419-115">Tracing</span></span>](index.md)
- [<span data-ttu-id="9e419-116">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="9e419-116">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9e419-117">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="9e419-117">Administration and Diagnostics</span></span>](../index.md)
