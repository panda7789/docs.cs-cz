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
ms.openlocfilehash: b8fabea78f85448e39fc6d31f0a7969458343877
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492003"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="166c8-102">IMetaDataImport::EnumMethodImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="166c8-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="166c8-103">Vytvoří výčet tokenů MethodBody a MethodDeclaration představujících metody zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="166c8-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="166c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="166c8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="166c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="166c8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="166c8-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="166c8-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="166c8-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="166c8-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="166c8-108">pro Token TypeDef pro typ, jehož implementace metody se má vypsat.</span><span class="sxs-lookup"><span data-stu-id="166c8-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="166c8-109">mimo Pole, do kterého se mají ukládat tokeny MethodBody</span><span class="sxs-lookup"><span data-stu-id="166c8-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="166c8-110">mimo Pole, do kterého se mají ukládat tokeny MethodDeclaration</span><span class="sxs-lookup"><span data-stu-id="166c8-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="166c8-111">pro Maximální velikost `rMethodBody` `rMethodDecl` polí a.</span><span class="sxs-lookup"><span data-stu-id="166c8-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="166c8-112">pro Skutečný počet metod vrácených v `rMethodBody` a `rMethodDecl` .</span><span class="sxs-lookup"><span data-stu-id="166c8-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="166c8-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="166c8-113">Return Value</span></span>  
  
|<span data-ttu-id="166c8-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="166c8-114">HRESULT</span></span>|<span data-ttu-id="166c8-115">Description</span><span class="sxs-lookup"><span data-stu-id="166c8-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="166c8-116">`EnumMethodImpls`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="166c8-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="166c8-117">Nejsou k dispozici žádné tokeny metod pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="166c8-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="166c8-118">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="166c8-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="166c8-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="166c8-119">Requirements</span></span>  
 <span data-ttu-id="166c8-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="166c8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="166c8-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="166c8-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="166c8-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="166c8-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="166c8-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="166c8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166c8-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="166c8-124">See also</span></span>

- [<span data-ttu-id="166c8-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="166c8-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="166c8-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="166c8-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
