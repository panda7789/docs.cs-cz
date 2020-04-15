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
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Vytváření interoperabilních služeb WS-I Basic Profile 1.1
Postup konfigurace koncového bodu služby WCF tak, aby byl interoperabilní s klienty ASP.NET webové služby:  
  
- Použijte <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ vazby pro koncový bod služby.  
  
- Nepoužívejte funkce zpětného volání a smlouvy relace nebo chování transakcí v koncovém bodě služby  
  
Volitelně můžete povolit podporu pro ověřování https a na úrovni přenosu klienta na vazbě.  
  
Následující funkce <xref:System.ServiceModel.BasicHttpBinding> třídy vyžadují funkce nad rámec základního profilu WS-I 1.1:  
  
- Kódování zpráv (MTOM) mechanismus přenosu <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> zpráv řízené vlastností. Ponechte tuto vlastnost na výchozí <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> hodnotu, která je nepoužívat MTOM.  
  
- Zabezpečení zpráv řízené <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> hodnotou poskytuje podporu ws-security kompatibilní s WS-I Basic Security Profile 1.0. Ponechat tuto vlastnost na výchozí <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> hodnotu, která je nepoužívat WS-Security.  
  
Chcete-li zpřístupnit metadata služby WCF pro ASP.NET, použijte nástroje pro generování klienta webové [služby: Nástroj pro popis webových služeb (Wsdl.exe),](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29) [Nástroj pro zjišťování webových služeb (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)a funkce **Přidat webový odkaz** v sadě Visual Studio. Povolte publikování metadat. Další informace naleznete v [tématu Publikování koncových bodů metadat](publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující ukázkový kód ukazuje, jak přidat koncový bod WCF, který je kompatibilní s klienty ASP.NET webové služby v kódu a alternativně v konfiguračním souboru.  
  
### <a name="code"></a>kód  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Viz také

- [Interoperabilita s webovými službami ASP.NET](./feature-details/interop-with-aspnet-web-services.md)
