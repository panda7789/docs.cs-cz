---
title: ICorDebugMDA::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0dfe2bb234631a733248066e8475c135de288e63
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737595"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="02f81-102">ICorDebugMDA::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="02f81-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="02f81-103">Získá řetězec obsahující název pomocníka spravovaného ladění (MDA) reprezentována [icordebugmda –](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="02f81-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02f81-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02f81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02f81-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="02f81-106">[in] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="02f81-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="02f81-107">[out] Ukazatel na délka názvu.</span><span class="sxs-lookup"><span data-stu-id="02f81-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="02f81-108">[out] Pole pro uložení názvu.</span><span class="sxs-lookup"><span data-stu-id="02f81-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02f81-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02f81-109">Remarks</span></span>  
 <span data-ttu-id="02f81-110">MDA názvy jsou jedinečné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="02f81-110">MDA names are unique values.</span></span> <span data-ttu-id="02f81-111">`GetName` Metody je vhodné výkonu alternativou k získání datový proud XML a extrahování název z datového proudu na základě schématu.</span><span class="sxs-lookup"><span data-stu-id="02f81-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02f81-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02f81-112">Requirements</span></span>  
 <span data-ttu-id="02f81-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02f81-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02f81-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02f81-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02f81-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02f81-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02f81-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02f81-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f81-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02f81-117">See also</span></span>
- [<span data-ttu-id="02f81-118">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02f81-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="02f81-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="02f81-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
