---
title: 'Postupy: přístup ke službám pomocí duplexního kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: bc42792b827b49265a0b1addf959de2fa1a041e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597212"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="53a43-102">Postupy: přístup ke službám pomocí duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="53a43-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="53a43-103">Jednou z funkcí služby Windows Communication Foundation (WCF) je schopnost vytvořit službu, která používá duplexový vzor pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="53a43-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="53a43-104">Tento model umožňuje službě komunikovat s klientem prostřednictvím zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="53a43-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="53a43-105">Toto téma ukazuje postup vytvoření klienta WCF v klientské třídě, která implementuje rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="53a43-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="53a43-106">Duální vazba zpřístupňuje IP adresu klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="53a43-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="53a43-107">Klient by měl zabezpečení používat k zajištění toho, aby se připojil pouze ke službám, kterým důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="53a43-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="53a43-108">Kurz týkající se vytvoření základní služby a klienta WCF najdete v tématu [Začínáme kurzu](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="53a43-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="53a43-109">Přístup k duplexní službě</span><span class="sxs-lookup"><span data-stu-id="53a43-109">To access a duplex service</span></span>

1. <span data-ttu-id="53a43-110">Vytvořte službu, která obsahuje dvě rozhraní.</span><span class="sxs-lookup"><span data-stu-id="53a43-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="53a43-111">První rozhraní je pro službu, druhým je pro zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="53a43-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="53a43-112">Další informace o vytváření duplexních služeb najdete v tématu [Postupy: Vytvoření duplexního kontraktu](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="53a43-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="53a43-113">Spusťte službu.</span><span class="sxs-lookup"><span data-stu-id="53a43-113">Run the service.</span></span>

3. <span data-ttu-id="53a43-114">Pro generování kontraktů (rozhraní) pro klienta použijte nástroj pro dodané [metadata (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="53a43-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="53a43-115">Informace o tom, jak to provést, najdete v tématu [Postup: Vytvoření klienta](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="53a43-115">For information about how to do this, see  [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="53a43-116">Implementujte rozhraní zpětného volání ve třídě klienta, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="53a43-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

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
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. <span data-ttu-id="53a43-117">Vytvořit instanci <xref:System.ServiceModel.InstanceContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="53a43-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="53a43-118">Konstruktor vyžaduje instanci klientské třídy.</span><span class="sxs-lookup"><span data-stu-id="53a43-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="53a43-119">Vytvořte instanci klienta WCF pomocí konstruktoru, který vyžaduje <xref:System.ServiceModel.InstanceContext> objekt.</span><span class="sxs-lookup"><span data-stu-id="53a43-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="53a43-120">Druhým parametrem konstruktoru je název koncového bodu, který se nachází v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="53a43-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="53a43-121">Podle potřeby zavolejte metody klienta služby WCF.</span><span class="sxs-lookup"><span data-stu-id="53a43-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="53a43-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="53a43-122">Example</span></span>

<span data-ttu-id="53a43-123">Následující příklad kódu ukazuje, jak vytvořit třídu klienta, která přistupuje k oboustrannému kontraktu.</span><span class="sxs-lookup"><span data-stu-id="53a43-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="53a43-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="53a43-124">See also</span></span>

- [<span data-ttu-id="53a43-125">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="53a43-125">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="53a43-126">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="53a43-126">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="53a43-127">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="53a43-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="53a43-128">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="53a43-128">How to: Create a Client</span></span>](../how-to-create-a-wcf-client.md)
- [<span data-ttu-id="53a43-129">Postupy: Použití objektu pro vytváření kanálů</span><span class="sxs-lookup"><span data-stu-id="53a43-129">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
