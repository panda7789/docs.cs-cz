---
title: IMetaDataEmit::GetTokenFromSig – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
ms.openlocfilehash: 740dad54bc3a79ff546176abdc35487d89ed8f44
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009246"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="65627-102">IMetaDataEmit::GetTokenFromSig – metoda</span><span class="sxs-lookup"><span data-stu-id="65627-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="65627-103">Získá token pro zadaný podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="65627-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65627-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65627-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65627-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65627-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="65627-106">pro Signatura, která se má zachovat a uložit.</span><span class="sxs-lookup"><span data-stu-id="65627-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="65627-107">pro Počet bajtů v `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="65627-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="65627-108">mimo `mdSignature`Přiřazený token.</span><span class="sxs-lookup"><span data-stu-id="65627-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65627-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65627-109">Requirements</span></span>  
 <span data-ttu-id="65627-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65627-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65627-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="65627-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65627-112">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="65627-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65627-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65627-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65627-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="65627-114">See also</span></span>

- [<span data-ttu-id="65627-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65627-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="65627-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65627-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
