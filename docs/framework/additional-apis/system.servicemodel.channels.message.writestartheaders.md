---
title: Message. WriteStartHeaders – metoda (System. ServiceModel. Channels)
author: mairaw
ms.author: mairaw
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: a2c82ee4029c7af0396219f5ded8c999fd01d65b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451176"
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
