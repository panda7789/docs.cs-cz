---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 016ff823eb2c84a9f54c0763edadef1224e31517
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168737"
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
  
 Typ přístupu: jen pro čtení  
  
 Nastavení fondu kanálu.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet přijatých kanálů.  
  
### <a name="packetroutable"></a>PacketRoutable  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota, která určuje, zda je balíček směrovatelný.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
