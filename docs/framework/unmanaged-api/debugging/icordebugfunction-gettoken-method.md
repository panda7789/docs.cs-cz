---
title: ICorDebugFunction::GetToken – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
ms.openlocfilehash: e542145e888049231a6c5e4cccbb4ee96c62f98b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213254"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="472fd-102">ICorDebugFunction::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="472fd-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="472fd-103">Získá token metadat pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="472fd-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="472fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="472fd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="472fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="472fd-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="472fd-106">mimo Ukazatel na `mdMethodDef` token, který odkazuje na metadata této funkce.</span><span class="sxs-lookup"><span data-stu-id="472fd-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="472fd-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="472fd-107">Requirements</span></span>  
 <span data-ttu-id="472fd-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="472fd-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="472fd-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="472fd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="472fd-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="472fd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="472fd-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="472fd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
