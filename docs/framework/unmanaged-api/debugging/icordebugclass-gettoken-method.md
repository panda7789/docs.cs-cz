---
title: ICorDebugClass::GetToken – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f67bd427c83385b2433b9f2e97f0b54e3b29a76f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401060"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="c7d70-102">ICorDebugClass::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="c7d70-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="c7d70-103">Získá `TypeDef` metadata token, který odkazuje na definici této třídy.</span><span class="sxs-lookup"><span data-stu-id="c7d70-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7d70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7d70-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7d70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7d70-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="c7d70-106">[out] Ukazatel na `mdTypeDef` token, který odkazuje na definici této třídy.</span><span class="sxs-lookup"><span data-stu-id="c7d70-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d70-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7d70-107">Requirements</span></span>  
 <span data-ttu-id="c7d70-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7d70-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7d70-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7d70-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7d70-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7d70-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7d70-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7d70-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d70-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7d70-112">See Also</span></span>  
 [<span data-ttu-id="c7d70-113">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="c7d70-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
