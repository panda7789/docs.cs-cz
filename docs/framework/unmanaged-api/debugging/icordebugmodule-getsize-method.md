---
title: ICorDebugModule::GetSize – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46ee21a9fd7b9267672a14107c1706af5d5cdcc5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763571"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="398ce-102">ICorDebugModule::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="398ce-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="398ce-103">Získá velikost v bajtech, modulu.</span><span class="sxs-lookup"><span data-stu-id="398ce-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="398ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="398ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="398ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="398ce-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="398ce-106">[out] Velikost modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="398ce-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="398ce-107">Pokud modul byl vytvořen z native image generator (NGen.exe), bude velikost modulu nula.</span><span class="sxs-lookup"><span data-stu-id="398ce-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="398ce-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="398ce-108">Requirements</span></span>  
 <span data-ttu-id="398ce-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="398ce-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="398ce-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="398ce-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="398ce-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="398ce-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="398ce-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="398ce-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
