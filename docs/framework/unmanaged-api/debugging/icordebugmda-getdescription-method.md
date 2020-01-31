---
title: ICorDebugMDA::GetDescription – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
ms.openlocfilehash: e3744cbfa08de30c53f15c457034b50e2fc5d283
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793240"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="85355-102">ICorDebugMDA::GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="85355-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="85355-103">Získá řetězec obsahující popis pomocníka spravovaného ladění (MDA) reprezentovaný [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="85355-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85355-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85355-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85355-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85355-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="85355-106">pro Velikost vyrovnávací paměti pro řetězce, která bude obsahovat popis.</span><span class="sxs-lookup"><span data-stu-id="85355-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="85355-107">mimo Ukazatel na počet bajtů vrácených v bufferu řetězce.</span><span class="sxs-lookup"><span data-stu-id="85355-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="85355-108">mimo Vyrovnávací paměť řetězců obsahující popis MDA.</span><span class="sxs-lookup"><span data-stu-id="85355-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85355-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85355-109">Remarks</span></span>  
 <span data-ttu-id="85355-110">Délka řetězce může být nulová.</span><span class="sxs-lookup"><span data-stu-id="85355-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85355-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85355-111">Requirements</span></span>  
 <span data-ttu-id="85355-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85355-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85355-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85355-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85355-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85355-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85355-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85355-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85355-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85355-116">See also</span></span>

- [<span data-ttu-id="85355-117">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85355-117">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="85355-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="85355-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
