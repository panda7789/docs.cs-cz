---
title: IMetaDataImport::EnumMethodImpls – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
ms.openlocfilehash: e766cec8fd84713e12c43cd1095650ed5b757bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175470"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="3b1f0-102">IMetaDataImport::EnumMethodImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="3b1f0-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="3b1f0-103">Výčet MethodBody a MethodDeclaration tokeny představující metody zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b1f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b1f0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdToken     rMethodBody[],
   [out]     mdToken     rMethodDecl[],
   [in]      ULONG       cMax,
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b1f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b1f0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3b1f0-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3b1f0-107">To musí být NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="3b1f0-108">[v] A TypeDef token pro typ, jehož implementace metody k výčtu.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="3b1f0-109">[out] Pole pro uložení tokenů MethodBody.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="3b1f0-110">[out] Pole pro uložení tokenů MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3b1f0-111">[v] Maximální velikost `rMethodBody` a `rMethodDecl` pole.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3b1f0-112">[v] Skutečný počet vrácených `rMethodBody` metod `rMethodDecl`a .</span><span class="sxs-lookup"><span data-stu-id="3b1f0-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b1f0-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3b1f0-113">Return Value</span></span>  
  
|<span data-ttu-id="3b1f0-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b1f0-114">HRESULT</span></span>|<span data-ttu-id="3b1f0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="3b1f0-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3b1f0-116">`EnumMethodImpls`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3b1f0-117">Neexistují žádné tokeny metody pro výčet.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="3b1f0-118">V tom `pcTokens` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b1f0-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b1f0-119">Requirements</span></span>  
 <span data-ttu-id="3b1f0-120">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b1f0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b1f0-121">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="3b1f0-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b1f0-122">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b1f0-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b1f0-123">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b1f0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1f0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b1f0-124">See also</span></span>

- [<span data-ttu-id="3b1f0-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b1f0-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3b1f0-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b1f0-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
