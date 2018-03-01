---
title: "ICLRDataTarget::GetMachineType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 56fabfd2bb929e40c60903ad7b5e86e2b18d7d93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="8a73f-102">ICLRDataTarget::GetMachineType – metoda</span><span class="sxs-lookup"><span data-stu-id="8a73f-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="8a73f-103">Získá identifikátor pro druh sada instrukcí, která používá tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="8a73f-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a73f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a73f-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a73f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a73f-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="8a73f-106">[out] Ukazatel na hodnotu, která znamená, že pokyn nastavit tento cílový proces používá.</span><span class="sxs-lookup"><span data-stu-id="8a73f-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="8a73f-107">Vrácený `machineType` je jedním z IMAGE_FILE_MACHINE konstanty, které jsou definovány v souboru WinNT.h hlavičkový soubor.</span><span class="sxs-lookup"><span data-stu-id="8a73f-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a73f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a73f-108">Requirements</span></span>  
 <span data-ttu-id="8a73f-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a73f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a73f-110">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="8a73f-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8a73f-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a73f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a73f-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a73f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a73f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a73f-113">See Also</span></span>  
 [<span data-ttu-id="8a73f-114">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8a73f-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
