---
title: ICorDebugEval::NewString – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: 8a5d421bf0eb8ec5a34fe21d6efc79bbe56c294c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137647"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="297d1-102">ICorDebugEval::NewString – metoda</span><span class="sxs-lookup"><span data-stu-id="297d1-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="297d1-103">Přidělí novou instanci řetězce se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="297d1-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="297d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="297d1-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="297d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="297d1-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="297d1-106">pro Ukazatel na obsah řetězce.</span><span class="sxs-lookup"><span data-stu-id="297d1-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="297d1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="297d1-107">Remarks</span></span>  
 <span data-ttu-id="297d1-108">Řetězec je vždy vytvořen v doméně aplikace, ve které je vlákno aktuálně prováděno.</span><span class="sxs-lookup"><span data-stu-id="297d1-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="297d1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="297d1-109">Requirements</span></span>  
 <span data-ttu-id="297d1-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="297d1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="297d1-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="297d1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="297d1-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="297d1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="297d1-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="297d1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
