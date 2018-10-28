---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 34220a3651819978f5f597fdc67d54630ec5e059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195811"
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída OneWayBindingElement Třída nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída OneWayBindingElement třída má následující vlastnosti:  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 Datový typ: ChannelPoolSettings  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení fondu kanálu.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet přijatých kanálů.  
  
### <a name="packetroutable"></a>PacketRoutable  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda je balíček směrovatelný.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
