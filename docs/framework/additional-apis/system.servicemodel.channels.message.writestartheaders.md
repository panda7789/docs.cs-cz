---
title: Message. WriteStartHeaders – metoda (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: c826e6a3b976e5705e9815586441e8a25b64f76e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214868"
---
# <a name="messagewritestartheaders-method"></a>Message. WriteStartHeaders – metoda

Zapíše počáteční hlavičku do souboru XML voláním metody <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType>.

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a>Parametry

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  Zapisovač, který se používá k zápisu počáteční hlavičky do souboru XML.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `Message.WriteStartHeaders` je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.ServiceModel.Channels>

**Sestavení:** System. ServiceModel. dll

**Verze .NET Framework:** K dispozici od verze 3,0.
