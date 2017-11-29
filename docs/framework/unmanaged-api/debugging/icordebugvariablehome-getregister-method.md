---
title: "ICorDebugVariableHome::GetRegister – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetRegister
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f16e4bfe4767e1b49d7dacf0481e8911a90e178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="2fe9b-102">ICorDebugVariableHome::GetRegister – metoda</span><span class="sxs-lookup"><span data-stu-id="2fe9b-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="2fe9b-103">Získá registrace, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnné s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="2fe9b-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fe9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fe9b-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fe9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fe9b-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="2fe9b-106">[out] CorDebugRegister – výčet hodnotu, která určuje registrace pro proměnné s typem umístění `VLT_REGISTER`a základní registrace pro proměnné s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="2fe9b-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fe9b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2fe9b-107">Return Value</span></span>  
 <span data-ttu-id="2fe9b-108">Metoda vrátí následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="2fe9b-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="2fe9b-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2fe9b-109">Value</span></span>|<span data-ttu-id="2fe9b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2fe9b-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="2fe9b-111">Proměnná je v seznamu uvedené `pRegister` argument.</span><span class="sxs-lookup"><span data-stu-id="2fe9b-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="2fe9b-112">Proměnná se nenachází v registru nebo register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="2fe9b-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2fe9b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fe9b-113">Requirements</span></span>  
 <span data-ttu-id="2fe9b-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fe9b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fe9b-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fe9b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fe9b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fe9b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fe9b-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fe9b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fe9b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fe9b-118">See Also</span></span>  
 [<span data-ttu-id="2fe9b-119">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="2fe9b-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="2fe9b-120">ICorDebugVariableHome rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fe9b-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
