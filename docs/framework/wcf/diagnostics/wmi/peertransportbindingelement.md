---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ba9031dad96f12c7c48b03f1da4af1b3adc6dd4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980431"
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
  
### <a name="listenipaddress"></a>ListenIPAddress  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 IP adresa, na kterém naslouchá partnerský uzel pro zprávy.  
  
### <a name="port"></a>Port  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Port síťového rozhraní, na které bude tato vazba procesy navázání partnerského vztahu mezi kanálu zpráv.  
  
### <a name="security"></a>Zabezpečení  
 Datový typ: PeerSecuritySettings  
  
 Typ přístupu: jen pro čtení  
  
 Nastavení zabezpečení rovnocenného přenosu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
