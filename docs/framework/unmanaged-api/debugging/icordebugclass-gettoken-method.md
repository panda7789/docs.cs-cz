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
ms.openlocfilehash: 3433f5f69927afb501c2596571f138e3a69fabb6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894115"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="9ecac-102">ICorDebugClass::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="9ecac-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="9ecac-103">Získá token `TypeDef` metadat, který odkazuje na definici této třídy.</span><span class="sxs-lookup"><span data-stu-id="9ecac-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ecac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ecac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ecac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ecac-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="9ecac-106">mimo Ukazatel na `mdTypeDef` token, který odkazuje na definici této třídy.</span><span class="sxs-lookup"><span data-stu-id="9ecac-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ecac-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ecac-107">Requirements</span></span>  
 <span data-ttu-id="9ecac-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ecac-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ecac-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9ecac-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ecac-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9ecac-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ecac-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ecac-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecac-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ecac-112">See also</span></span>

- [<span data-ttu-id="9ecac-113">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="9ecac-113">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
