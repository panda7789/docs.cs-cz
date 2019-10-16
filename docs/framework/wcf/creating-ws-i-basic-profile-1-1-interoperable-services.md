---
title: Vytváření interoperabilních služeb WS-I Basic Profile 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: eb1cd12c45a276d5c3cb14f89205fff618121abc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320130"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="04e71-102">Vytváření interoperabilních služeb WS-I Basic Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="04e71-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="04e71-103">Konfigurace koncového bodu služby WCF pro spolupráci s klienty webové služby ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="04e71-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="04e71-104">Jako typ vazby pro koncový bod služby použijte typ <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04e71-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="04e71-105">Nepoužívejte funkce zpětného volání a kontraktu relace ani chování transakcí na koncovém bodu služby.</span><span class="sxs-lookup"><span data-stu-id="04e71-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="04e71-106">Volitelně můžete povolit podporu ověřování klientů pomocí protokolu HTTPS a na úrovni přenosu na vazbu.</span><span class="sxs-lookup"><span data-stu-id="04e71-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="04e71-107">Následující funkce třídy <xref:System.ServiceModel.BasicHttpBinding> vyžadují funkce nad rámec WS-I Basic Profile 1,1:</span><span class="sxs-lookup"><span data-stu-id="04e71-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="04e71-108">Kódování zprávy nástroje pro optimalizaci přenosu zpráv (MTOM) kontrolované vlastností <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04e71-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="04e71-109">Ponechte tuto vlastnost nastavenou na výchozí hodnotu, což je <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> pro nepoužití MTOM.</span><span class="sxs-lookup"><span data-stu-id="04e71-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="04e71-110">Zabezpečení zprávy řízené hodnotou <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> poskytuje podporu WS-Security kompatibilní s profilem zabezpečení WS-I Basic 1,0.</span><span class="sxs-lookup"><span data-stu-id="04e71-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="04e71-111">Ponechte tuto vlastnost nastavenou na výchozí hodnotu, což je <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType>, aby nepoužívala WS-Security.</span><span class="sxs-lookup"><span data-stu-id="04e71-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="04e71-112">Aby byla metadata služby WCF dostupná pro ASP.NET, použijte nástroje pro generování klienta webové služby: [Nástroj Web Services Description Language (WSDL. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Nástroj pro zjišťování webových služeb (Disc. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)a funkci `Add Web Reference` v aplikaci Visual Studio; je nutné povolit publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="04e71-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the `Add Web Reference` feature in Visual Studio; you must enable metadata publication.</span></span> <span data-ttu-id="04e71-113">Další informace najdete v tématu [publikování koncových bodů metadat](publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="04e71-113">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04e71-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="04e71-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="04e71-115">Popis</span><span class="sxs-lookup"><span data-stu-id="04e71-115">Description</span></span>  
 <span data-ttu-id="04e71-116">Následující příklad kódu ukazuje, jak přidat koncový bod WCF, který je kompatibilní s klienty webové služby ASP.NET v kódu a případně v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="04e71-116">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="04e71-117">Kód</span><span class="sxs-lookup"><span data-stu-id="04e71-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="04e71-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04e71-118">See also</span></span>

- [<span data-ttu-id="04e71-119">Interoperabilita s webovými službami ASP.NET</span><span class="sxs-lookup"><span data-stu-id="04e71-119">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
