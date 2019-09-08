---
title: IAssemblyName::IsEqual – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 926bdcee3a3c3974c8546f3a6dfe98f0b62c93c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796567"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="bd78b-102">IAssemblyName::IsEqual – metoda</span><span class="sxs-lookup"><span data-stu-id="bd78b-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="bd78b-103">Určuje `IAssemblyName`, zda je zadaný objekt [IAssemblyName](iassemblyname-interface.md) na základě zadaných příznaků porovnávání stejný.</span><span class="sxs-lookup"><span data-stu-id="bd78b-103">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd78b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd78b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd78b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd78b-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="bd78b-106">pro Objekt, na který se má `IAssemblyName`porovnat. `IAssemblyName`</span><span class="sxs-lookup"><span data-stu-id="bd78b-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="bd78b-107">pro Bitová kombinace hodnot [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) , které ovlivňují porovnání.</span><span class="sxs-lookup"><span data-stu-id="bd78b-107">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd78b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd78b-108">Requirements</span></span>  
 <span data-ttu-id="bd78b-109">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd78b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd78b-110">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="bd78b-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bd78b-111">**Verze rozhraní .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd78b-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd78b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd78b-112">See also</span></span>

- [<span data-ttu-id="bd78b-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd78b-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="bd78b-114">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="bd78b-114">Fusion Enumerations</span></span>](fusion-enumerations.md)
