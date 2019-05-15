---
title: Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: b89afbe59b73288ba357fa55ec5d55c1fb18352b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582783"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="b98aa-102">Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="b98aa-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="b98aa-103">Můžete vytvořit připojení mezi klienty, kteří používají [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] pomocí vazby, které popisují parametry připojení.</span><span class="sxs-lookup"><span data-stu-id="b98aa-103">You can create connections between clients using the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="b98aa-104">Převedení aplikace rozhraní .NET Framework peer-to-peer připojení vyžaduje vazbu, která podporuje tuto technologii při vytváření připojení klientů.</span><span class="sxs-lookup"><span data-stu-id="b98aa-104">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="b98aa-105">Protokolu peer Channel poskytuje vazby volá <xref:System.ServiceModel.NetPeerTcpBinding>, který můžete použít podobným způsobem jako do <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="b98aa-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="b98aa-106">Hlavní rozdíly zahrnují určení službě překládání a definování nastavení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b98aa-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="b98aa-107">Pokud aplikace používá výchozí překladač a nastavení zabezpečení, převod normální klient/server – na základě aplikace pro použití protokolu Peer Channel zahrnuje změnu názvu vazby z "NetTcpBinding" k "NetPeerTcpBinding" ve vaší aplikace konfigurační soubor – není potřeba změnit základní kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="b98aa-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98aa-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b98aa-108">See also</span></span>

- [<span data-ttu-id="b98aa-109">Vytvoření aplikace protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="b98aa-109">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [<span data-ttu-id="b98aa-110">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="b98aa-110">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
