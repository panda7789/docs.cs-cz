---
title: Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 9cc73beeffc9daa9883832b3a6bedd0ff438095c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488995"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="0966a-102">Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="0966a-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="0966a-103">Můžete vytvořit připojení mezi klienty, kteří používají [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] pomocí vazby, které popisují parametry připojení.</span><span class="sxs-lookup"><span data-stu-id="0966a-103">You can create connections between clients using the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="0966a-104">Převádění [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace mohly používat peer-to-peer připojení vyžaduje vazbu, která podporuje tuto technologii, při vytváření připojení klienta.</span><span class="sxs-lookup"><span data-stu-id="0966a-104">Converting a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="0966a-105">Rovnocenného kanálu poskytuje vazbu názvem <xref:System.ServiceModel.NetPeerTcpBinding>, který můžete použít k podobným způsobem <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="0966a-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="0966a-106">Hlavní rozdíly týkat překladač služby a definování nastavení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0966a-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="0966a-107">Pokud aplikace používá výchozí překladač a nastavení zabezpečení, převod normální klientské nebo serverové aplikace pro používání rovnocenného kanálu zahrnuje Změna názvu vazbu z "NetTcpBinding" na "NetPeerTcpBinding" do aplikace konfigurační soubor – nemáte, chcete-li změnit základní kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0966a-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0966a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="0966a-108">See Also</span></span>  
 [<span data-ttu-id="0966a-109">Vytvoření aplikace protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="0966a-109">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [<span data-ttu-id="0966a-110">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="0966a-110">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
