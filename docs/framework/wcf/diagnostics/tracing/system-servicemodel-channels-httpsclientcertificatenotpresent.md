---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 3e3bedca7a46f147ee3d9e143cea7e57095c99d1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602037"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="a76e5-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="a76e5-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="a76e5-103">Certifikát klienta je povinný.</span><span class="sxs-lookup"><span data-stu-id="a76e5-103">Client certificate is required.</span></span> <span data-ttu-id="a76e5-104">V požadavku nebyl nalezen žádný certifikát.</span><span class="sxs-lookup"><span data-stu-id="a76e5-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a76e5-105">Popis</span><span class="sxs-lookup"><span data-stu-id="a76e5-105">Description</span></span>  
 <span data-ttu-id="a76e5-106">Toto trasování indikuje, že naslouchací proces HTTPS přijal požadavek HTTPS, který nebyl přidružen k klientskému certifikátu.</span><span class="sxs-lookup"><span data-stu-id="a76e5-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="a76e5-107">Vzhledem k tomu, že naslouchací proces byl nakonfigurován tak, aby vyžadoval klientské certifikáty u všech požadavků HTTPS, naslouchací proces nemohl ověřit pravost klienta.</span><span class="sxs-lookup"><span data-stu-id="a76e5-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a76e5-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="a76e5-108">See also</span></span>

- [<span data-ttu-id="a76e5-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="a76e5-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="a76e5-110">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="a76e5-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a76e5-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="a76e5-111">Administration and Diagnostics</span></span>](../index.md)
