---
title: Třída Channel
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: f60a3946617b0994db1ba9e9ddf43be863be81f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964078"
---
# <a name="channel-class"></a>Třída Channel
Kanál  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Třída kanálu nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída kanálu má následující vlastnosti.  
  
### <a name="localaddress"></a>LocalAddress  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Místní koncový bod pro kanál.  
  
### <a name="ref"></a>ref  
 Datový typ: Koncový bod  
  
 Typ přístupu: jen pro čtení  
  
 Odkaz na koncový bod kanálu se připojí k.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Vzdálená adresa připojená ke kanálu.  
  
### <a name="sessionid"></a>SessionId  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Id aktuálního procesu, pokud existuje.  
  
### <a name="type"></a>Type  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Typ kanálu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.ChannelBase>
