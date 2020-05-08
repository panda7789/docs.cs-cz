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
ms.openlocfilehash: 880c234462ac369ead06578730f3c14532c466e9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895289"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="8f6da-102">ICorDebugAppDomain::EnumerateAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="8f6da-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="8f6da-103">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="8f6da-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f6da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f6da-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f6da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f6da-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="8f6da-106">mimo Ukazatel na adresu objektu ICorDebugAssemblyEnum, který je enumerátorem sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="8f6da-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f6da-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f6da-107">Requirements</span></span>  
 <span data-ttu-id="8f6da-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f6da-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f6da-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f6da-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f6da-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8f6da-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f6da-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f6da-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
