---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 193000acf2f3c8a0eddb2552559ee40a0f5fced9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída PeerTransportBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída PeerTransportBindingElement má následující vlastnosti:  
  
### <a name="listenipaddress"></a>ListenIPAddress  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 IP adresa, na kterém naslouchá uzlu sdílené zprávy.  
  
### <a name="port"></a>port  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Port síťového rozhraní, v němž je tato vazba procesy peer kanál zprávy.  
  
### <a name="security"></a>Zabezpečení  
 Datový typ: PeerSecuritySettings  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení zabezpečení rovnocenného přenosu.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
