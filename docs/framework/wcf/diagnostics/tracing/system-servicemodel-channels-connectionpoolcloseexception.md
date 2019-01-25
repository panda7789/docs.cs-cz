---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: b2d49910ecbcd67beca83e2fbeabfbcafe6e1dd0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628029"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="e876f-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="e876f-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="e876f-103">Při zavírání připojení v tomto fondu připojení došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="e876f-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e876f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e876f-104">Description</span></span>  
 <span data-ttu-id="e876f-105">Úroveň trasování chyba označuje, že došlo k chybě při zavírání sdružení připojení používá sdružování funkce Windows Communication Foundation (WCF) pro připojení.</span><span class="sxs-lookup"><span data-stu-id="e876f-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="e876f-106">Jeden z možných důvodů je neúspěšné uzavření připojení z fondu nebo sadu připojení ve fondu v rámci CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="e876f-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="e876f-107">Při vyvolání této výjimky budou zrušeny všechny zbývající neuzavřený připojení v tomto fondu; Neuzavřený připojení v rámci fondy jsou zastavena.</span><span class="sxs-lookup"><span data-stu-id="e876f-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e876f-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e876f-108">See also</span></span>
- [<span data-ttu-id="e876f-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="e876f-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="e876f-110">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="e876f-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e876f-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="e876f-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
