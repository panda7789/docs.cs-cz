---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b9aa7e0d9eaba0181b17b44da1bf871c10af814
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída TcpTransportBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída TcpTransportBindingElement má následující vlastnosti:  
  
### <a name="connectionpoolsettings"></a>ConnectionPoolSettings  
 Datový typ: TcpConnectionPoolSettings  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení fondu připojení.  
  
### <a name="listenbacklog"></a>listenBacklog  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet požadavků ve frontě připojení, které může být dokončena.  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda je povoleno sdílení portů TCP pro toto připojení.  
  
### <a name="teredoenabled"></a>TeredoEnabled  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda je povoleno Teredo (technologie pro adresování klienty, kteří jsou za bránami firewall).  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
