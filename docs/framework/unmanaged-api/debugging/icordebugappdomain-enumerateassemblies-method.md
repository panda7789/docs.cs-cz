---
title: ICorDebugAppDomain::EnumerateAssemblies – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateAssemblies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateAssemblies
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateAssemblies method [.NET Framework debugging]
- EnumerateAssemblies method [.NET Framework debugging]
ms.assetid: 7add64f9-19a8-46a9-be62-905d5e7d1bd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ce95daaee3c74ac57b107ab8bcb23d41e42cabb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466645"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="f26aa-102">ICorDebugAppDomain::EnumerateAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="f26aa-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="f26aa-103">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="f26aa-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f26aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f26aa-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f26aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f26aa-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="f26aa-106">[out] Ukazatel na adresu icordebugassemblyenum – objekt, který je enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="f26aa-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f26aa-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f26aa-107">Requirements</span></span>  
 <span data-ttu-id="f26aa-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f26aa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f26aa-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f26aa-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f26aa-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f26aa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f26aa-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f26aa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
