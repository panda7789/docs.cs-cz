---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 68e6a25e4e3f47c556363e2fd5aa8d3bb9946449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
