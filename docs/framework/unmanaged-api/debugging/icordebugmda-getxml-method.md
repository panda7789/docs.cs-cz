---
title: ICorDebugMDA::GetXML – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e78b8a2069671d0fe790956ca914225325a78bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916614"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="371fc-102">ICorDebugMDA::GetXML – metoda</span><span class="sxs-lookup"><span data-stu-id="371fc-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="371fc-103">Získá úplný datový proud XML spojené s Pomocník spravovaného ladění (MDA) reprezentována [icordebugmda –](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="371fc-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="371fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="371fc-104">Syntax</span></span>  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="371fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="371fc-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="371fc-106">[in] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="371fc-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="371fc-107">[out] Ukazatel na délku datového proudu XML.</span><span class="sxs-lookup"><span data-stu-id="371fc-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="371fc-108">[out] Pole pro uložení datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="371fc-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="371fc-109">Pole může být prázdný.</span><span class="sxs-lookup"><span data-stu-id="371fc-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="371fc-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="371fc-110">Remarks</span></span>  
 <span data-ttu-id="371fc-111">`GetXML` Metoda může potenciálně ovlivnit výkon, v závislosti na velikosti související datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="371fc-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="371fc-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="371fc-112">Requirements</span></span>  
 <span data-ttu-id="371fc-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="371fc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="371fc-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="371fc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="371fc-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="371fc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="371fc-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="371fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="371fc-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="371fc-117">See also</span></span>

- [<span data-ttu-id="371fc-118">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="371fc-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="371fc-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="371fc-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
