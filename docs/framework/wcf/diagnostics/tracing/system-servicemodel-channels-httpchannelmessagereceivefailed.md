---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: e11b376924ee74e5d0d67da0cac59af41655dc44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594072"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="55c61-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="55c61-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="55c61-103">Nepodařilo se přijmout zprávu přes kanál HTTP.</span><span class="sxs-lookup"><span data-stu-id="55c61-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="55c61-104">Popis</span><span class="sxs-lookup"><span data-stu-id="55c61-104">Description</span></span>  
 <span data-ttu-id="55c61-105">Toto trasování je možné vygenerovat jako upozornění nebo chybu.</span><span class="sxs-lookup"><span data-stu-id="55c61-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="55c61-106">V obou případech se trasování vygeneruje, když se pro příchozí požadavek HTTP nenajde kompatibilní naslouchací proces a požadavek HTTP se zahodí.</span><span class="sxs-lookup"><span data-stu-id="55c61-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="55c61-107">Důvodem může být to, že příkaz HTTP požadavku nebyl rozpoznán jakýmkoli naslouchacím rozhraním protokolu HTTP, nebo protože na adrese, pro kterou byl požadavek cílen, nebyl naslouchá žádný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="55c61-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="55c61-108">Trasování je vygenerováno jako upozornění v případě místního hostitele a jako chyba, pokud je služba hostována službou IIS.</span><span class="sxs-lookup"><span data-stu-id="55c61-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c61-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="55c61-109">See also</span></span>

- [<span data-ttu-id="55c61-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="55c61-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="55c61-111">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="55c61-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="55c61-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="55c61-112">Administration and Diagnostics</span></span>](../index.md)
