---
title: IMetaDataEmit::DefineModuleRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f52f102102cb654035d49eea0f4b0a9061475a3a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128814"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="639d6-102">IMetaDataEmit::DefineModuleRef – metoda</span><span class="sxs-lookup"><span data-stu-id="639d6-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="639d6-103">Vytvoří podpis metadat pro modul se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="639d6-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="639d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="639d6-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="639d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="639d6-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="639d6-106">[in] Název další metadata souboru obvykle knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="639d6-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="639d6-107">Toto je pouze název souboru.</span><span class="sxs-lookup"><span data-stu-id="639d6-107">This is the file name only.</span></span> <span data-ttu-id="639d6-108">Nepoužívejte úplné cesty.</span><span class="sxs-lookup"><span data-stu-id="639d6-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="639d6-109">[out] Přiřazená `mdModuleRef` token.</span><span class="sxs-lookup"><span data-stu-id="639d6-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="639d6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="639d6-110">Requirements</span></span>  
 <span data-ttu-id="639d6-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="639d6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="639d6-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="639d6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="639d6-113">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="639d6-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="639d6-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="639d6-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="639d6-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="639d6-115">See also</span></span>

- [<span data-ttu-id="639d6-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="639d6-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="639d6-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="639d6-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
