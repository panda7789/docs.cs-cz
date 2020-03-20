---
title: 'Postupy: Vytvoření služby vyžadující relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184991"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="9594a-102">Postupy: Vytvoření služby vyžadující relace</span><span class="sxs-lookup"><span data-stu-id="9594a-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="9594a-103">Relace vytvořit sdílený stav mezi dvěma nebo více koncových bodů, které umožňuje užitečné funkce, jako jsou zpětná volání, multi-hop zabezpečení a přidružení mezi klienty a instance služby.</span><span class="sxs-lookup"><span data-stu-id="9594a-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="9594a-104">Další informace o relacích v aplikacích WCF (Windows Communication Foundation) naleznete v [tématu Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="9594a-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="9594a-105">Určení, že smlouva vyžaduje její vazbu pro podporu relací</span><span class="sxs-lookup"><span data-stu-id="9594a-105">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="9594a-106">Vytvořte servisní smlouvu s alespoň jednou operací.</span><span class="sxs-lookup"><span data-stu-id="9594a-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="9594a-107">Příklad vytvoření servisní smlouvy naleznete v tématu [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="9594a-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="9594a-108"><xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> Upravte, který deklaruje smlouvu nastavením <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnosti buď:</span><span class="sxs-lookup"><span data-stu-id="9594a-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="9594a-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>pokud tato smlouva musí být spuštěna v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="9594a-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="9594a-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>pokud lze tuto smlouvu spustit v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="9594a-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="9594a-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>pokud tato smlouva nesmí být spuštěna v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="9594a-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="9594a-112">Nakonfigurujte koncový bod služby tak, aby používal vazbu, která podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="9594a-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="9594a-113">Následující příklad konfigurace ukazuje použití <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, který podporuje`-`ws reliablemessaging relace.</span><span class="sxs-lookup"><span data-stu-id="9594a-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="9594a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9594a-114">Example</span></span>  
 <span data-ttu-id="9594a-115">Následující ukázkový kód ukazuje, jak zadat požadavek relace na úrovni smlouvy <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> a použít konfigurační soubor pro podporu tohoto požadavku s vazbou.</span><span class="sxs-lookup"><span data-stu-id="9594a-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="9594a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9594a-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
