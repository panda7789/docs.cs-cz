---
title: "ICorDebugModule::GetFunctionFromToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetFunctionFromToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96e458bc8fdcf37f572c1f45ba9c31d15311c8c6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="f8686-102">ICorDebugModule::GetFunctionFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="f8686-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="f8686-103">Získá funkce, která je zadána token metadat.</span><span class="sxs-lookup"><span data-stu-id="f8686-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8686-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8686-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8686-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8686-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="f8686-106">[v] A `mdMethodDef` metadata token, který odkazuje na funkci metadata.</span><span class="sxs-lookup"><span data-stu-id="f8686-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="f8686-107">[out] Ukazatel na adresu objekt rozhraní ICorDebugFunction, který představuje funkci.</span><span class="sxs-lookup"><span data-stu-id="f8686-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8686-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8686-108">Remarks</span></span>  
 <span data-ttu-id="f8686-109">`GetFunctionFromToken` Metoda vrátí CORDBG_E_FUNCTION_NOT_IL HRESULT, pokud je předaná hodnota `methodDef` neodkazuje na metodu (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f8686-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8686-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8686-110">Requirements</span></span>  
 <span data-ttu-id="f8686-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8686-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8686-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8686-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8686-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8686-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8686-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8686-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
