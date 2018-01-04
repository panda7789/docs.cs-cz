---
title: "Postupy: Vytvoření služby vyžadující relace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fba00b6b8aed8e27d5f16612bb77191f6674abe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="df621-102">Postupy: Vytvoření služby vyžadující relace</span><span class="sxs-lookup"><span data-stu-id="df621-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="df621-103">Relace vytvořit sdílený stav mezi dva nebo víc koncových bodů, které umožňuje užitečných funkcí, jako je například zpětná volání, vícenásobného předávání zabezpečení a přidružení mezi klienty a instance služby.</span><span class="sxs-lookup"><span data-stu-id="df621-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="df621-104">relace v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace, najdete v části [pomocí relace](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="df621-104"> sessions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="df621-105">Chcete-li určit kontraktu vyžadují, aby se jeho vazby pro podporu relací</span><span class="sxs-lookup"><span data-stu-id="df621-105">To specify that a contract require its binding to support sessions</span></span>  
  
1.  <span data-ttu-id="df621-106">Vytvoření kontraktu služby s nejméně jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="df621-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="df621-107">Příklad vytvoření kontraktu služby, naleznete v části [postupy: definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="df621-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="df621-108">Změnit <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> , kontrakt deklaruje nastavením <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost, která má buď:</span><span class="sxs-lookup"><span data-stu-id="df621-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <span data-ttu-id="df621-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Pokud tento kontrakt musí být spuštěn v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="df621-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    -   <span data-ttu-id="df621-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Pokud tuto smlouvu můžete spustit v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="df621-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    -   <span data-ttu-id="df621-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Pokud tento kontrakt se nesmí spouštět v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="df621-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3.  <span data-ttu-id="df621-112">Konfigurace vašeho koncového bodu služby použít vazbu, která podporuje relací.</span><span class="sxs-lookup"><span data-stu-id="df621-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="df621-113">Následující příklad konfigurace ukazuje použití <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, který podporuje WS`-`ReliableMessaging relace.</span><span class="sxs-lookup"><span data-stu-id="df621-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="df621-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="df621-114">Example</span></span>  
 <span data-ttu-id="df621-115">Následující příklad kódu ukazuje, jak zadat vyžadování kontrakt úrovni relace a pomocí konfiguračního souboru pro podporu tento požadavek se <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> vazby.</span><span class="sxs-lookup"><span data-stu-id="df621-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="df621-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="df621-116">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
