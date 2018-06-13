---
title: ICLRDataTarget::GetMachineType – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c515a8184e8c01b0e292057f3f66ffef28f2c5fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402878"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="fdce5-102">ICLRDataTarget::GetMachineType – metoda</span><span class="sxs-lookup"><span data-stu-id="fdce5-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="fdce5-103">Získá identifikátor pro druh sada instrukcí, která používá tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="fdce5-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdce5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdce5-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fdce5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdce5-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="fdce5-106">[out] Ukazatel na hodnotu, která znamená, že pokyn nastavit tento cílový proces používá.</span><span class="sxs-lookup"><span data-stu-id="fdce5-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="fdce5-107">Vrácený `machineType` je jedním z IMAGE_FILE_MACHINE konstanty, které jsou definovány v souboru WinNT.h hlavičkový soubor.</span><span class="sxs-lookup"><span data-stu-id="fdce5-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdce5-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdce5-108">Requirements</span></span>  
 <span data-ttu-id="fdce5-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdce5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdce5-110">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="fdce5-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="fdce5-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdce5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdce5-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdce5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdce5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdce5-113">See Also</span></span>  
 [<span data-ttu-id="fdce5-114">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdce5-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
