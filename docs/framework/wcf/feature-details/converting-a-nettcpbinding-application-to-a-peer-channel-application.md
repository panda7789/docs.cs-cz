---
title: "Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ee46e34aea14c4ee9ce23c807170104173f2704
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
Můžete vytvořit připojení mezi klienty, kteří používají [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] pomocí vazby, které popisují parametry připojení. Převádění [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace mohly používat peer-to-peer připojení vyžaduje vazbu, která podporuje tuto technologii, při vytváření připojení klienta. Rovnocenného kanálu poskytuje vazbu názvem <xref:System.ServiceModel.NetPeerTcpBinding>, který můžete použít k podobným způsobem <xref:System.ServiceModel.NetTcpBinding>. Hlavní rozdíly týkat překladač služby a definování nastavení zabezpečení.  
  
 Pokud aplikace používá výchozí překladač a nastavení zabezpečení, převod normální klientské nebo serverové aplikace pro používání rovnocenného kanálu zahrnuje Změna názvu vazbu z "NetTcpBinding" na "NetPeerTcpBinding" do aplikace konfigurační soubor – nemáte, chcete-li změnit základní kódu aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
