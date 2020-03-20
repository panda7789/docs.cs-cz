---
title: IMetaDataEmit::SetRVA – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
ms.openlocfilehash: fe0b4b7fef0d05c4acc06dad5bc8a4eaf0722c9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175574"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="b2fb0-102">IMetaDataEmit::SetRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="b2fb0-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="b2fb0-103">Nastaví relativní virtuální adresu zadané metody.</span><span class="sxs-lookup"><span data-stu-id="b2fb0-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2fb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2fb0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2fb0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2fb0-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="b2fb0-106">[v] Token pro cílovou metodu nebo implementaci metody.</span><span class="sxs-lookup"><span data-stu-id="b2fb0-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="b2fb0-107">[v] Adresa kódu nebo datové oblasti.</span><span class="sxs-lookup"><span data-stu-id="b2fb0-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2fb0-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2fb0-108">Requirements</span></span>  
 <span data-ttu-id="b2fb0-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2fb0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2fb0-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="b2fb0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2fb0-111">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2fb0-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2fb0-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2fb0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2fb0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2fb0-113">See also</span></span>

- [<span data-ttu-id="b2fb0-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2fb0-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b2fb0-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2fb0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
