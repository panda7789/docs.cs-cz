---
title: "Třída Channel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 073f0a2a2731a08acd914a7dd85cb2b419d98128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="channel-class"></a>Třída Channel
Kanál  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída Channel nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída Channel má následující vlastnosti.  
  
### <a name="localaddress"></a>LocalAddress  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Místní koncový bod pro kanál.  
  
### <a name="ref"></a>ref  
 Datový typ: koncový bod  
  
 Přístup k typu: jen pro čtení  
  
 Odkaz na koncový bod kanálu se připojí k.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Vzdálená adresa spojená s kanálem.  
  
### <a name="sessionid"></a>SessionId  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Aktuální relace Id, pokud existuje.  
  
### <a name="type"></a>Typ  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Typ kanálu.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.ChannelBase>
