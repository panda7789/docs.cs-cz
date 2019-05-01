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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989533"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="a3217-102">ICorDebugAppDomain::EnumerateAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="a3217-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="a3217-103">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="a3217-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3217-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3217-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3217-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3217-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="a3217-106">[out] Ukazatel na adresu icordebugassemblyenum – objekt, který je enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="a3217-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3217-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3217-107">Requirements</span></span>  
 <span data-ttu-id="a3217-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3217-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3217-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3217-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3217-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3217-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3217-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3217-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
