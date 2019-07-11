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
ms.openlocfilehash: c24d6e9c42a091eafbe6d4bdee2bb4e055fd8852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772031"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="29aac-102">ICorDebugType::GetBase – metoda</span><span class="sxs-lookup"><span data-stu-id="29aac-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="29aac-103">Získá ukazatel rozhraní k ICorDebugType, který představuje základní typ, pokud existuje, typu představovaného tímto rozhraním `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="29aac-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29aac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29aac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29aac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29aac-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="29aac-106">[out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje základního typu.</span><span class="sxs-lookup"><span data-stu-id="29aac-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29aac-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29aac-107">Remarks</span></span>  
 <span data-ttu-id="29aac-108">Základní typ pro typ hledání je užitečné implementovat běžné funkce ladicího programu, jako je například tisk si všechna pole objektu nebo její nadřazenou třídu.</span><span class="sxs-lookup"><span data-stu-id="29aac-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29aac-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29aac-109">Requirements</span></span>  
 <span data-ttu-id="29aac-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29aac-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29aac-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29aac-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29aac-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29aac-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29aac-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29aac-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
