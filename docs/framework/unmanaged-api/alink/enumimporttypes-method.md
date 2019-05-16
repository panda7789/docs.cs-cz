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
ms.openlocfilehash: 0cd154ac90418dd0f6f476151686ff670c01c98c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632235"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="f6549-102">EnumImportTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="f6549-102">EnumImportTypes Method</span></span>

<span data-ttu-id="f6549-103">Vytvoří výčet jednotlivých typů v každém oboru.</span><span class="sxs-lookup"><span data-stu-id="f6549-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="f6549-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6549-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="f6549-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6549-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="f6549-106">Popisovač pro enumerátor.</span><span class="sxs-lookup"><span data-stu-id="f6549-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="f6549-107">Maximální počet typů, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="f6549-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="f6549-108">Přijímá typ tokeny, která nepřekročí `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="f6549-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="f6549-109">Přijímá skutečný počet typů v `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="f6549-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f6549-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f6549-110">Return Value</span></span>

<span data-ttu-id="f6549-111">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="f6549-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="f6549-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6549-112">Requirements</span></span>

<span data-ttu-id="f6549-113">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="f6549-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="f6549-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6549-114">See also</span></span>

- [<span data-ttu-id="f6549-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6549-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f6549-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6549-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="f6549-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="f6549-117">ALink API</span></span>](index.md)
