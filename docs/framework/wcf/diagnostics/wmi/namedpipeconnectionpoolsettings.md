---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8c2d4bfc08a503a8d6eb0e8abf6f1e798b90bc83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963212"
---
# <a name="namedpipeconnectionpoolsettings"></a>NamedPipeConnectionPoolSettings
NamedPipeConnectionPoolSettings  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída NamedPipeConnectionPoolSettings nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída NamedPipeConnectionPoolSettings má následující vlastnosti:  
  
### <a name="groupname"></a>GroupName  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Název skupiny fondu připojení používaný prvkem vazby.  
  
### <a name="idletimeout"></a>IdleTimeout  
 Datový typ: datum a čas  
  
 Typ přístupu: jen pro čtení  
  
 Maximální doba, kterou může být připojení nečinné, než je odpojeno.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet odchozích připojení pro každý koncový bod na straně klienta.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
