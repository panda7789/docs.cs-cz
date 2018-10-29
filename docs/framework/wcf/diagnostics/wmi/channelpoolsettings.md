---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: d763be92243768bce9fdaefcd3e3575effac464b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200480"
---
# <a name="channelpoolsettings"></a>ChannelPoolSettings
ChannelPoolSettings  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Datový typ: datum a čas  
  
 Přístup k typu: jen pro čtení  
  
 Maximální doba, kterou může být připojení nečinné, než je odpojeno.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Datový typ: datum a čas  
  
 Přístup k typu: jen pro čtení  
  
 Maximální doba ukončení operace zapůjčení před vypršením časového limitu.  
  
### <a name="maxoutboundchannelsperendpoint"></a>MaxOutboundChannelsPerEndpoint  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet odchozích kanálů pro každý koncový bod.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
