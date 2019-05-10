---
title: 'Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 202b83116666283564ef99dd0a4a7395192cedb3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622892"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="409ad-102">Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0</span><span class="sxs-lookup"><span data-stu-id="409ad-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="409ad-103">Klientů Windows Communication Foundation (WCF) jsou přenosový kompatibilní s Web Services vylepšení 3.0 služby rozhraní Microsoft .NET (Najít), když klienti WCF umožňují použít verzi specifikace WS-Addressing ze srpna 2004.</span><span class="sxs-lookup"><span data-stu-id="409ad-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="409ad-104">Konfigurace klienta WCF pro spolupráci s WSE 3.0 webové služby</span><span class="sxs-lookup"><span data-stu-id="409ad-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1. <span data-ttu-id="409ad-105">Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření klienta WCF pro WSE 3.0 webovou službu.</span><span class="sxs-lookup"><span data-stu-id="409ad-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="409ad-106">WSE webové služby je vytvořená třída klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="409ad-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="409ad-107">Podrobnosti o vytvoření klienta WCF najdete v tématu [jak: Vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="409ad-107">For details about creating a WCF client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="409ad-108">Vytvořte třídu, která představuje vazbu, která může komunikovat s WSE 3.0 Web services.</span><span class="sxs-lookup"><span data-stu-id="409ad-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="409ad-109">Následující třídy je součástí [spolupráce s WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) vzorku.</span><span class="sxs-lookup"><span data-stu-id="409ad-109">The following class is part of the [Interoperating with WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) sample.</span></span>  
  
    1. <span data-ttu-id="409ad-110">Vytvořte třídu, která je odvozena od třídy <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="409ad-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="409ad-111">Následující příklad kódu vytvoří třídu s názvem `WseHttpBinding` , který je odvozen od <xref:System.ServiceModel.Channels.Binding> třídy.</span><span class="sxs-lookup"><span data-stu-id="409ad-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. <span data-ttu-id="409ad-112">Přidání vlastností do třídy, která zadejte výraz na klíč WSE, určuje, zda jsou požadovány odvozené klíče, určuje, zda se používají zabezpečené relace, určuje, zda jsou požadovány nacházejí potvrzení podpisů a nastavení ochrany zprávy.</span><span class="sxs-lookup"><span data-stu-id="409ad-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="409ad-113">Následující příklad kódu definuje `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, a `MessageProtectionOrder` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="409ad-113">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="409ad-114">Určí kontrolního výrazu WSE na klíč, určuje, zda jsou požadovány odvozené klíče, určuje, zda se používají zabezpečené relace, určuje, zda jsou požadovány nacházejí potvrzení podpisů a nastavení ochrany zprávy, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="409ad-114">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <span data-ttu-id="409ad-115">Přepsat <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metody nastavte vlastnosti vazby.</span><span class="sxs-lookup"><span data-stu-id="409ad-115">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="409ad-116">Následující příklad kódu určuje přenos, kódování zpráv a nastavení ochrany zpráv hodnoty s informacemi `SecurityAssertion` a `MessageProtectionOrder` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="409ad-116">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="409ad-117">V kódu aplikace klienta přidejte kód pro nastavení vlastnosti vazby.</span><span class="sxs-lookup"><span data-stu-id="409ad-117">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="409ad-118">Následující příklad kódu určuje, zda klient WCF musí používat zprávy ochrany a ověřování podle definice ve WSE 3.0 `AnonymousForCertificate` kontrolního výrazu zabezpečení na klíč.</span><span class="sxs-lookup"><span data-stu-id="409ad-118">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="409ad-119">Navíc se vyžaduje zabezpečených relací a odvozených klíčů.</span><span class="sxs-lookup"><span data-stu-id="409ad-119">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="409ad-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="409ad-120">Example</span></span>  
 <span data-ttu-id="409ad-121">Následující příklad kódu definuje vlastní vazby, které zpřístupní vlastnosti, které odpovídají vlastnosti kontrolní výraz WSE 3.0 na klíč zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="409ad-121">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="409ad-122">Vlastní vazby, který se nazývá `WseHttpBinding`, se pak použije k určení vlastností vazby pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="409ad-122">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="409ad-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="409ad-123">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- [<span data-ttu-id="409ad-124">Spolupráce s WSE</span><span class="sxs-lookup"><span data-stu-id="409ad-124">Interoperating with WSE</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
