---
title: EnumImportTypes – metoda
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d0aefea7345bc3bf37bdb8d13cb2cda19cfe527
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789952"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="0874c-102">EnumImportTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="0874c-102">EnumImportTypes Method</span></span>

<span data-ttu-id="0874c-103">Vytvoří výčet jednotlivých typů v každém oboru.</span><span class="sxs-lookup"><span data-stu-id="0874c-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="0874c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0874c-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="0874c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0874c-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="0874c-106">Popisovač pro enumerátor.</span><span class="sxs-lookup"><span data-stu-id="0874c-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="0874c-107">Maximální počet typů, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="0874c-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="0874c-108">Přijímá typ tokeny, která nepřekročí `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="0874c-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="0874c-109">Přijímá skutečný počet typů v `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="0874c-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="0874c-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0874c-110">Return Value</span></span>

<span data-ttu-id="0874c-111">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="0874c-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="0874c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0874c-112">Requirements</span></span>

<span data-ttu-id="0874c-113">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="0874c-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="0874c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0874c-114">See also</span></span>

- [<span data-ttu-id="0874c-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0874c-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0874c-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0874c-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0874c-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="0874c-117">ALink API</span></span>](index.md)