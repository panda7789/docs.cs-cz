---
title: ICorDebugGuidToTypeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: 76cab0b8b5f16f24c62e31be2707c95c7e557034
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777642"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="3f7dd-102">ICorDebugGuidToTypeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="3f7dd-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="3f7dd-103">Získá zadaný počet instancí [CorDebugGuidToTypeMapping –](cordebugguidtotypemapping-structure.md) , které mapují identifikátory GUID na informace typu.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-103">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f7dd-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f7dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f7dd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3f7dd-106">pro Počet objektů mapování typu GUID na typ, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="3f7dd-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt [CorDebugGuidToTypeMapping –](cordebugguidtotypemapping-structure.md) , který MAPUJE prostředí Windows Runtime GUID na odpovídající objekt ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3f7dd-108">mimo Ukazatel na počet [CorDebugGuidToTypeMapping –ch](cordebugguidtotypemapping-structure.md) objektů, které jsou ve skutečnosti vráceny v `values`.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f7dd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f7dd-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f7dd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f7dd-110">Requirements</span></span>  
 <span data-ttu-id="3f7dd-111">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="3f7dd-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="3f7dd-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3f7dd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f7dd-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3f7dd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f7dd-114">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f7dd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7dd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f7dd-115">See also</span></span>

- [<span data-ttu-id="3f7dd-116">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f7dd-116">ICorDebugGuidToTypeEnum Interface</span></span>](icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="3f7dd-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3f7dd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
