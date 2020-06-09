---
title: 'Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 7dd50fcc07c6c090042cf87acb4aa5d2b5321a68
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579576"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="07e53-102">Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0</span><span class="sxs-lookup"><span data-stu-id="07e53-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="07e53-103">Klienti služby Windows Communication Foundation (WCF) jsou kompatibilní s vylepšeními webových služeb 3,0 pro služby Microsoft .NET (WSE), když jsou klienti WCF nakonfigurováni na použití verze specifikace WS-Addressing ze srpna 2004.</span><span class="sxs-lookup"><span data-stu-id="07e53-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="07e53-104">Konfigurace klienta WCF pro spolupráci s webovou službou WSE 3,0</span><span class="sxs-lookup"><span data-stu-id="07e53-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1. <span data-ttu-id="07e53-105">Spusťte [Nástroj Svcutil. exe](../servicemodel-metadata-utility-tool-svcutil-exe.md) pro vytváření klienta WCF pro webovou službu WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="07e53-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="07e53-106">Pro webovou službu WSE se vytvoří Třída klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="07e53-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="07e53-107">Podrobnosti o vytvoření klienta WCF naleznete v tématu [Postupy: Vytvoření klienta](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="07e53-107">For details about creating a WCF client, see the [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="07e53-108">Vytvořte třídu, která představuje vazbu, která může komunikovat s webovými službami WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="07e53-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="07e53-109">Následující třída je součástí [spolupracujícího s WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) Sample.</span><span class="sxs-lookup"><span data-stu-id="07e53-109">The following class is part of the [Interoperating with WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) sample.</span></span>  
  
    1. <span data-ttu-id="07e53-110">Vytvořte třídu, která je odvozena od třídy <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="07e53-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="07e53-111">Následující příklad kódu vytvoří třídu s názvem `WseHttpBinding` , která je odvozena z <xref:System.ServiceModel.Channels.Binding> třídy.</span><span class="sxs-lookup"><span data-stu-id="07e53-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. <span data-ttu-id="07e53-112">Přidejte do třídy vlastnosti, které určují kontrolní výraz WSE klíč, zda jsou povinné odvozené klíče, zda jsou používány zabezpečené relace, zda jsou vyžadovány potvrzení podpisů a nastavení ochrany zpráv.</span><span class="sxs-lookup"><span data-stu-id="07e53-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="07e53-113">Následující příklad kódu definuje `SecurityAssertion` `RequireDerivedKeys` vlastnosti,, a `EstablishSecurityContext` `MessageProtectionOrder` .</span><span class="sxs-lookup"><span data-stu-id="07e53-113">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="07e53-114">Určují kontrolní výraz WSE klíč, zda jsou povinné odvozené klíče, zda jsou používány zabezpečené relace, zda jsou vyžadovány potvrzení podpisů a nastavení ochrany zpráv v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="07e53-114">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <span data-ttu-id="07e53-115">Přepsat <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodu pro nastavení vlastností vazby.</span><span class="sxs-lookup"><span data-stu-id="07e53-115">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="07e53-116">Následující příklad kódu určuje přenos, kódování zpráv a nastavení ochrany zpráv pomocí získání hodnot `SecurityAssertion` `MessageProtectionOrder` vlastností a.</span><span class="sxs-lookup"><span data-stu-id="07e53-116">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="07e53-117">V kódu klientské aplikace přidejte kód pro nastavení vlastností vazby.</span><span class="sxs-lookup"><span data-stu-id="07e53-117">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="07e53-118">Následující příklad kódu určuje, že klient služby WCF musí používat ochranu zpráv a ověřování podle definice `AnonymousForCertificate` kontrolního výrazu zabezpečení WSE 3,0 klíč.</span><span class="sxs-lookup"><span data-stu-id="07e53-118">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="07e53-119">Navíc se vyžadují zabezpečené relace a odvozené klíče.</span><span class="sxs-lookup"><span data-stu-id="07e53-119">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="07e53-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="07e53-120">Example</span></span>  
 <span data-ttu-id="07e53-121">Následující příklad kódu definuje vlastní vazbu, která zveřejňuje vlastnosti, které odpovídají vlastnostem kontrolního výrazu zabezpečení WSE 3,0 klíč.</span><span class="sxs-lookup"><span data-stu-id="07e53-121">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="07e53-122">Vlastní vazba, která je pojmenována `WseHttpBinding` , se pak použije k určení vlastností vazby pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="07e53-122">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="07e53-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="07e53-123">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- [<span data-ttu-id="07e53-124">Spolupráce s WSE</span><span class="sxs-lookup"><span data-stu-id="07e53-124">Interoperating with WSE</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
