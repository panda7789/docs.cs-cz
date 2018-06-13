---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 48b41d2f3f45cd9c590f87151253450962b994de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485294"
---
# <a name="channelpoolsettings"></a>ChannelPoolSettings
ChannelPoolSettings  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ChannelPoolSettings nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ChannelPoolSettings má následující vlastnosti:  
  
### <a name="idletimeout"></a>IdleTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Maximální doba zapůjčení operace dokončit před vypršením časového limitu.  
  
### <a name="maxoutboundchannelsperendpoint"></a>MaxOutboundChannelsPerEndpoint  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet odchozí kanály pro každý koncový bod.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
