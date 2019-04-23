---
title: ICorDebugModule::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b39467c067e50f2d553b35a41b0f783e0fc82156
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176641"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="d7fcf-102">ICorDebugModule::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="d7fcf-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="d7fcf-103">Získá název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="d7fcf-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7fcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7fcf-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7fcf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7fcf-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="d7fcf-106">[in] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="d7fcf-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d7fcf-107">[in] Ukazatel na vrácený název.</span><span class="sxs-lookup"><span data-stu-id="d7fcf-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="d7fcf-108">[out] Pole, která ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="d7fcf-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7fcf-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7fcf-109">Remarks</span></span>  
 <span data-ttu-id="d7fcf-110">`GetName` Metoda vrátí hodnotu S_OK HRESULT, pokud název souboru modulu odpovídá názvu na disku.</span><span class="sxs-lookup"><span data-stu-id="d7fcf-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="d7fcf-111">`GetName` Vrátí S_FALSE HRESULT, pokud je název kovodělných, například pro modul dynamické nebo v paměti.</span><span class="sxs-lookup"><span data-stu-id="d7fcf-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7fcf-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7fcf-112">Requirements</span></span>  
 <span data-ttu-id="d7fcf-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7fcf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7fcf-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7fcf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7fcf-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7fcf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7fcf-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7fcf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7fcf-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7fcf-117">See also</span></span>
