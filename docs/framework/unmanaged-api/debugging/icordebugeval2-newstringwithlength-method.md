---
title: ICorDebugEval2::NewStringWithLength – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b84a2fad53feda2996515781035c0eaad5828d54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666987"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="bdb1c-102">ICorDebugEval2::NewStringWithLength – metoda</span><span class="sxs-lookup"><span data-stu-id="bdb1c-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="bdb1c-103">Řetězce zadané délky, vytvoří se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="bdb1c-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdb1c-104">Syntax</span></span>  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdb1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bdb1c-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="bdb1c-106">[in] Ukazatel na hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="bdb1c-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="bdb1c-107">[in] Délka řetězce.</span><span class="sxs-lookup"><span data-stu-id="bdb1c-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdb1c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bdb1c-108">Remarks</span></span>  
 <span data-ttu-id="bdb1c-109">Pokud je na konci řetězce znak null je očekávané ve spravované řetězce volající `NewStringWithLength` – metoda musíte zajistit, že obsahuje délku řetězce znakem null.</span><span class="sxs-lookup"><span data-stu-id="bdb1c-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="bdb1c-110">Řetězec se vždy vytvoří v aplikační doméně, ve které vlákno právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="bdb1c-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdb1c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bdb1c-111">Requirements</span></span>  
 <span data-ttu-id="bdb1c-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdb1c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdb1c-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdb1c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdb1c-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdb1c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdb1c-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdb1c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
