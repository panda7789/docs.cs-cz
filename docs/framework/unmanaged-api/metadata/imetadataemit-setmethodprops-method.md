---
title: "IMetaDataEmit::SetMethodProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetMethodProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d03423aa20ed9582f0e2cb38b24169a25d47e352
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="9f1c9-102">IMetaDataEmit::SetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="9f1c9-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="9f1c9-103">Nastaví nebo aktualizuje funkce, které jsou uložené na zadaný relativní virtuální na adrese definované předchozí volání metody [imetadataemit::definemethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="9f1c9-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f1c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f1c9-104">Syntax</span></span>  
  
```  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f1c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f1c9-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="9f1c9-106">[v] Token pro metodu změnit.</span><span class="sxs-lookup"><span data-stu-id="9f1c9-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="9f1c9-107">[v] Atributy členu.</span><span class="sxs-lookup"><span data-stu-id="9f1c9-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="9f1c9-108">[v] Adresa kód.</span><span class="sxs-lookup"><span data-stu-id="9f1c9-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="9f1c9-109">[v] Pro metodu příznaky implementace.</span><span class="sxs-lookup"><span data-stu-id="9f1c9-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f1c9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f1c9-110">Requirements</span></span>  
 <span data-ttu-id="9f1c9-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f1c9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f1c9-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9f1c9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f1c9-113">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9f1c9-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f1c9-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f1c9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f1c9-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f1c9-115">See Also</span></span>  
 [<span data-ttu-id="9f1c9-116">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f1c9-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9f1c9-117">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f1c9-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
