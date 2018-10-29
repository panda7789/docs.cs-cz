---
title: Třída Channel
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 108d5f8e3cd092863dbd48e2bb9d180798b091a4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197870"
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
  
 Přístup k typu: jen pro čtení  
  
 Místní koncový bod pro kanál.  
  
### <a name="ref"></a>ref  
 Datový typ: koncového bodu  
  
 Přístup k typu: jen pro čtení  
  
 Odkaz na koncový bod kanálu se připojí k.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Vzdálená adresa připojená ke kanálu.  
  
### <a name="sessionid"></a>SessionId  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Id aktuálního procesu, pokud existuje.  
  
### <a name="type"></a>Typ  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Typ kanálu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.ChannelBase>
