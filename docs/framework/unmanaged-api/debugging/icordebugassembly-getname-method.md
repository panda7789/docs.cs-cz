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
ms.openlocfilehash: 5e3619d12b9377a8482254703d3d97d0348a013b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127173"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="afc5e-102">ICorDebugAssembly::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="afc5e-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="afc5e-103">Získá název sestavení, které představuje tato `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="afc5e-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afc5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afc5e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afc5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afc5e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="afc5e-106">pro Velikost pole `szName`.</span><span class="sxs-lookup"><span data-stu-id="afc5e-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="afc5e-107">mimo Ukazatel na celé číslo, které určuje skutečnou délku názvu.</span><span class="sxs-lookup"><span data-stu-id="afc5e-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="afc5e-108">mimo Pole, které ukládá název.</span><span class="sxs-lookup"><span data-stu-id="afc5e-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afc5e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="afc5e-109">Remarks</span></span>  
 <span data-ttu-id="afc5e-110">Metoda `GetName` vrátí úplnou cestu a název souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="afc5e-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afc5e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="afc5e-111">Requirements</span></span>  
 <span data-ttu-id="afc5e-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afc5e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afc5e-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="afc5e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afc5e-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="afc5e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afc5e-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afc5e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
