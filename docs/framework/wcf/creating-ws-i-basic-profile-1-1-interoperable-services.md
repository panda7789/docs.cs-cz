---
title: Vytváření interoperabilních služeb WS-I Basic Profile 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: aa76a6633ef86a908e00bb9dcb1b16eefe35c12d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804940"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="5f1bf-102">Vytváření interoperabilních služeb WS-I Basic Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="5f1bf-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="5f1bf-103">Ke konfiguraci koncového bodu služby WCF na umožňuje spolupráci s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webových služeb klientům:</span><span class="sxs-lookup"><span data-stu-id="5f1bf-103">To configure a WCF service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients:</span></span>  
  
-   <span data-ttu-id="5f1bf-104">Použití <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ vazby pro svůj koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="5f1bf-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
-   <span data-ttu-id="5f1bf-105">Zpětné volání a funkce kontrakt relace ani chování transakce nelze použít na váš koncový bod služby</span><span class="sxs-lookup"><span data-stu-id="5f1bf-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="5f1bf-106">Volitelně můžete umožnit podporu pro protokol HTTPS a ověření klienta transportní vrstvy na vazby.</span><span class="sxs-lookup"><span data-stu-id="5f1bf-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="5f1bf-107">Následující funkce sady <xref:System.ServiceModel.BasicHttpBinding> třída, aby funkce nad rámec WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="5f1bf-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
-   <span data-ttu-id="5f1bf-108">Kódování zpráv zpráva přenosu optimalizace mechanismus (MTOM) řízené <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5f1bf-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5f1bf-109">V jeho výchozí hodnotu, která je ponechte tuto vlastnost <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> nechcete použít MTOM.</span><span class="sxs-lookup"><span data-stu-id="5f1bf-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
-   <span data-ttu-id="5f1bf-110">Řídí zabezpečení zpráv <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> hodnota poskytuje podporu WS-zabezpečení, které jsou kompatibilní s WS-I Basic 1.0 profil zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5f1bf-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="5f1bf-111">V jeho výchozí hodnotu, která je ponechte tuto vlastnost <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> nechcete použít WS-zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5f1bf-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="5f1bf-112">Pro zpřístupnění metadata pro služby WCF pro [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], pomocí nástrojů generování klienta webové služby: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88), [webové služby zjišťování nástroj (Disco.exe)](http://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979)a `Add Web Reference` funkce v sadě Visual Studio; je nutné povolit metadata publikace.</span><span class="sxs-lookup"><span data-stu-id="5f1bf-112">To make the metadata for a WCF service available to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Services Discovery Tool (Disco.exe)](http://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979), and the `Add Web Reference` feature in Visual Studio; you must enable metadata publication.</span></span> <span data-ttu-id="5f1bf-113">Další informace najdete v tématu [publikování kocových bodů metadat](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="5f1bf-113">For more information, see [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f1bf-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f1bf-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5f1bf-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5f1bf-115">Description</span></span>  
 <span data-ttu-id="5f1bf-116">Následující příklad kódu ukazuje, jak přidat koncový bod WCF, který je kompatibilní s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webových služeb klientům v kódu a případně v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="5f1bf-116">The following example code demonstrates how to add a WCF endpoint that is compatible with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5f1bf-117">Kód</span><span class="sxs-lookup"><span data-stu-id="5f1bf-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5f1bf-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f1bf-118">See Also</span></span>  
 [<span data-ttu-id="5f1bf-119">Interoperabilita s webovými službami ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5f1bf-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
