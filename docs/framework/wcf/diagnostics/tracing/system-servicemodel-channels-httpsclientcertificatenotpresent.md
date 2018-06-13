---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 9cc1e835df961899d0df6d91e16df05662dca6c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487708"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="75547-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="75547-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="75547-103">Je požadován klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="75547-103">Client certificate is required.</span></span> <span data-ttu-id="75547-104">V požadavku nebyl nalezen žádný certifikát.</span><span class="sxs-lookup"><span data-stu-id="75547-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="75547-105">Popis</span><span class="sxs-lookup"><span data-stu-id="75547-105">Description</span></span>  
 <span data-ttu-id="75547-106">Trasování označuje, že naslouchací proces HTTPS přijala požadavek HTTPS, který nebyl přidružený certifikát klienta.</span><span class="sxs-lookup"><span data-stu-id="75547-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="75547-107">Vzhledem k tomu, že naslouchací proces byl nakonfigurován tak, aby vyžadovala certifikáty klientů pro všechny požadavky HTTPS, naslouchací proces se nezdařilo ověření pravosti klienta.</span><span class="sxs-lookup"><span data-stu-id="75547-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75547-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="75547-108">See Also</span></span>  
 [<span data-ttu-id="75547-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="75547-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="75547-110">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="75547-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="75547-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="75547-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
