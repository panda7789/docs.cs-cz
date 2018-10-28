---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 04326484bbf1f07c66ad8fb401642880f9ba8c6e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193926"
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
  
### <a name="connectionpoolsettings"></a>connectionPoolSettings  
 Datový typ: TcpConnectionPoolSettings  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení fondu připojení.  
  
### <a name="listenbacklog"></a>listenBacklog  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet připojení zařazených do fronty požadavků, které mohou být nevyřízeny.  
  
### <a name="portsharingenabled"></a>portSharingEnabled  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota určující, zda je pro toto připojení povoleno sdílení portu TCP.  
  
### <a name="teredoenabled"></a>teredoEnabled  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota určující, zda je povolena Teredo (technologie pro oslovování klientů, kteří jsou za firewally).  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
