---
title: SslState. SslProtocol – vlastnost (System .NET. Security)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 6983ac071dad29b240308031ecd0a3562a6856e4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847197"
---
# <a name="sslstatesslprotocol-property"></a>SslState. SslProtocol – vlastnost

Získá verze protokolu SSL.

## <a name="syntax"></a>Syntaxe

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a>Hodnota vlastnosti

<xref:System.Security.Authentication.SslProtocols>  
Bitová kombinace hodnot výčtu, která určuje verze protokolu SSL.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Vlastnost `SslState.SslProtocol` je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této vlastnosti v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Net.Security>

**Sestavení:** Systém (v System. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
