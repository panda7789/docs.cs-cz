---
title: Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 9cc73beeffc9daa9883832b3a6bedd0ff438095c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
Můžete vytvořit připojení mezi klienty, kteří používají [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] pomocí vazby, které popisují parametry připojení. Převádění [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace mohly používat peer-to-peer připojení vyžaduje vazbu, která podporuje tuto technologii, při vytváření připojení klienta. Rovnocenného kanálu poskytuje vazbu názvem <xref:System.ServiceModel.NetPeerTcpBinding>, který můžete použít k podobným způsobem <xref:System.ServiceModel.NetTcpBinding>. Hlavní rozdíly týkat překladač služby a definování nastavení zabezpečení.  
  
 Pokud aplikace používá výchozí překladač a nastavení zabezpečení, převod normální klientské nebo serverové aplikace pro používání rovnocenného kanálu zahrnuje Změna názvu vazbu z "NetTcpBinding" na "NetPeerTcpBinding" do aplikace konfigurační soubor – nemáte, chcete-li změnit základní kódu aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
