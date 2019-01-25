---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: 22730ef8a0c0b4706f9e267fef251014a70a58fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720168"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="22749-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="22749-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="22749-103">Příjem zprávy přes kanál protokolu HTTP se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="22749-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="22749-104">Popis</span><span class="sxs-lookup"><span data-stu-id="22749-104">Description</span></span>  
 <span data-ttu-id="22749-105">Trasování může být generována jako upozornění nebo chybu.</span><span class="sxs-lookup"><span data-stu-id="22749-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="22749-106">V obou případech je vygenerován trasování pro příchozí požadavek protokolu HTTP nebyla nalezena kompatibilní naslouchací proces a tato žádost HTTP se zahodí.</span><span class="sxs-lookup"><span data-stu-id="22749-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="22749-107">Může k tomu dojít, protože příkaz HTTP požadavku nebyl rozpoznán jakékoli naslouchací proces protokolu HTTP, nebo protože neposlouchal žádný posluchač na adrese požadavku je určený pro.</span><span class="sxs-lookup"><span data-stu-id="22749-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="22749-108">Trasování je vygenerován jako upozornění v případě v místním prostředí a za chybu, pokud služba je hostována ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="22749-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22749-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22749-109">See also</span></span>
- [<span data-ttu-id="22749-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="22749-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="22749-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="22749-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="22749-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="22749-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
