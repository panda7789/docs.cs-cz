---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 3dd28276cd3a39497c0387f5b9d0adec23d07c37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182192"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="c80a8-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="c80a8-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="c80a8-103">Při zavírání připojení v tomto fondu připojení došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="c80a8-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c80a8-104">Popis</span><span class="sxs-lookup"><span data-stu-id="c80a8-104">Description</span></span>  
 <span data-ttu-id="c80a8-105">Úroveň trasování chyba označuje, že došlo k chybě při zavírání sdružení připojení používá sdružování funkce Windows Communication Foundation (WCF) pro připojení.</span><span class="sxs-lookup"><span data-stu-id="c80a8-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="c80a8-106">Jeden z možných důvodů je neúspěšné uzavření připojení z fondu nebo sadu připojení ve fondu v rámci CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="c80a8-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="c80a8-107">Při vyvolání této výjimky budou zrušeny všechny zbývající neuzavřený připojení v tomto fondu; Neuzavřený připojení v rámci fondy jsou zastavena.</span><span class="sxs-lookup"><span data-stu-id="c80a8-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c80a8-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c80a8-108">See also</span></span>

- [<span data-ttu-id="c80a8-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="c80a8-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="c80a8-110">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="c80a8-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c80a8-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="c80a8-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
