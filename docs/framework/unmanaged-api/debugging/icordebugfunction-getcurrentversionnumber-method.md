---
title: ICorDebugFunction::GetCurrentVersionNumber – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: b47580022b98ea02584a94b3f74b3fd1c276f297
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212903"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="6457d-102">ICorDebugFunction::GetCurrentVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="6457d-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="6457d-103">Získá číslo verze nejnovější úpravy provedené na funkci reprezentované tímto objektem ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="6457d-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6457d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6457d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6457d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6457d-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="6457d-106">mimo Ukazatel na celočíselnou hodnotu, která je číslo verze poslední úpravy provedené u této funkce.</span><span class="sxs-lookup"><span data-stu-id="6457d-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6457d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6457d-107">Remarks</span></span>  
 <span data-ttu-id="6457d-108">Číslo verze nejnovější úpravy provedené v této funkci může být větší než číslo verze samotné funkce.</span><span class="sxs-lookup"><span data-stu-id="6457d-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="6457d-109">Pomocí metody [ICorDebugFunction2:: getčíslo_verze](icordebugfunction2-getversionnumber-method.md) nebo [ICorDebugCode:: getčíslo_verze](icordebugcode-getversionnumber-method.md) načtěte číslo verze funkce.</span><span class="sxs-lookup"><span data-stu-id="6457d-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6457d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6457d-110">Requirements</span></span>  
 <span data-ttu-id="6457d-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6457d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6457d-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6457d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6457d-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6457d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6457d-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6457d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
