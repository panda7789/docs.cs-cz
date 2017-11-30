---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0ea98388efe14ac0d18a94ec056a441096a4d7c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="0c272-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="0c272-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="0c272-103">Při ukončování připojení v tomto fondu připojení došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="0c272-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0c272-104">Popis</span><span class="sxs-lookup"><span data-stu-id="0c272-104">Description</span></span>  
 <span data-ttu-id="0c272-105">Úroveň trasování chyby označuje, že došlo k chybě při zavírání fondy připojení používá [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]je sdružování připojení funkce.</span><span class="sxs-lookup"><span data-stu-id="0c272-105">This error level trace indicates that an error has occurred while closing the connection pools used by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]’s connection pooling feature.</span></span> <span data-ttu-id="0c272-106">Jedním z možných důvodů pro tento je neúspěšná skončení ve fondu připojení nebo sadu ve fondu připojení v rámci intervalu.</span><span class="sxs-lookup"><span data-stu-id="0c272-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="0c272-107">Pokud se výjimka, budou zrušeny všechna zbývající uzavřené připojení v tomto fondu; připojení uzavřené v jiných fondech jsou opuštění.</span><span class="sxs-lookup"><span data-stu-id="0c272-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c272-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c272-108">See Also</span></span>  
 [<span data-ttu-id="0c272-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="0c272-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0c272-110">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="0c272-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0c272-111">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="0c272-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
