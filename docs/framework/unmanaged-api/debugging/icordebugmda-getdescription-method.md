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
ms.openlocfilehash: 998d4baf03123f1ffc174b2a7aeed0ff4a25b001
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133474"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="02769-102">ICorDebugMDA::GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="02769-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="02769-103">Získá řetězec obsahující popis Pomocník spravovaného ladění (MDA) reprezentována [icordebugmda –](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="02769-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02769-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02769-104">Syntax</span></span>  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02769-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02769-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="02769-106">[in] Velikost vyrovnávací paměti pro řetězec, ve kterém bude uložený popis.</span><span class="sxs-lookup"><span data-stu-id="02769-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="02769-107">[out] Ukazatel na počet bajtů vrácených ve vyrovnávací paměti řetězce.</span><span class="sxs-lookup"><span data-stu-id="02769-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="02769-108">[out] Vyrovnávací paměti řetězce obsahující popis MDA.</span><span class="sxs-lookup"><span data-stu-id="02769-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02769-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02769-109">Remarks</span></span>  
 <span data-ttu-id="02769-110">Řetězec může být nulovou délku.</span><span class="sxs-lookup"><span data-stu-id="02769-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02769-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02769-111">Requirements</span></span>  
 <span data-ttu-id="02769-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02769-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02769-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02769-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02769-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02769-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02769-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02769-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02769-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02769-116">See also</span></span>

- [<span data-ttu-id="02769-117">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02769-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="02769-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="02769-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
