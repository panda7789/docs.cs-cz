---
title: "ICorDebugModule::GetSize – metoda"
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
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9474b48526e2ba6292c28e5e66eb97f8e57f2a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="25001-102">ICorDebugModule::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="25001-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="25001-103">Získá velikost v bajtech modulu.</span><span class="sxs-lookup"><span data-stu-id="25001-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25001-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25001-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25001-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25001-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="25001-106">[out] Velikost modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="25001-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="25001-107">Pokud v modulu bylo vytvořeno ze Generátor nativních bitových kopií (NGen.exe), bude velikost modulu nula.</span><span class="sxs-lookup"><span data-stu-id="25001-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25001-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25001-108">Requirements</span></span>  
 <span data-ttu-id="25001-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25001-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25001-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25001-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25001-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25001-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25001-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25001-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
