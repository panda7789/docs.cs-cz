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
ms.openlocfilehash: 3059d30f3969b4e19cee5a8d7a34c606f3849c05
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008739"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="cc887-102">IMetaDataEmit::SetRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="cc887-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="cc887-103">Nastaví relativní virtuální adresu zadané metody.</span><span class="sxs-lookup"><span data-stu-id="cc887-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc887-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc887-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc887-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc887-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="cc887-106">pro Token pro implementaci cílové metody nebo metody.</span><span class="sxs-lookup"><span data-stu-id="cc887-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="cc887-107">pro Adresa kódu nebo oblasti dat.</span><span class="sxs-lookup"><span data-stu-id="cc887-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc887-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc887-108">Requirements</span></span>  
 <span data-ttu-id="cc887-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc887-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc887-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cc887-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc887-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="cc887-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc887-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc887-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc887-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc887-113">See also</span></span>

- [<span data-ttu-id="cc887-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc887-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="cc887-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc887-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
