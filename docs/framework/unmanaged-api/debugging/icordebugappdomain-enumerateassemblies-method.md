---
title: "ICorDebugAppDomain::EnumerateAssemblies – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.EnumerateAssemblies
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::EnumerateAssemblies
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateAssemblies method [.NET Framework debugging]
- EnumerateAssemblies method [.NET Framework debugging]
ms.assetid: 7add64f9-19a8-46a9-be62-905d5e7d1bd8
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dde65b9a3add4c0b7cd4dea90d5cebaae9f05794
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="31e7d-102">ICorDebugAppDomain::EnumerateAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="31e7d-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="31e7d-103">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="31e7d-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31e7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31e7d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31e7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31e7d-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="31e7d-106">[out] Ukazatel na adresu ICorDebugAssemblyEnum objekt, který je enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="31e7d-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31e7d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31e7d-107">Requirements</span></span>  
 <span data-ttu-id="31e7d-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31e7d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31e7d-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31e7d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31e7d-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31e7d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31e7d-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31e7d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
