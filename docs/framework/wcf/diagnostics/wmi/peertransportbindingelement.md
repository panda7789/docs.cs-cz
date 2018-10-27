---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 58bf07b0429ca2435b5aae3683ef69951a10003e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185180"
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třídě PeerTransportBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídě PeerTransportBindingElement má následující vlastnosti:  
  
### <a name="listenipaddress"></a>Třída listenIPAddress  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 IP adresa, na kterém naslouchá partnerský uzel pro zprávy.  
  
### <a name="port"></a>Port  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Port síťového rozhraní, na které bude tato vazba procesy navázání partnerského vztahu mezi kanálu zpráv.  
  
### <a name="security"></a>Zabezpečení  
 Datový typ: PeerSecuritySettings  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení zabezpečení rovnocenného přenosu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
