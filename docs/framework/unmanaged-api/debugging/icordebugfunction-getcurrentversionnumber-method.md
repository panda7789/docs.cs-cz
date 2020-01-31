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
ms.openlocfilehash: 5e080e9aa89816b24aa2eb1b6b1be823922e86fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794523"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="6fcd7-102">ICorDebugFunction::GetCurrentVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="6fcd7-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="6fcd7-103">Získá číslo verze nejnovější úpravy provedené na funkci reprezentované tímto objektem ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="6fcd7-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fcd7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fcd7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fcd7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fcd7-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="6fcd7-106">mimo Ukazatel na celočíselnou hodnotu, která je číslo verze poslední úpravy provedené u této funkce.</span><span class="sxs-lookup"><span data-stu-id="6fcd7-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fcd7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fcd7-107">Remarks</span></span>  
 <span data-ttu-id="6fcd7-108">Číslo verze nejnovější úpravy provedené v této funkci může být větší než číslo verze samotné funkce.</span><span class="sxs-lookup"><span data-stu-id="6fcd7-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="6fcd7-109">Pomocí metody [ICorDebugFunction2:: getčíslo_verze](icordebugfunction2-getversionnumber-method.md) nebo [ICorDebugCode:: getčíslo_verze](icordebugcode-getversionnumber-method.md) načtěte číslo verze funkce.</span><span class="sxs-lookup"><span data-stu-id="6fcd7-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fcd7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fcd7-110">Requirements</span></span>  
 <span data-ttu-id="6fcd7-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fcd7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fcd7-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6fcd7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fcd7-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6fcd7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fcd7-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fcd7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
