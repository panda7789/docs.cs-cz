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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09bd9f4029f5e4609ab1ef6f49a4364e83f1edfb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184563"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="16349-102">IMetaDataImport::EnumMethodImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="16349-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="16349-103">Vytvoří výčet MethodBody a MethodDeclaration tokeny představující metody zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="16349-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16349-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16349-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16349-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16349-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="16349-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="16349-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="16349-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="16349-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="16349-108">[in] Definice typu pro typ token, jehož implementace metody pro výčet.</span><span class="sxs-lookup"><span data-stu-id="16349-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="16349-109">[out] Pole pro ukládání tokenů MethodBody.</span><span class="sxs-lookup"><span data-stu-id="16349-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="16349-110">[out] Pole pro ukládání tokenů MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="16349-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="16349-111">[in] Maximální velikost `rMethodBody` a `rMethodDecl` pole.</span><span class="sxs-lookup"><span data-stu-id="16349-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="16349-112">[in] Skutečný počet metod vrácené v `rMethodBody` a `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="16349-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16349-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="16349-113">Return Value</span></span>  
  
|<span data-ttu-id="16349-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16349-114">HRESULT</span></span>|<span data-ttu-id="16349-115">Popis</span><span class="sxs-lookup"><span data-stu-id="16349-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="16349-116">`EnumMethodImpls` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="16349-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="16349-117">Neexistují žádné tokeny metody pro výčet.</span><span class="sxs-lookup"><span data-stu-id="16349-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="16349-118">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="16349-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16349-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16349-119">Requirements</span></span>  
 <span data-ttu-id="16349-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16349-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16349-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="16349-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16349-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16349-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16349-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16349-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16349-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16349-124">See also</span></span>

- [<span data-ttu-id="16349-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16349-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="16349-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16349-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
