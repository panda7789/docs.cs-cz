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
ms.openlocfilehash: a2b76cb59a95082e0cf9c0884b8277cca3c8fe8d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976067"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="dfa2a-102">ICorDebugEval2::NewStringWithLength – metoda</span><span class="sxs-lookup"><span data-stu-id="dfa2a-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="dfa2a-103">Vytvoří řetězec o zadané délce se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="dfa2a-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfa2a-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfa2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfa2a-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="dfa2a-106">pro Ukazatel na hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="dfa2a-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="dfa2a-107">pro Délka řetězce</span><span class="sxs-lookup"><span data-stu-id="dfa2a-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfa2a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfa2a-108">Remarks</span></span>  
 <span data-ttu-id="dfa2a-109">Pokud se očekává, že je koncový znak null řetězce ve spravovaném řetězci, volající `NewStringWithLength` metody musí zajistit, aby délka řetězce zahrnovala koncový znak null.</span><span class="sxs-lookup"><span data-stu-id="dfa2a-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="dfa2a-110">Řetězec je vždy vytvořen v doméně aplikace, ve které je vlákno aktuálně prováděno.</span><span class="sxs-lookup"><span data-stu-id="dfa2a-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa2a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dfa2a-111">Requirements</span></span>  
 <span data-ttu-id="dfa2a-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa2a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa2a-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dfa2a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfa2a-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dfa2a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfa2a-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa2a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
