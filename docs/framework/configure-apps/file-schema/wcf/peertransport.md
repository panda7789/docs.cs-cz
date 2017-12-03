---
title: "&lt;– peerTransport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfa8c480524c920ac2f73236b6548072e7805ab2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeertransportgt"></a>&lt;– peerTransport&gt;
Definuje sdílené přenos vlastní vazby.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<– peerTransport >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<peerTransport   
    listenIpAddress="String"  
    maxBufferPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    port="Integer"  
        <security>  
    </security>  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|listenIpAddress|Řetězec, který určuje IP adresu, na kterém bude uzlu sdílené naslouchat zpráv TCP. Výchozí hodnota je `null`.|  
|maxBufferPoolSize|Kladné celé číslo, které určuje maximální velikost fondu vyrovnávací paměti. Výchozí hodnota je 524288.<br /><br /> Mnoho části služby WCF pomocí vyrovnávací paměti. Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu. Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.|  
|MaxReceivedMessageSize|Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlavičky. Odesílatel zprávy obdrží chybu protokolu SOAP po příliš velké vzhledem k příjemce zprávy. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65536.|  
|port|Celé číslo, které určuje, na které tato vazba zpracuje rovnocenné zprávy TCP port síťového rozhraní. Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>. Výchozí hodnota je 0.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|Definuje nastavení zabezpečení pro tento přenos. Tento element je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento přenos nelze použít s smluv, které mají požadavek nebo odpověď operace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
