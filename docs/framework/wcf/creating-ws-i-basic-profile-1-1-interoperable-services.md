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
ms.workload: dotnet
ms.openlocfilehash: 61c4f26c9880d8a7f6a8fb356bafcc0d312509dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Vytváření interoperabilních služeb WS-I Basic Profile 1.1
Ke konfiguraci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] koncový bod služby jako vzájemná spolupráce s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webových služeb klientům:  
  
-   Použití <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ vazby pro svůj koncový bod služby.  
  
-   Zpětné volání a funkce kontrakt relace ani chování transakce nelze použít na váš koncový bod služby  
  
 Volitelně můžete umožnit podporu pro protokol HTTPS a ověření klienta transportní vrstvy na vazby.  
  
 Následující funkce sady <xref:System.ServiceModel.BasicHttpBinding> třída, aby funkce nad rámec WS-I Basic Profile 1.1:  
  
-   Kódování zpráv zpráva přenosu optimalizace mechanismus (MTOM) řízené <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> vlastnost. V jeho výchozí hodnotu, která je ponechte tuto vlastnost <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> nechcete použít MTOM.  
  
-   Řídí zabezpečení zpráv <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> hodnota poskytuje podporu WS-zabezpečení, které jsou kompatibilní s WS-I Basic 1.0 profil zabezpečení. V jeho výchozí hodnotu, která je ponechte tuto vlastnost <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> nechcete použít WS-zabezpečení.  
  
 Chcete, aby metadata pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, které jsou k dispozici pro [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], pomocí nástrojů generování klienta webové služby: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/en-us/b9210348-8bc2-4367-8c91-d1a04b403e88), [(nástroj pro zjišťování webové služby Disco.exe)](http://msdn.microsoft.com/en-us/acd88078-c581-42bc-94ca-6633e2851979)a `Add Web Reference` funkci v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; je nutné povolit metadata publikace. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Publikování kocových bodů metadat](../../../docs/framework/wcf/publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu ukazuje, jak přidat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] koncový bod, který je kompatibilní s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webových služeb klientům v kódu a případně v konfiguračním souboru.  
  
### <a name="code"></a>Kód  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Viz také  
 [Interoperabilita s webovými službami ASP.NET](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
