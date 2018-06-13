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
ms.openlocfilehash: 10e7da7711cd63579589fda416d0d3a4f777eefe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412537"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="7b62d-102">ICorDebugModule::GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="7b62d-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="7b62d-103">Získá základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="7b62d-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b62d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b62d-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b62d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b62d-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="7b62d-106">[out] A `CORDB_ADDRESS` určující základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="7b62d-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b62d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b62d-107">Remarks</span></span>  
 <span data-ttu-id="7b62d-108">Pokud modul je nativní bitové kopie (to znamená, pokud modul bylo vytvořeno pomocí Generátor nativních bitových kopií, NGen.exe), jeho základní adresa bude nula.</span><span class="sxs-lookup"><span data-stu-id="7b62d-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b62d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b62d-109">Requirements</span></span>  
 <span data-ttu-id="7b62d-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b62d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b62d-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b62d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b62d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b62d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b62d-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b62d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b62d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b62d-114">See Also</span></span>  
    
 
