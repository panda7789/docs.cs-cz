---
title: ICorDebugStringValue::GetLength – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e62539304817432fcab8f3e0958e5a70b371b83d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416943"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="d54b9-102">ICorDebugStringValue::GetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="d54b9-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="d54b9-103">Získá počet znaků v řetězci odkazuje tento ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="d54b9-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d54b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d54b9-104">Syntax</span></span>  
  
```  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d54b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d54b9-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="d54b9-106">[out] Ukazatel na hodnotu, která určuje délku řetězce, který odkazuje toto `ICorDebugStringValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="d54b9-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d54b9-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d54b9-107">Requirements</span></span>  
 <span data-ttu-id="d54b9-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d54b9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d54b9-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d54b9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d54b9-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d54b9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d54b9-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d54b9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
