---
title: IAssemblyEnum::GetNextAssembly – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57d64096ea693be41359aef63c04674ca77769c6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760973"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="8eb3a-102">IAssemblyEnum::GetNextAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="8eb3a-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="8eb3a-103">Získá ukazatel na další [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obsažené v tomto [iassemblyenum –](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="8eb3a-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8eb3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eb3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8eb3a-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="8eb3a-106">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8eb3a-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="8eb3a-107">`pvReserved` musí být referencí s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="8eb3a-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="8eb3a-108">[out] Vrácený `IAssemblyName` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="8eb3a-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8eb3a-109">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8eb3a-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="8eb3a-110">`dwFlags` musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="8eb3a-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eb3a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8eb3a-111">Requirements</span></span>  
 <span data-ttu-id="8eb3a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eb3a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb3a-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8eb3a-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8eb3a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb3a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb3a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8eb3a-115">See also</span></span>

- [<span data-ttu-id="8eb3a-116">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8eb3a-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="8eb3a-117">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8eb3a-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
