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
ms.openlocfilehash: c4f33bb15a351be5fe8318dcc3339d429dec039e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750759"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="a427c-102">ICorDebugClass::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="a427c-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="a427c-103">Získá `TypeDef` token metadat, který odkazuje na definici této třídy.</span><span class="sxs-lookup"><span data-stu-id="a427c-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a427c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a427c-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a427c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a427c-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="a427c-106">[out] Ukazatel `mdTypeDef` token, který odkazuje na definici této třídy.</span><span class="sxs-lookup"><span data-stu-id="a427c-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a427c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a427c-107">Requirements</span></span>  
 <span data-ttu-id="a427c-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a427c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a427c-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a427c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a427c-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a427c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a427c-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a427c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a427c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a427c-112">See also</span></span>

- [<span data-ttu-id="a427c-113">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="a427c-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
