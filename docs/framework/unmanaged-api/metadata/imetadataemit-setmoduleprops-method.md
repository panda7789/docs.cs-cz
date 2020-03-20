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
ms.openlocfilehash: 69c3ee366dbb8505e0df744037c480da996bb836
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175613"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="e12e8-102">IMetaDataEmit::SetModuleProps – metoda</span><span class="sxs-lookup"><span data-stu-id="e12e8-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="e12e8-103">Aktualizuje odkazy na modul definovaný předchozím voláním [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="e12e8-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e12e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e12e8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e12e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e12e8-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e12e8-106">[v] Název modulu v unicode.</span><span class="sxs-lookup"><span data-stu-id="e12e8-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="e12e8-107">Toto je pouze název souboru a nikoli úplný název cesty.</span><span class="sxs-lookup"><span data-stu-id="e12e8-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e12e8-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e12e8-108">Requirements</span></span>  
 <span data-ttu-id="e12e8-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e12e8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e12e8-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="e12e8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e12e8-111">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e12e8-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e12e8-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e12e8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e12e8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e12e8-113">See also</span></span>

- [<span data-ttu-id="e12e8-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e12e8-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e12e8-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e12e8-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
