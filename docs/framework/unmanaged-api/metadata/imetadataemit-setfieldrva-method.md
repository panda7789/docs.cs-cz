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
ms.openlocfilehash: d429995e41006798aee5f796150bedbd6ae87f6f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003864"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="5e98e-102">IMetaDataEmit::SetFieldRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="5e98e-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="5e98e-103">Nastaví hodnotu globální proměnné pro relativní virtuální adresu pole, na které odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="5e98e-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e98e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e98e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e98e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e98e-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="5e98e-106">pro Token pro cílové pole</span><span class="sxs-lookup"><span data-stu-id="5e98e-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="5e98e-107">pro Adresa kódu nebo oblasti dat.</span><span class="sxs-lookup"><span data-stu-id="5e98e-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e98e-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e98e-108">Requirements</span></span>  
 <span data-ttu-id="5e98e-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e98e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e98e-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5e98e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e98e-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="5e98e-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e98e-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e98e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e98e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e98e-113">See also</span></span>

- [<span data-ttu-id="5e98e-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e98e-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5e98e-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e98e-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
