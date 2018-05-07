---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 4a30ad3ddfef5d39942345b0e0d5274eeff8e596
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tcpconnectionpoolsettings"></a>TcpConnectionPoolSettings
TcpConnectionPoolSettings  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída TcpConnectionPoolSettings nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída TcpConnectionPoolSettings má následující vlastnosti:  
  
### <a name="groupname"></a>Název skupiny  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název skupiny fondu připojení používá prvku vazby.  
  
### <a name="idletimeout"></a>IdleTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Maximální dobu pro dokončení před vypršením časového limitu operace zapůjčení.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet odchozí připojení pro každý koncový bod.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
