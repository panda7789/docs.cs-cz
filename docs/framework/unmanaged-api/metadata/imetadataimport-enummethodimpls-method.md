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
ms.openlocfilehash: de333ea1ff376918df8069438ce275fde392ae0b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503109"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="d8859-102">IMetaDataImport::EnumMethodImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="d8859-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="d8859-103">Vytvoří výčet MethodBody a MethodDeclaration tokeny představující metody zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="d8859-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8859-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8859-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d8859-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8859-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d8859-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="d8859-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d8859-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="d8859-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="d8859-108">[in] Definice typu pro typ token, jehož implementace metody pro výčet.</span><span class="sxs-lookup"><span data-stu-id="d8859-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="d8859-109">[out] Pole pro ukládání tokenů MethodBody.</span><span class="sxs-lookup"><span data-stu-id="d8859-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="d8859-110">[out] Pole pro ukládání tokenů MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="d8859-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d8859-111">[in] Maximální velikost `rMethodBody` a `rMethodDecl` pole.</span><span class="sxs-lookup"><span data-stu-id="d8859-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d8859-112">[in] Skutečný počet metod vrácené v `rMethodBody` a `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="d8859-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8859-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d8859-113">Return Value</span></span>  
  
|<span data-ttu-id="d8859-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8859-114">HRESULT</span></span>|<span data-ttu-id="d8859-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d8859-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d8859-116">`EnumMethodImpls` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d8859-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d8859-117">Neexistují žádné tokeny metody pro výčet.</span><span class="sxs-lookup"><span data-stu-id="d8859-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="d8859-118">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="d8859-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8859-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8859-119">Requirements</span></span>  
 <span data-ttu-id="d8859-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8859-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8859-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d8859-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8859-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8859-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8859-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8859-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8859-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8859-124">See also</span></span>
- [<span data-ttu-id="d8859-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8859-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d8859-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8859-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
