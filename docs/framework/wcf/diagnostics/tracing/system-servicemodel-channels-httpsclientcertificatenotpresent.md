---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd70b4154a388ecb30518f03773d2a296258d7b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="e8f3b-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="e8f3b-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="e8f3b-103">Je požadován klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="e8f3b-103">Client certificate is required.</span></span> <span data-ttu-id="e8f3b-104">V požadavku nebyl nalezen žádný certifikát.</span><span class="sxs-lookup"><span data-stu-id="e8f3b-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e8f3b-105">Popis</span><span class="sxs-lookup"><span data-stu-id="e8f3b-105">Description</span></span>  
 <span data-ttu-id="e8f3b-106">Trasování označuje, že naslouchací proces HTTPS přijala požadavek HTTPS, který nebyl přidružený certifikát klienta.</span><span class="sxs-lookup"><span data-stu-id="e8f3b-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="e8f3b-107">Vzhledem k tomu, že naslouchací proces byl nakonfigurován tak, aby vyžadovala certifikáty klientů pro všechny požadavky HTTPS, naslouchací proces se nezdařilo ověření pravosti klienta.</span><span class="sxs-lookup"><span data-stu-id="e8f3b-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f3b-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8f3b-108">See Also</span></span>  
 [<span data-ttu-id="e8f3b-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="e8f3b-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e8f3b-110">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="e8f3b-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e8f3b-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="e8f3b-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
