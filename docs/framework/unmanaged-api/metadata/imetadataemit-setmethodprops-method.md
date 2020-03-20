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
ms.openlocfilehash: 9662a14b4ea97aed16968083489324d46c38dda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177514"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="a9b81-102">IMetaDataEmit::SetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="a9b81-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="a9b81-103">Nastaví nebo aktualizuje funkci metody definované předchozím voláním [Metody IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="a9b81-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9b81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9b81-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9b81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9b81-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="a9b81-106">[v] Token pro metodu, která má být změněna.</span><span class="sxs-lookup"><span data-stu-id="a9b81-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="a9b81-107">[v] Atributy člena.</span><span class="sxs-lookup"><span data-stu-id="a9b81-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="a9b81-108">[v] Adresa kódu.</span><span class="sxs-lookup"><span data-stu-id="a9b81-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="a9b81-109">[v] Příznaky implementace pro metodu.</span><span class="sxs-lookup"><span data-stu-id="a9b81-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9b81-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9b81-110">Requirements</span></span>  
 <span data-ttu-id="a9b81-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9b81-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9b81-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="a9b81-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9b81-113">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9b81-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9b81-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9b81-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b81-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9b81-115">See also</span></span>

- [<span data-ttu-id="a9b81-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9b81-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a9b81-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9b81-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
