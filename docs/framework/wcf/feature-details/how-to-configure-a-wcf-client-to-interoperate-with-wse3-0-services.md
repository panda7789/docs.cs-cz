---
title: "Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0"
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
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea71737e1e214aa1a035739901bf79f8ef4a9c7a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="36e90-102">Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0</span><span class="sxs-lookup"><span data-stu-id="36e90-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="36e90-103">rozhraní Microsoft .NET (WSE) služeb, když jsou klienti úroveň kompatibilní s Web Services vylepšení 3.0 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienti jsou nakonfigurovány pro použití srpen 2004 verzi specifikace WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="36e90-103"> clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="36e90-104">Konfigurace klienta WCF pro spolupráci s WSE 3.0 webové služby</span><span class="sxs-lookup"><span data-stu-id="36e90-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1.  <span data-ttu-id="36e90-105">Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta pro WSE 3.0 webovou službu.</span><span class="sxs-lookup"><span data-stu-id="36e90-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="36e90-106">Pro WSE webové služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] třída klienta se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="36e90-106">For a WSE Web service, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class is created.</span></span>  
  
     <span data-ttu-id="36e90-107">Podrobnosti o vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, najdete v článku [postupy: vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="36e90-107">For details about creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="36e90-108">Vytvořte třídu, která představuje vazbu, který může komunikovat s WSE 3.0 Web services.</span><span class="sxs-lookup"><span data-stu-id="36e90-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="36e90-109">Následující třídy je součástí [spolupráce s WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) ukázka.</span><span class="sxs-lookup"><span data-stu-id="36e90-109">The following class is part of the [Interoperating with WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) sample.</span></span>  
  
    1.  <span data-ttu-id="36e90-110">Vytvořte třídu, která je odvozena od třídy <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="36e90-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="36e90-111">Následující příklad kódu vytvoří třídu s názvem `WseHttpBinding` odvozený z <xref:System.ServiceModel.Channels.Binding> třídy.</span><span class="sxs-lookup"><span data-stu-id="36e90-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="36e90-112">Přidáte vlastnosti pro třídu, která zadejte připraveného assertion WSE, jestli odvozené klíče jsou požadovány, jestli zabezpečených relací se používají, zda jsou požadovány potvrzení podpisu a nastavení ochrany zpráv.</span><span class="sxs-lookup"><span data-stu-id="36e90-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="36e90-113">Následující příklad kódu definuje `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` vlastnosti, které určují připraveného assertion WSE, jestli odvozené klíče jsou požadovány, jestli zabezpečených relací se používají, zda jsou požadovány potvrzení podpisu a nastavení ochrany zprávy, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="36e90-113">The following code example defines `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="36e90-114">Přepsání <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodu a nastavit vlastnosti vazby.</span><span class="sxs-lookup"><span data-stu-id="36e90-114">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="36e90-115">Následující příklad kódu určuje přenosu, kódování zpráv a nastavení ochrany zpráv získáním hodnoty `SecurityAssertion` a `MessageProtectionOrder` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="36e90-115">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="36e90-116">V kódu aplikace klienta přidáte kód pro nastavení vlastnosti vazby.</span><span class="sxs-lookup"><span data-stu-id="36e90-116">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="36e90-117">Následující příklad kódu určuje, že [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient musí použít ochranu zprávu a ověřování podle definice WSE 3.0 `AnonymousForCertificate` assertion připraveného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="36e90-117">The following code example specifies that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="36e90-118">Kromě toho jsou vyžadovány zabezpečených relací a odvozené klíče.</span><span class="sxs-lookup"><span data-stu-id="36e90-118">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="36e90-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="36e90-119">Example</span></span>  
 <span data-ttu-id="36e90-120">Následující příklad kódu definuje vlastní vazby, která zveřejňuje vlastnosti, které odpovídají vlastnosti kontrolní výraz WSE 3.0 to zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="36e90-120">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="36e90-121">Vlastní vazby, která se nazývá `WseHttpBinding`, pak slouží k určení vazby vlastnosti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="36e90-121">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="36e90-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="36e90-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 [<span data-ttu-id="36e90-123">Spolupráce s WSE</span><span class="sxs-lookup"><span data-stu-id="36e90-123">Interoperating with WSE</span></span>](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
