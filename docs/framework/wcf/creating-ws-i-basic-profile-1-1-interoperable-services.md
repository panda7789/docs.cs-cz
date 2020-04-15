---
title: Vytváření interoperabilních služeb WS-I Basic Profile 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: fd7828cccb1a19a17e899525d863021d3670fbdd
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389750"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="ee3e9-102">Vytváření interoperabilních služeb WS-I Basic Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="ee3e9-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="ee3e9-103">Postup konfigurace koncového bodu služby WCF tak, aby byl interoperabilní s klienty ASP.NET webové služby:</span><span class="sxs-lookup"><span data-stu-id="ee3e9-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="ee3e9-104">Použijte <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ vazby pro koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="ee3e9-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="ee3e9-105">Nepoužívejte funkce zpětného volání a smlouvy relace nebo chování transakcí v koncovém bodě služby</span><span class="sxs-lookup"><span data-stu-id="ee3e9-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
<span data-ttu-id="ee3e9-106">Volitelně můžete povolit podporu pro ověřování https a na úrovni přenosu klienta na vazbě.</span><span class="sxs-lookup"><span data-stu-id="ee3e9-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
<span data-ttu-id="ee3e9-107">Následující funkce <xref:System.ServiceModel.BasicHttpBinding> třídy vyžadují funkce nad rámec základního profilu WS-I 1.1:</span><span class="sxs-lookup"><span data-stu-id="ee3e9-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="ee3e9-108">Kódování zpráv (MTOM) mechanismus přenosu <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> zpráv řízené vlastností.</span><span class="sxs-lookup"><span data-stu-id="ee3e9-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ee3e9-109">Ponechte tuto vlastnost na výchozí <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> hodnotu, která je nepoužívat MTOM.</span><span class="sxs-lookup"><span data-stu-id="ee3e9-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="ee3e9-110">Zabezpečení zpráv řízené <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> hodnotou poskytuje podporu ws-security kompatibilní s WS-I Basic Security Profile 1.0.</span><span class="sxs-lookup"><span data-stu-id="ee3e9-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="ee3e9-111">Ponechat tuto vlastnost na výchozí <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> hodnotu, která je nepoužívat WS-Security.</span><span class="sxs-lookup"><span data-stu-id="ee3e9-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
<span data-ttu-id="ee3e9-112">Chcete-li zpřístupnit metadata služby WCF pro ASP.NET, použijte nástroje pro generování klienta webové [služby: Nástroj pro popis webových služeb (Wsdl.exe),](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29) [Nástroj pro zjišťování webových služeb (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)a funkce **Přidat webový odkaz** v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ee3e9-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the **Add Web Reference** feature in Visual Studio.</span></span> <span data-ttu-id="ee3e9-113">Povolte publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="ee3e9-113">Enable metadata publication.</span></span> <span data-ttu-id="ee3e9-114">Další informace naleznete v [tématu Publikování koncových bodů metadat](publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="ee3e9-114">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee3e9-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee3e9-115">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ee3e9-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ee3e9-116">Description</span></span>  
 <span data-ttu-id="ee3e9-117">Následující ukázkový kód ukazuje, jak přidat koncový bod WCF, který je kompatibilní s klienty ASP.NET webové služby v kódu a alternativně v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ee3e9-117">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ee3e9-118">kód</span><span class="sxs-lookup"><span data-stu-id="ee3e9-118">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ee3e9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee3e9-119">See also</span></span>

- [<span data-ttu-id="ee3e9-120">Interoperabilita s webovými službami ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ee3e9-120">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
