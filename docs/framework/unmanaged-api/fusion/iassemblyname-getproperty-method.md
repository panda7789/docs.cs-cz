---
title: IAssemblyName::GetProperty – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
ms.openlocfilehash: b86828e01fb00b12feff2ed451793c240e16e240
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134382"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="2d03e-102">IAssemblyName::GetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="2d03e-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="2d03e-103">Získá ukazatel na vlastnost, na kterou odkazuje zadaný identifikátor vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2d03e-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d03e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d03e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d03e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d03e-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="2d03e-106">pro Jedinečný identifikátor pro požadovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2d03e-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="2d03e-107">mimo Vrácená data vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2d03e-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="2d03e-108">[in, out] Velikost `pvProperty`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="2d03e-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d03e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d03e-109">Requirements</span></span>  
 <span data-ttu-id="2d03e-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d03e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d03e-111">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="2d03e-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2d03e-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d03e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d03e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d03e-113">See also</span></span>

- [<span data-ttu-id="2d03e-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d03e-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
