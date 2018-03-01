---
title: "Postupy: Přístup ke službám pomocí duplexního kontraktu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 425d17fa34b61985ad3600f992e028e156f6adb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="3748a-102">Postupy: Přístup ke službám pomocí duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="3748a-102">How to: Access Services with a Duplex Contract</span></span>
<span data-ttu-id="3748a-103">Jedna z funkcí systému [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je schopnost vytvářet služby, která používá vzor duplexní zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="3748a-103">One feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="3748a-104">Tento vzor umožňuje službě ke komunikaci s klientem prostřednictvím zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="3748a-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="3748a-105">Toto téma ukazuje postup vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta v třídě klienta, který implementuje rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="3748a-105">This topic shows the steps to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client in a client class that implements the callback interface.</span></span>  
  
 <span data-ttu-id="3748a-106">Duální vazbu zpřístupní IP adresu klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="3748a-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="3748a-107">Klient musí použít zabezpečení zajistit, že připojení jenom k službám ho vztahy důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="3748a-107">The client should use security to ensure that it connects only to services it trusts.</span></span>  
  
 <span data-ttu-id="3748a-108">Kurz týkající se vytváření základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby a klienta, najdete v části [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="3748a-108">For a tutorial on creating a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
### <a name="to-access-a-duplex-service"></a><span data-ttu-id="3748a-109">Pro přístup k duplexní služby</span><span class="sxs-lookup"><span data-stu-id="3748a-109">To access a duplex service</span></span>  
  
1.  <span data-ttu-id="3748a-110">Vytvoření služby, který obsahuje dvě rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3748a-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="3748a-111">První rozhraní je pro službu, druhý pro zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="3748a-111">The first interface is for the service, the second is for the callback.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="3748a-112">Vytvoření duplexní služby, najdete v části [postupy: vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="3748a-112"> creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
2.  <span data-ttu-id="3748a-113">Spusťte službu.</span><span class="sxs-lookup"><span data-stu-id="3748a-113">Run the service.</span></span>  
  
3.  <span data-ttu-id="3748a-114">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat kontrakty (rozhraní) pro klienta.</span><span class="sxs-lookup"><span data-stu-id="3748a-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="3748a-115">Informace o tom, jak to udělat najdete v tématu [postupy: vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="3748a-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
4.  <span data-ttu-id="3748a-116">Implementujte rozhraní zpětného volání ve třídě klienta, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3748a-116">Implement the callback interface in the client class, as shown in the following example.</span></span>  
  
    ```csharp  
    public class CallbackHandler : ICalculatorDuplexCallback  
    {  
        public void Result(double result)  
        {  
            Console.WriteLine("Result ({0})", result);  
        }  
        public void Equation(string equation)  
        {  
            Console.WriteLine("Equation({0})", equation);  
        }  
    }  
    ```  
  
    ```vb  
    Public Class CallbackHandler   
    Implements ICalculatorDuplexCallback  
       Public Sub Result (ByVal result As Double)  
          Console.WriteLine("Result ({0})", result)  
       End Sub  
        Public Sub Equation(ByVal equation As String)  
            Console.Writeline("Equation({0})", equation)  
        End Sub  
    End Class  
    ```  
  
5.  <span data-ttu-id="3748a-117">Vytvořit instanci <xref:System.ServiceModel.InstanceContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="3748a-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="3748a-118">Konstruktor vyžaduje instanci třídy klienta.</span><span class="sxs-lookup"><span data-stu-id="3748a-118">The constructor requires an instance of the client class.</span></span>  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  <span data-ttu-id="3748a-119">Vytvoření instance [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta pomocí konstruktoru, který vyžaduje <xref:System.ServiceModel.InstanceContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="3748a-119">Create an instance of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="3748a-120">Druhý parametr konstruktoru je název koncového bodu v konfiguračním souboru nalézt.</span><span class="sxs-lookup"><span data-stu-id="3748a-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  <span data-ttu-id="3748a-121">Volání metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="3748a-121">Call the methods of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3748a-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="3748a-122">Example</span></span>  
 <span data-ttu-id="3748a-123">Následující příklad kódu ukazuje, jak vytvořit třídu klienta, který přistupuje k duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3748a-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="3748a-124">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3748a-124">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3748a-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3748a-125">See Also</span></span>  
 [<span data-ttu-id="3748a-126">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="3748a-126">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="3748a-127">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="3748a-127">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="3748a-128">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="3748a-128">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="3748a-129">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="3748a-129">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="3748a-130">Postupy: Použití objektu pro vytváření kanálů</span><span class="sxs-lookup"><span data-stu-id="3748a-130">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
