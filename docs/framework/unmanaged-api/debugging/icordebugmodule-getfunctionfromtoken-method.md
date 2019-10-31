---
title: ICorDebugModule::GetFunctionFromToken – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: cb966a918c63b4fbc00dcf52819b9384427dfdaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129591"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="00292-102">ICorDebugModule::GetFunctionFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="00292-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="00292-103">Získá funkci, která je určena tokenem metadat.</span><span class="sxs-lookup"><span data-stu-id="00292-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00292-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00292-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00292-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00292-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="00292-106">pro Token metadat `mdMethodDef`, který odkazuje na metadata funkce.</span><span class="sxs-lookup"><span data-stu-id="00292-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="00292-107">mimo Ukazatel na adresu objektu rozhraní ICorDebugFunction, který představuje funkci.</span><span class="sxs-lookup"><span data-stu-id="00292-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00292-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00292-108">Remarks</span></span>  
 <span data-ttu-id="00292-109">Metoda `GetFunctionFromToken` vrátí CORDBG_E_FUNCTION_NOT_IL HRESULT, pokud hodnota předaná v `methodDef` neodkazuje na metodu jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="00292-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00292-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00292-110">Requirements</span></span>  
 <span data-ttu-id="00292-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00292-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00292-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="00292-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00292-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="00292-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00292-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00292-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
