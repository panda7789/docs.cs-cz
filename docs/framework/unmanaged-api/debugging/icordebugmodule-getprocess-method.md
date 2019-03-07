---
title: ICorDebugModule::GetProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97cecd66462cf6a88012b13dec82dbf617891dd5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493840"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="77c66-102">ICorDebugModule::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="77c66-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="77c66-103">Získá nadřazený proces tento modul.</span><span class="sxs-lookup"><span data-stu-id="77c66-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77c66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77c66-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77c66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77c66-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="77c66-106">[out] Ukazatel na adresu ICorDebugProcess objekt, který představuje proces, který obsahuje tento modul.</span><span class="sxs-lookup"><span data-stu-id="77c66-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77c66-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77c66-107">Requirements</span></span>  
 <span data-ttu-id="77c66-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77c66-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77c66-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77c66-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77c66-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77c66-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77c66-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77c66-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
