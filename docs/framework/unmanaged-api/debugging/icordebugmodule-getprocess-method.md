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
ms.openlocfilehash: c10c45c4450e02d633ebeeca15da95b7c95ff0b4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212526"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="82eb0-102">ICorDebugModule::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="82eb0-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="82eb0-103">Získá obsahující proces tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="82eb0-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82eb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82eb0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82eb0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82eb0-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="82eb0-106">mimo Ukazatel na adresu objektu ICorDebugProcess, který představuje proces obsahující tento modul.</span><span class="sxs-lookup"><span data-stu-id="82eb0-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82eb0-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82eb0-107">Requirements</span></span>  
 <span data-ttu-id="82eb0-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82eb0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82eb0-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="82eb0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82eb0-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="82eb0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82eb0-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82eb0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
