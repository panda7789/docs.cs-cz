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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f48f2d95829d2c8111065e5f4ede4e43a16d63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796663"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="c440c-102">IAssemblyName::GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="c440c-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="c440c-103">Získá název sestavení, na které odkazuje tento objekt [IAssemblyName](iassemblyname-interface.md) , do čitelného lidského.</span><span class="sxs-lookup"><span data-stu-id="c440c-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c440c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c440c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c440c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c440c-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="c440c-106">mimo Vyrovnávací paměť řetězců, která obsahuje název odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="c440c-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="c440c-107">[in, out] Velikost `szDisplayName` v různých znacích včetně ukončovacího znaku null.</span><span class="sxs-lookup"><span data-stu-id="c440c-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="c440c-108">pro Bitová kombinace hodnot [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) , které ovlivňují funkce `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="c440c-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c440c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c440c-109">Requirements</span></span>  
 <span data-ttu-id="c440c-110">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c440c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c440c-111">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c440c-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c440c-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c440c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c440c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c440c-113">See also</span></span>

- [<span data-ttu-id="c440c-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c440c-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="c440c-115">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="c440c-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
