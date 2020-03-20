---
title: IMetaDataEmit::Save – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: 76f18336808e6832b2ded94349efd7948f23a1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175691"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="f8294-102">IMetaDataEmit::Save – metoda</span><span class="sxs-lookup"><span data-stu-id="f8294-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="f8294-103">Uloží všechna metadata v aktuálním oboru do souboru na zadanou adresu.</span><span class="sxs-lookup"><span data-stu-id="f8294-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8294-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8294-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8294-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8294-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="f8294-106">[v] Název souboru, do který chcete uložit.</span><span class="sxs-lookup"><span data-stu-id="f8294-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="f8294-107">Pokud je tato hodnota null, bude kopie v paměti uložena do posledního umístění, které bylo použito.</span><span class="sxs-lookup"><span data-stu-id="f8294-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="f8294-108">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="f8294-108">[in] Reserved.</span></span> <span data-ttu-id="f8294-109">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="f8294-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8294-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8294-110">Requirements</span></span>  
 <span data-ttu-id="f8294-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8294-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8294-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="f8294-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8294-113">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8294-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8294-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8294-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8294-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8294-115">See also</span></span>

- [<span data-ttu-id="f8294-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8294-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f8294-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8294-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
