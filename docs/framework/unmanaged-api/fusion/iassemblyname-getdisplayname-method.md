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
ms.openlocfilehash: 323c883b4010f3ddd4c575e5d5fc40a3419e57c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697404"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="62e77-102">IAssemblyName::GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="62e77-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="62e77-103">Získá popisný název sestavení odkazuje situace [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="62e77-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e77-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62e77-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62e77-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62e77-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="62e77-106">[out] Vyrovnávací paměti řetězce, který obsahuje název odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="62e77-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="62e77-107">[out v] Velikost `szDisplayName` v širokých znaků včetně ukončovacího znaku null znaků.</span><span class="sxs-lookup"><span data-stu-id="62e77-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="62e77-108">[in] Bitová kombinace hodnot [asm_display_flags –](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) hodnoty, které ovlivňují funkce `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="62e77-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62e77-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62e77-109">Requirements</span></span>  
 <span data-ttu-id="62e77-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62e77-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62e77-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="62e77-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="62e77-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62e77-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e77-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62e77-113">See also</span></span>

- [<span data-ttu-id="62e77-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62e77-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="62e77-115">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="62e77-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
