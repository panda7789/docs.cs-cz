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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe587f6356eec861c39c9eb0aa0b6476e0b9a232
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407516"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="d786b-102">ICorDebugAssembly::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="d786b-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="d786b-103">Získá název sestavení, které to `ICorDebugAssembly` instance představuje.</span><span class="sxs-lookup"><span data-stu-id="d786b-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d786b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d786b-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d786b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d786b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d786b-106">[v] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="d786b-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d786b-107">[out] Ukazatel na celé číslo, které určuje skutečné délce název.</span><span class="sxs-lookup"><span data-stu-id="d786b-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="d786b-108">[out] Pole, které ukládá název.</span><span class="sxs-lookup"><span data-stu-id="d786b-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d786b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d786b-109">Remarks</span></span>  
 <span data-ttu-id="d786b-110">`GetName` Metoda vrátí úplný název a cesta k souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="d786b-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d786b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d786b-111">Requirements</span></span>  
 <span data-ttu-id="d786b-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d786b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d786b-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d786b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d786b-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d786b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d786b-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d786b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
