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
ms.openlocfilehash: 75d1ce526d4cba025ea6e9db8281023969e7cb0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448508"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="36648-102">IMetaDataImport::EnumMethodImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="36648-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="36648-103">Vytvoří výčet MethodBody a MethodDeclaration tokenů představující metody zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="36648-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36648-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36648-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="36648-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36648-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="36648-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="36648-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="36648-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="36648-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="36648-108">[v] Definice typu pro typ tokenu, jejíž implementace metody pro výčet.</span><span class="sxs-lookup"><span data-stu-id="36648-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="36648-109">[out] Pole pro uložení MethodBody tokenů.</span><span class="sxs-lookup"><span data-stu-id="36648-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="36648-110">[out] Pole pro uložení MethodDeclaration tokenů.</span><span class="sxs-lookup"><span data-stu-id="36648-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="36648-111">[v] Maximální velikost `rMethodBody` a `rMethodDecl` pole.</span><span class="sxs-lookup"><span data-stu-id="36648-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="36648-112">[v] Skutečný počet metody, vrátí se v `rMethodBody` a `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="36648-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36648-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="36648-113">Return Value</span></span>  
  
|<span data-ttu-id="36648-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36648-114">HRESULT</span></span>|<span data-ttu-id="36648-115">Popis</span><span class="sxs-lookup"><span data-stu-id="36648-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="36648-116">`EnumMethodImpls` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="36648-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="36648-117">Neexistují žádné metoda tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="36648-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="36648-118">V takovém případě `pcTokens` je nulová.</span><span class="sxs-lookup"><span data-stu-id="36648-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36648-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36648-119">Requirements</span></span>  
 <span data-ttu-id="36648-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36648-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36648-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="36648-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36648-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36648-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36648-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36648-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36648-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="36648-124">See Also</span></span>  
 [<span data-ttu-id="36648-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36648-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="36648-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36648-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
