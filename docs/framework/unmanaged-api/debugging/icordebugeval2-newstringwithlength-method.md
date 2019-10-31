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
ms.openlocfilehash: 3836b6c08098d38516c8a25260fb28998a2317fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084786"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="31d1b-102">ICorDebugEval2::NewStringWithLength – metoda</span><span class="sxs-lookup"><span data-stu-id="31d1b-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="31d1b-103">Vytvoří řetězec o zadané délce se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="31d1b-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31d1b-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31d1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31d1b-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="31d1b-106">pro Ukazatel na hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="31d1b-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="31d1b-107">pro Délka řetězce</span><span class="sxs-lookup"><span data-stu-id="31d1b-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31d1b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31d1b-108">Remarks</span></span>  
 <span data-ttu-id="31d1b-109">Pokud se očekává, že koncová hodnota řetězce null je ve spravovaném řetězci, volající metody `NewStringWithLength` musí zajistit, aby délka řetězce zahrnovala koncový znak null.</span><span class="sxs-lookup"><span data-stu-id="31d1b-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="31d1b-110">Řetězec je vždy vytvořen v doméně aplikace, ve které je vlákno aktuálně prováděno.</span><span class="sxs-lookup"><span data-stu-id="31d1b-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31d1b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31d1b-111">Requirements</span></span>  
 <span data-ttu-id="31d1b-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31d1b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d1b-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="31d1b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31d1b-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="31d1b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31d1b-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d1b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
