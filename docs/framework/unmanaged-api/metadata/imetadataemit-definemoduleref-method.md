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
ms.openlocfilehash: efff491d92ac7910f43f76965ef98d1d0e4ba0aa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004423"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="7dc7a-102">IMetaDataEmit::DefineModuleRef – metoda</span><span class="sxs-lookup"><span data-stu-id="7dc7a-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="7dc7a-103">Vytvoří podpis metadat pro modul se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="7dc7a-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dc7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7dc7a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dc7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7dc7a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="7dc7a-106">pro Název dalšího souboru metadat, obvykle knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="7dc7a-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="7dc7a-107">Toto je pouze název souboru.</span><span class="sxs-lookup"><span data-stu-id="7dc7a-107">This is the file name only.</span></span> <span data-ttu-id="7dc7a-108">Nepoužívejte úplný název cesty.</span><span class="sxs-lookup"><span data-stu-id="7dc7a-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="7dc7a-109">mimo Přiřazený `mdModuleRef` token</span><span class="sxs-lookup"><span data-stu-id="7dc7a-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dc7a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7dc7a-110">Requirements</span></span>  
 <span data-ttu-id="7dc7a-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dc7a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dc7a-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7dc7a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7dc7a-113">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="7dc7a-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7dc7a-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dc7a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dc7a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7dc7a-115">See also</span></span>

- [<span data-ttu-id="7dc7a-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7dc7a-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7dc7a-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7dc7a-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
