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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da57ecf0c153d902322798e1927c995a34cb93d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761984"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="cb593-102">ICorDebugMDA::GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="cb593-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="cb593-103">Získá řetězec obsahující popis Pomocník spravovaného ladění (MDA) reprezentována [icordebugmda –](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="cb593-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb593-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb593-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb593-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb593-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="cb593-106">[in] Velikost vyrovnávací paměti pro řetězec, ve kterém bude uložený popis.</span><span class="sxs-lookup"><span data-stu-id="cb593-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cb593-107">[out] Ukazatel na počet bajtů vrácených ve vyrovnávací paměti řetězce.</span><span class="sxs-lookup"><span data-stu-id="cb593-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="cb593-108">[out] Vyrovnávací paměti řetězce obsahující popis MDA.</span><span class="sxs-lookup"><span data-stu-id="cb593-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb593-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb593-109">Remarks</span></span>  
 <span data-ttu-id="cb593-110">Řetězec může být nulovou délku.</span><span class="sxs-lookup"><span data-stu-id="cb593-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb593-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb593-111">Requirements</span></span>  
 <span data-ttu-id="cb593-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb593-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb593-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb593-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb593-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb593-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb593-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb593-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb593-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb593-116">See also</span></span>

- [<span data-ttu-id="cb593-117">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb593-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="cb593-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="cb593-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
