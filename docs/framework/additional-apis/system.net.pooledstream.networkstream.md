---
title: PooledStream. NetworkStream – vlastnost (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.PooledStream.NetworkStream
- System.Net.PooledStream.get_NetworkStream
- System.Net.PooledStream.set_NetworkStream
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 541b8c94b30675c1286b48a2291c3bd3e4aeea0b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847176"
---
# <a name="pooledstreamnetworkstream-property"></a>PooledStream. NetworkStream – vlastnost

Získá nebo nastaví síťový datový proud pro `PooledStream` soket.

## <a name="syntax"></a>Syntaxe

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a>Hodnota vlastnosti

<xref:System.Net.Sockets.NetworkStream>  
Síťový datový proud pro `PooledStream` soket.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Vlastnost `PooledStream.NetworkStream` je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této vlastnosti v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Net>

**Sestavení:** Systém (v System. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
