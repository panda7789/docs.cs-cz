---
title: Třída Channel
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 4b7c66560c0c136a258c527d8a681d491eb50aae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
