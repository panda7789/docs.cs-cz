---
title: "ICorDebugType::GetBase – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetBase
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de00e519b43d486e70d5ed8165eed01b59d6e725
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="141d4-102">ICorDebugType::GetBase – metoda</span><span class="sxs-lookup"><span data-stu-id="141d4-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="141d4-103">Získá ukazatele rozhraní k ICorDebugType, který představuje základní typ, pokud takové existuje, typu představovaný to `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="141d4-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="141d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="141d4-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="141d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="141d4-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="141d4-106">[out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje základního typu.</span><span class="sxs-lookup"><span data-stu-id="141d4-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="141d4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="141d4-107">Remarks</span></span>  
 <span data-ttu-id="141d4-108">Základní typ pro typ vyhledávání je užitečné k implementaci běžných funkce ladicího programu, například tisk na všechna pole objekt nebo její nadřazenou třídu.</span><span class="sxs-lookup"><span data-stu-id="141d4-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="141d4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="141d4-109">Requirements</span></span>  
 <span data-ttu-id="141d4-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="141d4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="141d4-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="141d4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="141d4-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="141d4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="141d4-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="141d4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
