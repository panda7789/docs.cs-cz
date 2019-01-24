---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 0d5dc5c9b9bf2313d18c9fadb1a2adb87c1b11b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610783"
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
  
### <a name="connectionpoolsettings"></a>ConnectionPoolSettings  
 Datový typ: TcpConnectionPoolSettings  
  
 Typ přístupu: jen pro čtení  
  
 Nastavení fondu připojení.  
  
### <a name="listenbacklog"></a>listenBacklog  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet připojení zařazených do fronty požadavků, které mohou být nevyřízeny.  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Logická hodnota určující, zda je pro toto připojení povoleno sdílení portu TCP.  
  
### <a name="teredoenabled"></a>TeredoEnabled  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Logická hodnota určující, zda je povolena Teredo (technologie pro oslovování klientů, kteří jsou za firewally).  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
