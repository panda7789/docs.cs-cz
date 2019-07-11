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
ms.openlocfilehash: b944112ce0b00e84da6243e2e48917e2318b0f1c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746840"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="a2af6-102">ICorDebugClass::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="a2af6-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="a2af6-103">Získá `TypeDef` token metadat, který odkazuje na definici této třídy.</span><span class="sxs-lookup"><span data-stu-id="a2af6-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2af6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2af6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2af6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2af6-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="a2af6-106">[out] Ukazatel `mdTypeDef` token, který odkazuje na definici této třídy.</span><span class="sxs-lookup"><span data-stu-id="a2af6-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2af6-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2af6-107">Requirements</span></span>  
 <span data-ttu-id="a2af6-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2af6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2af6-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2af6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2af6-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2af6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2af6-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2af6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2af6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2af6-112">See also</span></span>

- [<span data-ttu-id="a2af6-113">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="a2af6-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
