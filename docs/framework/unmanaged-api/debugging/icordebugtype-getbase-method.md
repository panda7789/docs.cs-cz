---
title: "ICorDebugType::GetBase – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c28c88988155cf5e00897858d4306e4cb2ea78a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="f0b76-102">ICorDebugType::GetBase – metoda</span><span class="sxs-lookup"><span data-stu-id="f0b76-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="f0b76-103">Získá ukazatele rozhraní k ICorDebugType, který představuje základní typ, pokud takové existuje, typu představovaný to `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="f0b76-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0b76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0b76-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0b76-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0b76-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="f0b76-106">[out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje základního typu.</span><span class="sxs-lookup"><span data-stu-id="f0b76-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0b76-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0b76-107">Remarks</span></span>  
 <span data-ttu-id="f0b76-108">Základní typ pro typ vyhledávání je užitečné k implementaci běžných funkce ladicího programu, například tisk na všechna pole objekt nebo její nadřazenou třídu.</span><span class="sxs-lookup"><span data-stu-id="f0b76-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0b76-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0b76-109">Requirements</span></span>  
 <span data-ttu-id="f0b76-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0b76-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0b76-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0b76-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0b76-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0b76-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0b76-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0b76-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
