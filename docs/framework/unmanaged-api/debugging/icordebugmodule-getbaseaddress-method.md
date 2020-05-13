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
ms.openlocfilehash: 9270afa1d8c8ddd74cfe6dd05e39c1480f5767e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206938"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="3dc64-102">ICorDebugModule::GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="3dc64-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="3dc64-103">Získá základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="3dc64-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dc64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dc64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dc64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dc64-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="3dc64-106">mimo A `CORDB_ADDRESS` Určuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="3dc64-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dc64-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3dc64-107">Remarks</span></span>  
 <span data-ttu-id="3dc64-108">Pokud je modul nativní Image (to znamená, že pokud modul vytvořil generátor nativních bitových kopií, NGen. exe), jeho základní adresa bude nulová.</span><span class="sxs-lookup"><span data-stu-id="3dc64-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dc64-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3dc64-109">Requirements</span></span>  
 <span data-ttu-id="3dc64-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dc64-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dc64-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3dc64-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dc64-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3dc64-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dc64-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dc64-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc64-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dc64-114">See also</span></span>
