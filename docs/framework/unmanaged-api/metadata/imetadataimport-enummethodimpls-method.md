---
title: "IMetaDataImport::EnumMethodImpls – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2634642c49c9d95765b6a93048a04ce512b28099
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="21b22-102">IMetaDataImport::EnumMethodImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="21b22-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="21b22-103">Vytvoří výčet MethodBody a MethodDeclaration tokenů představující metody zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="21b22-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21b22-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="21b22-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21b22-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="21b22-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="21b22-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="21b22-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="21b22-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="21b22-108">[v] Definice typu pro typ tokenu, jejíž implementace metody pro výčet.</span><span class="sxs-lookup"><span data-stu-id="21b22-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="21b22-109">[out] Pole pro uložení MethodBody tokenů.</span><span class="sxs-lookup"><span data-stu-id="21b22-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="21b22-110">[out] Pole pro uložení MethodDeclaration tokenů.</span><span class="sxs-lookup"><span data-stu-id="21b22-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="21b22-111">[v] Maximální velikost `rMethodBody` a `rMethodDecl` pole.</span><span class="sxs-lookup"><span data-stu-id="21b22-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="21b22-112">[v] Skutečný počet metody, vrátí se v `rMethodBody` a `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="21b22-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21b22-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="21b22-113">Return Value</span></span>  
  
|<span data-ttu-id="21b22-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21b22-114">HRESULT</span></span>|<span data-ttu-id="21b22-115">Popis</span><span class="sxs-lookup"><span data-stu-id="21b22-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="21b22-116">`EnumMethodImpls`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="21b22-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="21b22-117">Neexistují žádné metoda tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="21b22-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="21b22-118">V takovém případě `pcTokens` je nulová.</span><span class="sxs-lookup"><span data-stu-id="21b22-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21b22-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21b22-119">Requirements</span></span>  
 <span data-ttu-id="21b22-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21b22-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b22-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="21b22-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21b22-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21b22-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="21b22-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b22-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b22-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="21b22-124">See Also</span></span>  
 [<span data-ttu-id="21b22-125">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21b22-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="21b22-126">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21b22-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
