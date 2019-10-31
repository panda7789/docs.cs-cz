---
title: ICorDebugModule::GetGlobalVariableValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetGlobalVariableValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type:
- apiref
ms.openlocfilehash: 3afefdc3d704044184ea20d061eb9449458b5060
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129569"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="2fd6e-102">ICorDebugModule::GetGlobalVariableValue – metoda</span><span class="sxs-lookup"><span data-stu-id="2fd6e-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="2fd6e-103">Získá hodnotu zadané globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="2fd6e-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fd6e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fd6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fd6e-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="2fd6e-106">pro Token `mdFieldDef`, který odkazuje na metadata popisující globální proměnnou.</span><span class="sxs-lookup"><span data-stu-id="2fd6e-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="2fd6e-107">mimo Ukazatel na adresu objektu ICorDebugValue, který představuje hodnotu zadané globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="2fd6e-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fd6e-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fd6e-108">Requirements</span></span>  
 <span data-ttu-id="2fd6e-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fd6e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fd6e-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2fd6e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fd6e-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2fd6e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fd6e-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fd6e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
