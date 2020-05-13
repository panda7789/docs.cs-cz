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
ms.openlocfilehash: 4f9818137016dc3e0522ed516c52df2550ffdfca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212513"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="00767-102">ICorDebugModule::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="00767-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="00767-103">Získá velikost modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="00767-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00767-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00767-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00767-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00767-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="00767-106">mimo Velikost modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="00767-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="00767-107">Pokud byl modul vytvořen z nativního generátoru bitových kopií (NGen. exe), bude mít velikost modulu hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="00767-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00767-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00767-108">Requirements</span></span>  
 <span data-ttu-id="00767-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00767-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00767-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="00767-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00767-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="00767-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00767-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00767-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
