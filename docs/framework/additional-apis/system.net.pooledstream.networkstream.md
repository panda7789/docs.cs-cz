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
# <a name="pooledstreamnetworkstream-property"></a><span data-ttu-id="ef031-102">PooledStream. NetworkStream – vlastnost</span><span class="sxs-lookup"><span data-stu-id="ef031-102">PooledStream.NetworkStream Property</span></span>

<span data-ttu-id="ef031-103">Získá nebo nastaví síťový datový proud pro `PooledStream` soket.</span><span class="sxs-lookup"><span data-stu-id="ef031-103">Gets or sets the network stream for the `PooledStream` socket.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef031-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef031-104">Syntax</span></span>

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="ef031-105">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ef031-105">Property value</span></span>

<xref:System.Net.Sockets.NetworkStream>  
<span data-ttu-id="ef031-106">Síťový datový proud pro `PooledStream` soket.</span><span class="sxs-lookup"><span data-stu-id="ef031-106">The network stream for the `PooledStream` socket.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef031-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef031-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ef031-108">Vlastnost `PooledStream.NetworkStream` je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="ef031-108">The `PooledStream.NetworkStream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ef031-109">Společnost Microsoft v žádné situaci nepodporuje použití této vlastnosti v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ef031-109">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef031-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef031-110">Requirements</span></span>

<span data-ttu-id="ef031-111">**Obor názvů:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="ef031-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="ef031-112">**Sestavení:** Systém (v System. dll)</span><span class="sxs-lookup"><span data-stu-id="ef031-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="ef031-113">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="ef031-113">**.NET Framework versions:** Available since 2.0.</span></span>
