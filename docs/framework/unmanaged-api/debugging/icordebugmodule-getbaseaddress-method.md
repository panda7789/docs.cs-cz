---
title: ICorDebugModule::GetBaseAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11685e8ceba1638ce99a8c4c47b66d0ae2e67714
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476162"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="6edf1-102">ICorDebugModule::GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="6edf1-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="6edf1-103">Získá základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="6edf1-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6edf1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6edf1-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6edf1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6edf1-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="6edf1-106">[out] A `CORDB_ADDRESS` , která určuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="6edf1-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6edf1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6edf1-107">Remarks</span></span>  
 <span data-ttu-id="6edf1-108">Pokud modul je nativní obrázek (tj. Pokud modul se vytvořil parametrem Generátor nativních bitových kopií, NGen.exe), jeho základní adresa bude nula.</span><span class="sxs-lookup"><span data-stu-id="6edf1-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6edf1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6edf1-109">Requirements</span></span>  
 <span data-ttu-id="6edf1-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6edf1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6edf1-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6edf1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6edf1-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6edf1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6edf1-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6edf1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edf1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6edf1-114">See also</span></span>


