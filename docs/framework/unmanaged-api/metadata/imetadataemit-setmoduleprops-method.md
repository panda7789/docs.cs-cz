---
title: IMetaDataEmit::SetModuleProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 2d3c820975488fa722e7af6070611ba7e9686ce8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445441"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="8ef14-102">IMetaDataEmit::SetModuleProps – metoda</span><span class="sxs-lookup"><span data-stu-id="8ef14-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="8ef14-103">Aktualizuje odkazy na modul definovaný předchozím voláním [IMetaDataEmit::D efinemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="8ef14-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ef14-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ef14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ef14-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="8ef14-106">pro Název modulu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="8ef14-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="8ef14-107">Toto je pouze název souboru, nikoli název úplné cesty.</span><span class="sxs-lookup"><span data-stu-id="8ef14-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef14-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ef14-108">Requirements</span></span>  
 <span data-ttu-id="8ef14-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef14-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef14-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8ef14-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ef14-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="8ef14-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ef14-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef14-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef14-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ef14-113">See also</span></span>

- [<span data-ttu-id="8ef14-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ef14-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8ef14-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ef14-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
