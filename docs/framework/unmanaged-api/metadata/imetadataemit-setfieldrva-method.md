---
title: IMetaDataEmit::SetFieldRVA – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bfc4ac58785b766e74d836fa3cf3b1aca75f01d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521020"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="c0e59-102">IMetaDataEmit::SetFieldRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="c0e59-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="c0e59-103">Nastaví hodnotu globální proměnné pro relativní virtuální adresu pole odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="c0e59-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0e59-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0e59-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0e59-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="c0e59-106">[in] Token pro cílové pole.</span><span class="sxs-lookup"><span data-stu-id="c0e59-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="c0e59-107">[in] Adresa oblasti kódu nebo data.</span><span class="sxs-lookup"><span data-stu-id="c0e59-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0e59-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0e59-108">Requirements</span></span>  
 <span data-ttu-id="c0e59-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0e59-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0e59-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0e59-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0e59-111">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0e59-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0e59-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0e59-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e59-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0e59-113">See also</span></span>
- [<span data-ttu-id="c0e59-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0e59-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c0e59-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0e59-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
