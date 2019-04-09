---
title: 'Postupy: Vytvoření služby vyžadující relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: c104798fa3ef0e8b9dc43ad9cc68599b71de4011
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140488"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="d3536-102">Postupy: Vytvoření služby vyžadující relace</span><span class="sxs-lookup"><span data-stu-id="d3536-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="d3536-103">Relace vytvořit sdílený stav mezi dva nebo víc koncových bodů, které umožňuje užitečných funkcí, jako je například zpětná volání, zabezpečení s více segmenty směrování a přidružení mezi klienty a instance služby.</span><span class="sxs-lookup"><span data-stu-id="d3536-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="d3536-104">Další informace o relacích v aplikacích Windows Communication Foundation (WCF) najdete v tématu [s využitím relací](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="d3536-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="d3536-105">Chcete-li určit, že kontrakt vyžadovat jeho vazby pro podporu relace</span><span class="sxs-lookup"><span data-stu-id="d3536-105">To specify that a contract require its binding to support sessions</span></span>  
  
1.  <span data-ttu-id="d3536-106">Vytvoření kontraktu služby s alespoň jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="d3536-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="d3536-107">Příklad vytvoření kontraktu služby najdete v tématu [jak: Definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="d3536-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="d3536-108">Upravit <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> kontrakt, který deklaruje tak, že nastavíte <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost buď:</span><span class="sxs-lookup"><span data-stu-id="d3536-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> <span data-ttu-id="d3536-109">Pokud tento kontrakt musí být spuštěn v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="d3536-109">if this contract must be run within a session.</span></span>  
  
    -   <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> <span data-ttu-id="d3536-110">Pokud tuto smlouvu můžete spustit v relaci.</span><span class="sxs-lookup"><span data-stu-id="d3536-110">if this contract can be run within a session.</span></span>  
  
    -   <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> <span data-ttu-id="d3536-111">Pokud tuto smlouvu nesmí běžet v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="d3536-111">if this contract must not be run within a session.</span></span>  
  
3.  <span data-ttu-id="d3536-112">Nakonfigurujte koncový bod služby můžete použít vazbu, která podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="d3536-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="d3536-113">Následující příklad konfigurace ukazuje použití <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, která podporuje WS`-`ReliableMessaging relace.</span><span class="sxs-lookup"><span data-stu-id="d3536-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="d3536-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3536-114">Example</span></span>  
 <span data-ttu-id="d3536-115">Následující příklad kódu ukazuje, jak zadat vyžadování úroveň smlouvy relace a pomocí konfiguračního souboru splnění tohoto požadavku se <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> vazby.</span><span class="sxs-lookup"><span data-stu-id="d3536-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="d3536-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3536-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
