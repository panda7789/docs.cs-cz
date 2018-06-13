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
ms.openlocfilehash: 4503c3c745fde148c77ff30c9ece008dd9d54829
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445793"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="b50aa-102">IMetaDataEmit::DefineModuleRef – metoda</span><span class="sxs-lookup"><span data-stu-id="b50aa-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="b50aa-103">Vytvoří metadata podpis pro modul se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="b50aa-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b50aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b50aa-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b50aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b50aa-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="b50aa-106">[v] Název souboru další metadata, obvykle knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="b50aa-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="b50aa-107">Toto je pouze název souboru.</span><span class="sxs-lookup"><span data-stu-id="b50aa-107">This is the file name only.</span></span> <span data-ttu-id="b50aa-108">Nepoužívejte úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="b50aa-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="b50aa-109">[out] Přiřazená `mdModuleRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="b50aa-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b50aa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b50aa-110">Requirements</span></span>  
 <span data-ttu-id="b50aa-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b50aa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b50aa-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b50aa-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b50aa-113">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b50aa-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b50aa-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b50aa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b50aa-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b50aa-115">See Also</span></span>  
 [<span data-ttu-id="b50aa-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b50aa-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b50aa-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b50aa-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
