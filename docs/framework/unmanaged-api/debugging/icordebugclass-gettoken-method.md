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
ms.openlocfilehash: 6964c931307a40f384ad8a8e355cab0aad575ec6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125775"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="ce5c9-102">ICorDebugClass::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="ce5c9-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="ce5c9-103">Získá token metadat `TypeDef`, který odkazuje na definici této třídy.</span><span class="sxs-lookup"><span data-stu-id="ce5c9-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce5c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce5c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce5c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce5c9-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="ce5c9-106">mimo Ukazatel na token `mdTypeDef`, který odkazuje na definici této třídy.</span><span class="sxs-lookup"><span data-stu-id="ce5c9-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce5c9-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce5c9-107">Requirements</span></span>  
 <span data-ttu-id="ce5c9-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce5c9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce5c9-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ce5c9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce5c9-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ce5c9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce5c9-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce5c9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5c9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce5c9-112">See also</span></span>

- [<span data-ttu-id="ce5c9-113">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="ce5c9-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
