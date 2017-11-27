---
title: "IAssemblyName::GetDisplayName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.GetDisplayName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 810192848e15a200a4b2eb33eaf60ddbd7c7c607
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="5a162-102">IAssemblyName::GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="5a162-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="5a162-103">Získá popisný název sestavení odkazuje toto [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="5a162-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a162-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a162-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a162-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a162-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="5a162-106">[out] Vyrovnávací paměť řetězec obsahující název odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="5a162-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="5a162-107">[ve out] Velikost `szDisplayName` v široké znaky, včetně null ukončovací znak.</span><span class="sxs-lookup"><span data-stu-id="5a162-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="5a162-108">[v] Bitovou kombinaci [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) hodnoty, které ovlivňují funkce `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="5a162-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a162-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a162-109">Requirements</span></span>  
 <span data-ttu-id="5a162-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a162-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a162-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5a162-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5a162-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a162-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a162-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a162-113">See Also</span></span>  
 [<span data-ttu-id="5a162-114">Iassemblyname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a162-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="5a162-115">Výčty fúzí</span><span class="sxs-lookup"><span data-stu-id="5a162-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
