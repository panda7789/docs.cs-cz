---
title: Typu MemoryStream není. InternalGetOriginAndLength – metoda (System.IO)
author: mairaw
ms.author: mairaw
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d2bfa087fe2fb247f963cfa687c27056363d5696
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284029"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a><span data-ttu-id="19e53-102">Typu MemoryStream není. InternalGetOriginAndLength – metoda</span><span class="sxs-lookup"><span data-stu-id="19e53-102">MemoryStream.InternalGetOriginAndLength method</span></span>

<span data-ttu-id="19e53-103">Získá interní hodnoty původu a délky streamu paměti.</span><span class="sxs-lookup"><span data-stu-id="19e53-103">Gets the internal values of origin and length of the memory stream.</span></span>

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a><span data-ttu-id="19e53-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="19e53-104">Parameters</span></span>

- <span data-ttu-id="19e53-105">`origin` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="19e53-105">`origin` <xref:System.Int32></span></span>\
  <span data-ttu-id="19e53-106">Když tato metoda vrátí hodnotu, posun pole bajtů zadané při vytváření nového objektu <xref:System.IO.MemoryStream>.</span><span class="sxs-lookup"><span data-stu-id="19e53-106">When this method returns, the offset of the byte array specified when creating a new <xref:System.IO.MemoryStream> object.</span></span> <span data-ttu-id="19e53-107">Obsahuje 0, pokud bylo pole bajtů vytvořeno pomocí <xref:System.IO.MemoryStream>.</span><span class="sxs-lookup"><span data-stu-id="19e53-107">Contains 0 if the byte array was created by <xref:System.IO.MemoryStream>.</span></span>

- <span data-ttu-id="19e53-108">`length` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="19e53-108">`length` <xref:System.Int32></span></span>\
  <span data-ttu-id="19e53-109">Až tato metoda vrátí hodnotu, počet bajtů v paměťovém proudu.</span><span class="sxs-lookup"><span data-stu-id="19e53-109">When this method returns, the number of bytes within the memory stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="19e53-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19e53-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="19e53-111">Metoda `MemoryStream.InternalGetOriginAndLength` je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="19e53-111">The `MemoryStream.InternalGetOriginAndLength` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="19e53-112">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="19e53-112">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="19e53-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19e53-113">Requirements</span></span>

<span data-ttu-id="19e53-114">**Obor názvů:** <xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="19e53-114">**Namespace:** <xref:System.IO></span></span>

<span data-ttu-id="19e53-115">**Sestavení:** mscorlib. dll (v mscorlib. dll)</span><span class="sxs-lookup"><span data-stu-id="19e53-115">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="19e53-116">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="19e53-116">**.NET Framework versions:** Available since 2.0.</span></span>
