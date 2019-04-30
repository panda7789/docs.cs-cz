---
title: ICorDebugType::GetBase – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d04bc67013a2227f295ac3a41be027b9f9b04e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946303"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="a21fb-102">ICorDebugType::GetBase – metoda</span><span class="sxs-lookup"><span data-stu-id="a21fb-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="a21fb-103">Získá ukazatel rozhraní k ICorDebugType, který představuje základní typ, pokud existuje, typu představovaného tímto rozhraním `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="a21fb-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a21fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a21fb-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a21fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a21fb-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="a21fb-106">[out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje základního typu.</span><span class="sxs-lookup"><span data-stu-id="a21fb-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a21fb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a21fb-107">Remarks</span></span>  
 <span data-ttu-id="a21fb-108">Základní typ pro typ hledání je užitečné implementovat běžné funkce ladicího programu, jako je například tisk si všechna pole objektu nebo její nadřazenou třídu.</span><span class="sxs-lookup"><span data-stu-id="a21fb-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a21fb-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a21fb-109">Requirements</span></span>  
 <span data-ttu-id="a21fb-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a21fb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a21fb-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a21fb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a21fb-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a21fb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a21fb-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a21fb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
