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
ms.openlocfilehash: aff8fb0a2316817e413f10e82215556f1f54fbc4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109629"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="94bee-102">ICorDebugModule::GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="94bee-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="94bee-103">Získá základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="94bee-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94bee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94bee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94bee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94bee-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="94bee-106">mimo `CORDB_ADDRESS`, která určuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="94bee-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94bee-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94bee-107">Remarks</span></span>  
 <span data-ttu-id="94bee-108">Pokud je modul nativní Image (to znamená, že pokud modul vytvořil generátor nativních bitových kopií, NGen. exe), jeho základní adresa bude nulová.</span><span class="sxs-lookup"><span data-stu-id="94bee-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94bee-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94bee-109">Requirements</span></span>  
 <span data-ttu-id="94bee-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94bee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94bee-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="94bee-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94bee-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="94bee-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94bee-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94bee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94bee-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94bee-114">See also</span></span>
