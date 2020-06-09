---
title: Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 42266d8c7c04e2d8f3f1e4734d9a05181c3f1ea3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595554"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="3b115-102">Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="3b115-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="3b115-103">Propojení mezi klienty pomocí WinFX můžete vytvořit pomocí vazeb, které popisují parametry připojení.</span><span class="sxs-lookup"><span data-stu-id="3b115-103">You can create connections between clients using the WinFX by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="3b115-104">Převedení .NET Framework aplikace na použití připojení typu peer-to-peer vyžaduje vazbu, která tuto technologii podporuje při vytváření připojení klientů.</span><span class="sxs-lookup"><span data-stu-id="3b115-104">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="3b115-105">Partnerský kanál poskytuje vazbu nazvanou <xref:System.ServiceModel.NetPeerTcpBinding> , kterou můžete použít podobným způsobem <xref:System.ServiceModel.NetTcpBinding> .</span><span class="sxs-lookup"><span data-stu-id="3b115-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="3b115-106">Mezi klíčové rozdíly patří určení služby překladače a definování nastavení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3b115-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="3b115-107">Pokud aplikace používá výchozí překladač a nastavení zabezpečení, převádění normální aplikace založené na klientech a serverech na použití rovnocenného kanálu zahrnuje změnu názvu vazby z "NetTcpBinding" na "NetPeerTcpBinding" v konfiguračním souboru aplikace. nemusíte tedy měnit základ kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b115-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b115-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b115-108">See also</span></span>

- [<span data-ttu-id="3b115-109">Vytvoření aplikace protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="3b115-109">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
- [<span data-ttu-id="3b115-110">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="3b115-110">System-Provided Bindings</span></span>](../system-provided-bindings.md)
