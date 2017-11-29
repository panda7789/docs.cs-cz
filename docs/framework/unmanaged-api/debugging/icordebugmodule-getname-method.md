---
title: "ICorDebugModule::GetName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b10e0eed3c2df8781aa7085cc43157894cc6e2c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="30656-102">ICorDebugModule::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="30656-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="30656-103">Získá název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="30656-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30656-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30656-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30656-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30656-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="30656-106">[v] Velikost `szName` pole.</span><span class="sxs-lookup"><span data-stu-id="30656-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="30656-107">[v] Ukazatel na délku vrácený název.</span><span class="sxs-lookup"><span data-stu-id="30656-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="30656-108">[out] Pole, které ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="30656-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30656-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30656-109">Remarks</span></span>  
 <span data-ttu-id="30656-110">`GetName` Metoda vrátí S_OK HRESULT, pokud název souboru modulu odpovídá názvu na disku.</span><span class="sxs-lookup"><span data-stu-id="30656-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="30656-111">`GetName`Vrátí S_FALSE HRESULT, pokud je název kovodělných, například pro modul dynamické nebo v paměti.</span><span class="sxs-lookup"><span data-stu-id="30656-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30656-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30656-112">Requirements</span></span>  
 <span data-ttu-id="30656-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30656-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30656-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30656-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30656-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30656-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30656-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30656-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30656-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="30656-117">See Also</span></span>  
    
 
