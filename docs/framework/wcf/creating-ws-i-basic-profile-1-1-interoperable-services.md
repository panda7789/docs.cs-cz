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
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Vytváření interoperabilních služeb WS-I Basic Profile 1.1
Konfigurace koncového bodu služby WCF pro spolupráci s klienty webové služby ASP.NET:  
  
- Jako typ vazby pro koncový bod služby použijte typ <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>.  
  
- Nepoužívejte funkce zpětného volání a kontraktu relace ani chování transakcí na koncovém bodu služby.  
  
 Volitelně můžete povolit podporu ověřování klientů pomocí protokolu HTTPS a na úrovni přenosu na vazbu.  
  
 Následující funkce třídy <xref:System.ServiceModel.BasicHttpBinding> vyžadují funkce nad rámec WS-I Basic Profile 1,1:  
  
- Kódování zprávy nástroje pro optimalizaci přenosu zpráv (MTOM) kontrolované vlastností <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType>. Ponechte tuto vlastnost nastavenou na výchozí hodnotu, což je <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> pro nepoužití MTOM.  
  
- Zabezpečení zprávy řízené hodnotou <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> poskytuje podporu WS-Security kompatibilní s profilem zabezpečení WS-I Basic 1,0. Ponechte tuto vlastnost nastavenou na výchozí hodnotu, což je <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType>, aby nepoužívala WS-Security.  
  
 Aby byla metadata služby WCF dostupná pro ASP.NET, použijte nástroje pro generování klienta webové služby: [Nástroj Web Services Description Language (WSDL. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Nástroj pro zjišťování webových služeb (Disc. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)a funkci `Add Web Reference` v aplikaci Visual Studio; je nutné povolit publikování metadat. Další informace najdete v tématu [publikování koncových bodů metadat](publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu ukazuje, jak přidat koncový bod WCF, který je kompatibilní s klienty webové služby ASP.NET v kódu a případně v konfiguračním souboru.  
  
### <a name="code"></a>Kód  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Viz také:

- [Interoperabilita s webovými službami ASP.NET](./feature-details/interop-with-aspnet-web-services.md)
