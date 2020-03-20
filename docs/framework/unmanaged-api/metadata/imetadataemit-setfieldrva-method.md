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
ms.openlocfilehash: 7648a1b3d219ee5d2b1ddc6b26f7b65c9ac85105
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175639"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="22d6e-102">IMetaDataEmit::SetFieldRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="22d6e-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="22d6e-103">Nastaví hodnotu globální proměnné pro relativní virtuální adresu pole, na které odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="22d6e-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22d6e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22d6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22d6e-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="22d6e-106">[v] Token pro cílové pole.</span><span class="sxs-lookup"><span data-stu-id="22d6e-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="22d6e-107">[v] Adresa kódu nebo datové oblasti.</span><span class="sxs-lookup"><span data-stu-id="22d6e-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22d6e-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22d6e-108">Requirements</span></span>  
 <span data-ttu-id="22d6e-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22d6e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22d6e-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="22d6e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22d6e-111">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22d6e-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22d6e-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22d6e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d6e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="22d6e-113">See also</span></span>

- [<span data-ttu-id="22d6e-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22d6e-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="22d6e-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22d6e-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
