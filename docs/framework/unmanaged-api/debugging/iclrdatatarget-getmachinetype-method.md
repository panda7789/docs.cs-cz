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
ms.openlocfilehash: 9d86b23b91702929a86334f557a8d647e19861a4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860600"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="2c4da-102">ICLRDataTarget::GetMachineType – metoda</span><span class="sxs-lookup"><span data-stu-id="2c4da-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="2c4da-103">Získá identifikátor pro druh sady instrukcí, který cílový proces používá.</span><span class="sxs-lookup"><span data-stu-id="2c4da-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c4da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c4da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c4da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c4da-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="2c4da-106">mimo Ukazatel na hodnotu, která označuje sadu instrukcí, kterou cílový proces používá.</span><span class="sxs-lookup"><span data-stu-id="2c4da-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="2c4da-107">Vrácená `machineType` je jedna z IMAGE_FILE_MACHINE konstanty, které jsou definovány v souboru hlaviček Winnt. h.</span><span class="sxs-lookup"><span data-stu-id="2c4da-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c4da-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c4da-108">Requirements</span></span>  
 <span data-ttu-id="2c4da-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c4da-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c4da-110">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="2c4da-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2c4da-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2c4da-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c4da-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c4da-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c4da-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c4da-113">See also</span></span>

- [<span data-ttu-id="2c4da-114">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c4da-114">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
