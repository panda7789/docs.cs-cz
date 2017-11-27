---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5038d093333eca9ca191c3ecae4cfa889d723276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
