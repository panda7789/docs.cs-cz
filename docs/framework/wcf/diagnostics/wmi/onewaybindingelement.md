---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47de8c2449c46b12b8d10ac2a5269a18d1454f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída Třída OneWayBindingElement nedefinuje žádné metody.  
  
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
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda je směrovatelné paketu.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
