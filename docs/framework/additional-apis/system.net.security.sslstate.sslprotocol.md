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
# <a name="sslstatesslprotocol-property"></a><span data-ttu-id="299cc-102">SslState. SslProtocol – vlastnost</span><span class="sxs-lookup"><span data-stu-id="299cc-102">SslState.SslProtocol Property</span></span>

<span data-ttu-id="299cc-103">Získá verze protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="299cc-103">Gets the SSL protocol versions.</span></span>

## <a name="syntax"></a><span data-ttu-id="299cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="299cc-104">Syntax</span></span>

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a><span data-ttu-id="299cc-105">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="299cc-105">Property value</span></span>

<xref:System.Security.Authentication.SslProtocols>  
<span data-ttu-id="299cc-106">Bitová kombinace hodnot výčtu, která určuje verze protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="299cc-106">A bitwise combination of the enumeration values that specify the SSL protocol versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="299cc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="299cc-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="299cc-108">Vlastnost `SslState.SslProtocol` je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="299cc-108">The `SslState.SslProtocol` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="299cc-109">Společnost Microsoft v žádné situaci nepodporuje použití této vlastnosti v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="299cc-109">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="299cc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="299cc-110">Requirements</span></span>

<span data-ttu-id="299cc-111">**Obor názvů:** <xref:System.Net.Security></span><span class="sxs-lookup"><span data-stu-id="299cc-111">**Namespace:** <xref:System.Net.Security></span></span>

<span data-ttu-id="299cc-112">**Sestavení:** Systém (v System. dll)</span><span class="sxs-lookup"><span data-stu-id="299cc-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="299cc-113">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="299cc-113">**.NET Framework versions:** Available since 2.0.</span></span>
