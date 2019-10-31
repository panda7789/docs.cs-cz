---
title: IAssemblyName::GetDisplayName – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
ms.openlocfilehash: 5dbb5dc483bc5a08c59606654d55b5a62266e509
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134370"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="e895d-102">IAssemblyName::GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="e895d-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="e895d-103">Získá název sestavení, na které odkazuje tento objekt [IAssemblyName](iassemblyname-interface.md) , do čitelného lidského.</span><span class="sxs-lookup"><span data-stu-id="e895d-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e895d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e895d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e895d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e895d-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="e895d-106">mimo Vyrovnávací paměť řetězců, která obsahuje název odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="e895d-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="e895d-107">[in, out] Velikost `szDisplayName` v různých znacích, včetně ukončovacího znaku null.</span><span class="sxs-lookup"><span data-stu-id="e895d-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="e895d-108">pro Bitová kombinace hodnot [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) , které ovlivňují funkce `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="e895d-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e895d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e895d-109">Requirements</span></span>  
 <span data-ttu-id="e895d-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e895d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e895d-111">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e895d-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e895d-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e895d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e895d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e895d-113">See also</span></span>

- [<span data-ttu-id="e895d-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e895d-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="e895d-115">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="e895d-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
