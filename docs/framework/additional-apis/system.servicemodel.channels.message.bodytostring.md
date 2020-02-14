---
title: Message. BodyToString – metoda (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215509"
---
# <a name="messagebodytostring-method"></a>Message. BodyToString – metoda

Převede tělo zprávy na řetězec voláním metody <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType>.

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a>Parametry

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  Zapisovač, který slouží k převodu textu zprávy na řetězec.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `Message.BodyToString` je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.ServiceModel.Channels>

**Sestavení:** System. ServiceModel. dll

**Verze .NET Framework:** K dispozici od verze 3,0.
