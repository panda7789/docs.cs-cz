---
title: "Používání protokolu WS-AtomicTransaction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12e6e2be3e01ea920b45cce7a27814dd19c00935
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-ws-atomictransaction"></a><span data-ttu-id="4c850-102">Používání protokolu WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="4c850-102">Using WS-AtomicTransaction</span></span>
<span data-ttu-id="4c850-103">WS-AtomicTransaction (WS-AT) je protokol umožňuje vzájemnou spolupráci transakce.</span><span class="sxs-lookup"><span data-stu-id="4c850-103">WS-AtomicTransaction (WS-AT) is an interoperable transaction protocol.</span></span> <span data-ttu-id="4c850-104">Umožňuje toku distribuované transakce prostřednictvím zpráv, webové služby a koordinovat způsobem umožňuje vzájemnou spolupráci mezi infrastruktury heterogenní transakce.</span><span class="sxs-lookup"><span data-stu-id="4c850-104">It enables you to flow distributed transactions by using Web service messages, and coordinate in an interoperable manner between heterogeneous transaction infrastructures.</span></span> <span data-ttu-id="4c850-105">WS-AT používá protokol dvoufázový zápis k řízení atomic výsledek mezi distribuovaných aplikací, správci transakcí a správci prostředků.</span><span class="sxs-lookup"><span data-stu-id="4c850-105">WS-AT uses the two-phase commit protocol to drive an atomic outcome between distributed applications, transaction managers, and resource managers.</span></span>  
  
 <span data-ttu-id="4c850-106">Implementace služby WS-AT [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] poskytuje zahrnuje protokol služby integrovaný do správce transakcí Microsoft Distributed Transaction Coordinator služba MSDTC ().</span><span class="sxs-lookup"><span data-stu-id="4c850-106">The WS-AT implementation [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides includes a protocol service built into the Microsoft Distributed Transaction Coordinator (MSDTC) transaction manager.</span></span> <span data-ttu-id="4c850-107">Pomocí protokolu WS-AT [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace můžete tok transakcí do jiných aplikací, včetně interoperabilní webové služby vytvořené pomocí technologie třetích stran.</span><span class="sxs-lookup"><span data-stu-id="4c850-107">Using WS-AT, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can flow transactions to other applications, including interoperable Web services built using third-party technology.</span></span>  
  
 <span data-ttu-id="4c850-108">Při toku transakce mezi klientské aplikace a aplikace serveru, transakční protokol použitý je určen podle vazby, že serveru zpřístupní v koncovém bodě klienta vybrané.</span><span class="sxs-lookup"><span data-stu-id="4c850-108">When flowing a transaction between a client application and a server application, the transaction protocol used is determined by the binding that the server exposes on the endpoint the client selected.</span></span> <span data-ttu-id="4c850-109">Některé [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] výchozí vazby poskytované systémem k určení `OleTransactions` protokol jako formát šíření transakce, zatímco ostatní výchozí k určení WS-AT.</span><span class="sxs-lookup"><span data-stu-id="4c850-109">Some [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] system-provided bindings default to specifying the `OleTransactions` protocol as the transaction propagation format, while others default to specifying WS-AT.</span></span> <span data-ttu-id="4c850-110">Můžete také prostřednictvím kódu programu upravit volba transakčního protokolu v dané vazby.</span><span class="sxs-lookup"><span data-stu-id="4c850-110">You can also programmatically modify the choice of transaction protocol inside a given binding.</span></span>  
  
 <span data-ttu-id="4c850-111">Volba vlivy protokolu:</span><span class="sxs-lookup"><span data-stu-id="4c850-111">The choice of protocol influences:</span></span>  
  
-   <span data-ttu-id="4c850-112">Formát hlavičky zpráv použije k posunutí transakce z klienta na server.</span><span class="sxs-lookup"><span data-stu-id="4c850-112">The format of the message headers used to flow the transaction from client to server.</span></span>  
  
-   <span data-ttu-id="4c850-113">Síťový protokol použitý ke spuštění protokolu dvoufázového potvrzení mezi správce transakcí klienta a transakce serveru, aby bylo možné vyřešit výsledek transakce.</span><span class="sxs-lookup"><span data-stu-id="4c850-113">The network protocol used to run the two-phase commit protocol between the client's transaction manager and the server's transaction, in order to resolve the outcome of the transaction.</span></span>  
  
 <span data-ttu-id="4c850-114">Pokud serveru a klienta jsou zapsány pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], není potřeba použít WS-AT.</span><span class="sxs-lookup"><span data-stu-id="4c850-114">If the server and client are written using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], you do not need to use WS-AT.</span></span> <span data-ttu-id="4c850-115">Místo toho můžete použít výchozí nastavení `NetTcpBinding` s `TransactionFlow` povoleno, atribut, který bude používat `OleTransactions` místo protokolu.</span><span class="sxs-lookup"><span data-stu-id="4c850-115">Instead, you can use the default settings of `NetTcpBinding` with the `TransactionFlow` attribute enabled, which will use the `OleTransactions` protocol instead.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="4c850-116">[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4c850-116"> [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span> <span data-ttu-id="4c850-117">Jinak pokud jsou toku transakcí k webovým službám založen na technologiích třetích stran, musíte použít WS-AT.</span><span class="sxs-lookup"><span data-stu-id="4c850-117">Otherwise, if you are flowing transactions to Web services built on third-party technologies, you must use WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c850-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c850-118">See Also</span></span>  
 [<span data-ttu-id="4c850-119">Konfigurace podpory protokolu WS-Atomic Transactions</span><span class="sxs-lookup"><span data-stu-id="4c850-119">Configuring WS-Atomic Transaction Support</span></span>](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
