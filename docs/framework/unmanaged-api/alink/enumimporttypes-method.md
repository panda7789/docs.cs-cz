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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355737"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="c9ed0-102">EnumImportTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="c9ed0-102">EnumImportTypes Method</span></span>

<span data-ttu-id="c9ed0-103">Vytvoří výčet jednotlivých typů v každém oboru.</span><span class="sxs-lookup"><span data-stu-id="c9ed0-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9ed0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9ed0-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="c9ed0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9ed0-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="c9ed0-106">Popisovač pro enumerátor.</span><span class="sxs-lookup"><span data-stu-id="c9ed0-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="c9ed0-107">Maximální počet typů, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="c9ed0-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="c9ed0-108">Přijímá typ tokeny, která nepřekročí `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="c9ed0-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="c9ed0-109">Přijímá skutečný počet typů v `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="c9ed0-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="c9ed0-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c9ed0-110">Return Value</span></span>

<span data-ttu-id="c9ed0-111">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="c9ed0-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="c9ed0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9ed0-112">Requirements</span></span>

<span data-ttu-id="c9ed0-113">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="c9ed0-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="c9ed0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9ed0-114">See also</span></span>

- [<span data-ttu-id="c9ed0-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9ed0-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c9ed0-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9ed0-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c9ed0-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="c9ed0-117">ALink API</span></span>](index.md)