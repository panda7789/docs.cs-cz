---
title: "Vytváření interoperabilních služeb WS-I Basic Profile 1.1"
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
helpviewer_keywords: configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 500e57b36bbbdd1d23e6efb2c50421e3e134bcb3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="4180d-102">Vytváření interoperabilních služeb WS-I Basic Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="4180d-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="4180d-103">Ke konfiguraci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] koncový bod služby jako vzájemná spolupráce s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webových služeb klientům:</span><span class="sxs-lookup"><span data-stu-id="4180d-103">To configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients:</span></span>  
  
-   <span data-ttu-id="4180d-104">Použití <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ vazby pro svůj koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="4180d-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
-   <span data-ttu-id="4180d-105">Zpětné volání a funkce kontrakt relace ani chování transakce nelze použít na váš koncový bod služby</span><span class="sxs-lookup"><span data-stu-id="4180d-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="4180d-106">Volitelně můžete umožnit podporu pro protokol HTTPS a ověření klienta transportní vrstvy na vazby.</span><span class="sxs-lookup"><span data-stu-id="4180d-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="4180d-107">Následující funkce sady <xref:System.ServiceModel.BasicHttpBinding> třída, aby funkce nad rámec WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="4180d-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
-   <span data-ttu-id="4180d-108">Kódování zpráv zpráva přenosu optimalizace mechanismus (MTOM) řízené <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4180d-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="4180d-109">V jeho výchozí hodnotu, která je ponechte tuto vlastnost <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> nechcete použít MTOM.</span><span class="sxs-lookup"><span data-stu-id="4180d-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
-   <span data-ttu-id="4180d-110">Řídí zabezpečení zpráv <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> hodnota poskytuje podporu WS-zabezpečení, které jsou kompatibilní s WS-I Basic 1.0 profil zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4180d-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="4180d-111">V jeho výchozí hodnotu, která je ponechte tuto vlastnost <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> nechcete použít WS-zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4180d-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="4180d-112">Chcete, aby metadata pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, které jsou k dispozici pro [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], pomocí nástrojů generování klienta webové služby: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/en-us/b9210348-8bc2-4367-8c91-d1a04b403e88), [(nástroj pro zjišťování webové služby Disco.exe)](http://msdn.microsoft.com/en-us/acd88078-c581-42bc-94ca-6633e2851979)a `Add Web Reference` funkci v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; je nutné povolit metadata publikace.</span><span class="sxs-lookup"><span data-stu-id="4180d-112">To make the metadata for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service available to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/en-us/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Services Discovery Tool (Disco.exe)](http://msdn.microsoft.com/en-us/acd88078-c581-42bc-94ca-6633e2851979), and the `Add Web Reference` feature in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; you must enable metadata publication.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="4180d-113">[Publikování kocových bodů metadat](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="4180d-113"> [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4180d-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4180d-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4180d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="4180d-115">Description</span></span>  
 <span data-ttu-id="4180d-116">Následující příklad kódu ukazuje, jak přidat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] koncový bod, který je kompatibilní s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webových služeb klientům v kódu a případně v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="4180d-116">The following example code demonstrates how to add a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] endpoint that is compatible with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4180d-117">Kód</span><span class="sxs-lookup"><span data-stu-id="4180d-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4180d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4180d-118">See Also</span></span>  
 [<span data-ttu-id="4180d-119">Vzájemná funkční spolupráce s webovými službami ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4180d-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
