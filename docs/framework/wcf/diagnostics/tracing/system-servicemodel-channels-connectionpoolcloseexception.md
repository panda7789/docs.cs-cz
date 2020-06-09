---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 0a312d192546655dc327667c00f4f2bbc0c15fdb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602038"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="075ac-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="075ac-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="075ac-103">Při zavírání připojení v tomto fondu připojení došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="075ac-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="075ac-104">Popis</span><span class="sxs-lookup"><span data-stu-id="075ac-104">Description</span></span>  
 <span data-ttu-id="075ac-105">Tato funkce trasování úrovně chyby indikuje, že došlo k chybě při zavírání fondů připojení používaných funkcí sdružování připojení služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="075ac-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="075ac-106">Jedním z možných důvodů je neúspěšné uzavření sdruženého připojení nebo sada připojení ve fondu v rámci CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="075ac-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="075ac-107">Pokud je tato výjimka vyvolána, všechna zbývající neuzavřená připojení v rámci tohoto fondu budou přerušena; neuzavřená připojení v rámci jiných fondů jsou opuštěna.</span><span class="sxs-lookup"><span data-stu-id="075ac-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="075ac-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="075ac-108">See also</span></span>

- [<span data-ttu-id="075ac-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="075ac-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="075ac-110">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="075ac-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="075ac-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="075ac-111">Administration and Diagnostics</span></span>](../index.md)
