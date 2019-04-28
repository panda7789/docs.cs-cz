---
title: ICorDebugCode::IsIL – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a82606d90444c2d543065287780e42da4f8b4943
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750264"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="53fb7-102">ICorDebugCode::IsIL – metoda</span><span class="sxs-lookup"><span data-stu-id="53fb7-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="53fb7-103">Získá hodnotu určující, zda tento "ICorDebugCode" představuje kód, který byl zkompilován v jazyk Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="53fb7-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53fb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53fb7-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53fb7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53fb7-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="53fb7-106">[out] `true` tato `ICorDebugCode` představuje kód, který byl kompilovaný do jazyka MSIL; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="53fb7-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53fb7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53fb7-107">Requirements</span></span>  
 <span data-ttu-id="53fb7-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53fb7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53fb7-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53fb7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53fb7-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53fb7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53fb7-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53fb7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fb7-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53fb7-112">See also</span></span>
