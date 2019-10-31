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
ms.openlocfilehash: bfe77982b88b2fc96dc2846b9db04df28bfc0c38
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131440"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="f66a1-102">ICorDebugMDA::GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="f66a1-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="f66a1-103">Získá řetězec obsahující popis pomocníka spravovaného ladění (MDA) reprezentovaný [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f66a1-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f66a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f66a1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f66a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f66a1-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f66a1-106">pro Velikost vyrovnávací paměti pro řetězce, která bude obsahovat popis.</span><span class="sxs-lookup"><span data-stu-id="f66a1-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f66a1-107">mimo Ukazatel na počet bajtů vrácených v bufferu řetězce.</span><span class="sxs-lookup"><span data-stu-id="f66a1-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="f66a1-108">mimo Vyrovnávací paměť řetězců obsahující popis MDA.</span><span class="sxs-lookup"><span data-stu-id="f66a1-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f66a1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f66a1-109">Remarks</span></span>  
 <span data-ttu-id="f66a1-110">Délka řetězce může být nulová.</span><span class="sxs-lookup"><span data-stu-id="f66a1-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f66a1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f66a1-111">Requirements</span></span>  
 <span data-ttu-id="f66a1-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f66a1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f66a1-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f66a1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f66a1-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f66a1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f66a1-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f66a1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66a1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f66a1-116">See also</span></span>

- [<span data-ttu-id="f66a1-117">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f66a1-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="f66a1-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="f66a1-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
