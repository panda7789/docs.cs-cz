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
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448731"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="9ee94-102">EnumImportTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="9ee94-102">EnumImportTypes Method</span></span>

<span data-ttu-id="9ee94-103">Vytvoří výčet každého typu v jednotlivých oborech.</span><span class="sxs-lookup"><span data-stu-id="9ee94-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ee94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ee94-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="9ee94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ee94-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="9ee94-106">Popisovač pro enumerátor</span><span class="sxs-lookup"><span data-stu-id="9ee94-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="9ee94-107">Maximální počet typů, které se mají načíst</span><span class="sxs-lookup"><span data-stu-id="9ee94-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="9ee94-108">Přijímá tokeny typu, nepřekročí `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="9ee94-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="9ee94-109">Přijímá skutečný počet typů v `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="9ee94-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ee94-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9ee94-110">Return Value</span></span>

<span data-ttu-id="9ee94-111">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9ee94-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ee94-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ee94-112">Requirements</span></span>

<span data-ttu-id="9ee94-113">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="9ee94-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="9ee94-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ee94-114">See also</span></span>

- [<span data-ttu-id="9ee94-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ee94-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9ee94-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ee94-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9ee94-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="9ee94-117">ALink API</span></span>](index.md)
