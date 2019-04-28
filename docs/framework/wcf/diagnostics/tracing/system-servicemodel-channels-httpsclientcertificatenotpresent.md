---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 15ae13563cfcfb3765559cafb2d31bd6482df7b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767309"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="e3666-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="e3666-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="e3666-103">Je požadován klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="e3666-103">Client certificate is required.</span></span> <span data-ttu-id="e3666-104">V požadavku nebyl nalezen žádný certifikát.</span><span class="sxs-lookup"><span data-stu-id="e3666-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e3666-105">Popis</span><span class="sxs-lookup"><span data-stu-id="e3666-105">Description</span></span>  
 <span data-ttu-id="e3666-106">Trasování označuje, že naslouchací proces HTTPS přijala požadavek HTTPS, který se nepřidružil k klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="e3666-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="e3666-107">Protože naslouchací proces byl nakonfigurovaný k vyžadování klientské certifikáty pro všechny požadavky HTTPS, naslouchací proces se nepovedlo ověřit pravost klienta.</span><span class="sxs-lookup"><span data-stu-id="e3666-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3666-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3666-108">See also</span></span>

- [<span data-ttu-id="e3666-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="e3666-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="e3666-110">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="e3666-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e3666-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="e3666-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
