---
title: "ICLRDataTarget::GetMachineType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetMachineType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8cd3a71d150011a1a5b9ad84c4687aac6346eb6f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="e926c-102">ICLRDataTarget::GetMachineType – metoda</span><span class="sxs-lookup"><span data-stu-id="e926c-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="e926c-103">Získá identifikátor pro druh sada instrukcí, která používá tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="e926c-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e926c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e926c-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e926c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e926c-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="e926c-106">[out] Ukazatel na hodnotu, která znamená, že pokyn nastavit tento cílový proces používá.</span><span class="sxs-lookup"><span data-stu-id="e926c-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="e926c-107">Vrácený `machineType` je jedním z IMAGE_FILE_MACHINE konstanty, které jsou definovány v souboru WinNT.h hlavičkový soubor.</span><span class="sxs-lookup"><span data-stu-id="e926c-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e926c-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e926c-108">Requirements</span></span>  
 <span data-ttu-id="e926c-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e926c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e926c-110">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e926c-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e926c-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e926c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e926c-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e926c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e926c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e926c-113">See Also</span></span>  
 [<span data-ttu-id="e926c-114">ICLRDataTarget – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="e926c-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
