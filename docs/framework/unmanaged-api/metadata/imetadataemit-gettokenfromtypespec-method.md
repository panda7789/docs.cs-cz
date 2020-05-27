---
title: IMetaDataEmit::GetTokenFromTypeSpec – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 1cd09fe785bb37c892417ddbf1efaaaa90e121bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009233"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="5ef0e-102">IMetaDataEmit::GetTokenFromTypeSpec – metoda</span><span class="sxs-lookup"><span data-stu-id="5ef0e-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="5ef0e-103">Získá token metadat pro typ se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="5ef0e-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ef0e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ef0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ef0e-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="5ef0e-106">pro Podpis, který je definován.</span><span class="sxs-lookup"><span data-stu-id="5ef0e-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="5ef0e-107">pro Počet bajtů v `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="5ef0e-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="5ef0e-108">mimo `mdTypeSpec`Přiřazený token.</span><span class="sxs-lookup"><span data-stu-id="5ef0e-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ef0e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ef0e-109">Requirements</span></span>  
 <span data-ttu-id="5ef0e-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ef0e-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5ef0e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ef0e-112">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="5ef0e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ef0e-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ef0e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef0e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ef0e-114">See also</span></span>

- [<span data-ttu-id="5ef0e-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5ef0e-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5ef0e-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5ef0e-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
