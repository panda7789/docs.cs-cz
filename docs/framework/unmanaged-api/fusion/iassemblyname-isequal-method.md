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
ms.openlocfilehash: 23bc251053dd27a7c5accb48ab4759ecdb79fe09
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134309"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="716e4-102">IAssemblyName::IsEqual – metoda</span><span class="sxs-lookup"><span data-stu-id="716e4-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="716e4-103">Určuje, zda je zadaný objekt [IAssemblyName](iassemblyname-interface.md) roven tomuto `IAssemblyName`na základě zadaných příznaků porovnávání.</span><span class="sxs-lookup"><span data-stu-id="716e4-103">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="716e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="716e4-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="716e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="716e4-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="716e4-106">pro Objekt `IAssemblyName`, pro který chcete porovnat tento `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="716e4-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="716e4-107">pro Bitová kombinace hodnot [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) , které ovlivňují porovnání.</span><span class="sxs-lookup"><span data-stu-id="716e4-107">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="716e4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="716e4-108">Requirements</span></span>  
 <span data-ttu-id="716e4-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="716e4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="716e4-110">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="716e4-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="716e4-111">**Verze rozhraní .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="716e4-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716e4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="716e4-112">See also</span></span>

- [<span data-ttu-id="716e4-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="716e4-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="716e4-114">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="716e4-114">Fusion Enumerations</span></span>](fusion-enumerations.md)
