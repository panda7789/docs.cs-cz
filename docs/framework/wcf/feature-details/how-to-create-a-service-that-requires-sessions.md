---
title: 'Postupy: Vytvoření služby vyžadující relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 29c2a87daaf763a50aa657c9badc002ff2fa27e1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593331"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="c632c-102">Postupy: Vytvoření služby vyžadující relace</span><span class="sxs-lookup"><span data-stu-id="c632c-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="c632c-103">Relace vytvoří sdílený stav mezi dvěma nebo více koncovými body, které umožňují užitečné funkce, jako jsou zpětná volání, zabezpečení více segmentů a přidružení mezi klienty a instancemi služby.</span><span class="sxs-lookup"><span data-stu-id="c632c-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="c632c-104">Další informace o relacích v aplikacích Windows Communication Foundation (WCF) najdete v tématu [použití relací](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="c632c-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="c632c-105">Určení, že kontrakt vyžaduje svoji vazbu na podporu relací</span><span class="sxs-lookup"><span data-stu-id="c632c-105">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="c632c-106">Vytvořte kontrakt služby s nejméně jednou operací.</span><span class="sxs-lookup"><span data-stu-id="c632c-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="c632c-107">Příklad vytvoření kontraktu služby naleznete v tématu [How to: define a Service kontrakt](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="c632c-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="c632c-108">Upravte <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> , který deklaruje kontrakt, nastavením <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnosti na hodnotu:</span><span class="sxs-lookup"><span data-stu-id="c632c-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="c632c-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Pokud se tento kontrakt musí spustit v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="c632c-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="c632c-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Pokud se tato smlouva dá spustit v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="c632c-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="c632c-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Pokud tato smlouva nesmí běžet v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="c632c-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="c632c-112">Nakonfigurujte koncový bod služby tak, aby používal vazbu, která podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="c632c-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="c632c-113">Následující příklad konfigurace ukazuje použití <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> , který podporuje relaci WS- `-` ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="c632c-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="c632c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="c632c-114">Example</span></span>  
 <span data-ttu-id="c632c-115">Následující příklad kódu ukazuje, jak zadat požadavek relace na úrovni smlouvy a použít konfigurační soubor pro podporu tohoto požadavku s <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> vazbou.</span><span class="sxs-lookup"><span data-stu-id="c632c-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="c632c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c632c-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
