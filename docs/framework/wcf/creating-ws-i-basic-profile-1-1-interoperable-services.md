---
title: Vytváření interoperabilních služeb WS-I Basic Profile 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 06a59c7457c0367d421cb46e33cb67f8fa039c7d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879187"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Vytváření interoperabilních služeb WS-I Basic Profile 1.1
Konfigurace koncového bodu služby WCF umožňuje spolupráci s klienty webové služby ASP.NET:  
  
- Použití <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ vazby pro vaše koncové body služby.  
  
- Nepoužívejte zpětné volání a funkce smlouvy relace nebo chování transakce na váš koncový bod služby  
  
 Volitelně můžete povolit podporu protokolu HTTPS a ověřování klientů na úrovni přenosu na vazbu.  
  
 Následující funkce <xref:System.ServiceModel.BasicHttpBinding> třídy vyžadují funkce nad rámec WS-I Basic Profile 1.1:  
  
- Kódování zpráv přenosu optimalizace mechanismus (MTOM) zpráva řídí <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> vlastnost. Ponechte výchozí hodnotu, která je tato vlastnost <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> nechcete použít MTOM.  
  
- Řídí zabezpečení zpráv <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> hodnota podporuje WS-Security kompatibilní s WS-I základní 1.0 profil zabezpečení. Ponechte výchozí hodnotu, která je tato vlastnost <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> nechcete použít WS-Security.  
  
 Pokud chcete zpřístupnit metadata pro služby WCF pro ASP.NET, pomocí nástrojů generování klienta webové služby: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [nástroj zjišťování webové služby (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)a `Add Web Reference` funkce v sadě Visual Studio; je nutné povolit publikování metadat. Další informace najdete v tématu [publikování kocových bodů metadat](../../../docs/framework/wcf/publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu ukazuje, jak přidat koncový bod WCF, který je kompatibilní s klienty webové služby ASP.NET v kódu a také v konfiguračním souboru.  
  
### <a name="code"></a>Kód  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Viz také:

- [Interoperabilita s webovými službami ASP.NET](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
