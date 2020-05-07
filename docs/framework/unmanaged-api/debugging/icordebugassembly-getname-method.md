---
title: ICorDebugAssembly::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
ms.openlocfilehash: daf5319f5d57f44cb20ce9f28d3c7b84c7015ff6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894908"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="242be-102">ICorDebugAssembly::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="242be-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="242be-103">Získá název sestavení, které tato `ICorDebugAssembly` instance představuje.</span><span class="sxs-lookup"><span data-stu-id="242be-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="242be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="242be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="242be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="242be-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="242be-106">pro Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="242be-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="242be-107">mimo Ukazatel na celé číslo, které určuje skutečnou délku názvu.</span><span class="sxs-lookup"><span data-stu-id="242be-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="242be-108">mimo Pole, které ukládá název.</span><span class="sxs-lookup"><span data-stu-id="242be-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="242be-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="242be-109">Remarks</span></span>  
 <span data-ttu-id="242be-110">`GetName` Metoda vrátí úplnou cestu a název souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="242be-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="242be-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="242be-111">Requirements</span></span>  
 <span data-ttu-id="242be-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="242be-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="242be-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="242be-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="242be-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="242be-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="242be-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="242be-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
