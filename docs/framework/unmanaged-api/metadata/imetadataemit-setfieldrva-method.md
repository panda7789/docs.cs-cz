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
ms.openlocfilehash: 0447a44c555e141c96d6a52ba330e181151a7bc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445887"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="2ae71-102">IMetaDataEmit::SetFieldRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="2ae71-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="2ae71-103">Nastaví hodnotu globální proměnné pro relativní virtuální adresu pole odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="2ae71-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ae71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ae71-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ae71-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ae71-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="2ae71-106">[v] Token pro cílové pole.</span><span class="sxs-lookup"><span data-stu-id="2ae71-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="2ae71-107">[v] Adresa kód nebo datové oblasti.</span><span class="sxs-lookup"><span data-stu-id="2ae71-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ae71-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ae71-108">Requirements</span></span>  
 <span data-ttu-id="2ae71-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ae71-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ae71-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2ae71-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ae71-111">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ae71-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ae71-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ae71-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae71-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ae71-113">See Also</span></span>  
 [<span data-ttu-id="2ae71-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ae71-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="2ae71-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ae71-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
