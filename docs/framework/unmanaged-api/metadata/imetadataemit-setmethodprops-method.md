---
title: IMetaDataEmit::SetMethodProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 534afdd5990435c6b4db5ef8ea27a8065b199496
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183596"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="a2c2d-102">IMetaDataEmit::SetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="a2c2d-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="a2c2d-103">Nastaví nebo aktualizuje funkci uložen na zadané relativní virtuální adrese, určené předchozí volání metody [imetadataemit::definemethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="a2c2d-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2c2d-104">Syntax</span></span>  
  
```  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2c2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2c2d-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="a2c2d-106">[in] Token metody změnit.</span><span class="sxs-lookup"><span data-stu-id="a2c2d-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="a2c2d-107">[in] Atributy členu.</span><span class="sxs-lookup"><span data-stu-id="a2c2d-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="a2c2d-108">[in] Adresa kód.</span><span class="sxs-lookup"><span data-stu-id="a2c2d-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="a2c2d-109">[in] Příznaky implementace metody.</span><span class="sxs-lookup"><span data-stu-id="a2c2d-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c2d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2c2d-110">Requirements</span></span>  
 <span data-ttu-id="a2c2d-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2c2d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2c2d-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a2c2d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2c2d-113">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2c2d-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2c2d-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c2d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c2d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2c2d-115">See also</span></span>

- [<span data-ttu-id="a2c2d-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2c2d-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a2c2d-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2c2d-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
