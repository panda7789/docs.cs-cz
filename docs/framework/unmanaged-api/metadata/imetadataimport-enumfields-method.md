---
title: "IMetaDataImport::EnumFields – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumFields
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 90cfe65779ec71ae483f1119e30bbc4c7e3ec4cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="a60b2-102">IMetaDataImport::EnumFields – metoda</span><span class="sxs-lookup"><span data-stu-id="a60b2-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="a60b2-103">Vytvoří výčet FieldDef tokeny pro typ, který odkazuje zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="a60b2-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a60b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a60b2-104">Syntax</span></span>  
  
```  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a60b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a60b2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a60b2-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="a60b2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="a60b2-107">[v] Token TypeDef třídy, jejichž pole jsou na vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="a60b2-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="a60b2-108">[out] Seznam FieldDef tokeny.</span><span class="sxs-lookup"><span data-stu-id="a60b2-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a60b2-109">[v] Maximální velikost `rFields` pole.</span><span class="sxs-lookup"><span data-stu-id="a60b2-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a60b2-110">[out] Skutečný počet FieldDef tokeny, vrátí se v `rFields`.</span><span class="sxs-lookup"><span data-stu-id="a60b2-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a60b2-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a60b2-111">Return Value</span></span>  
  
|<span data-ttu-id="a60b2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a60b2-112">HRESULT</span></span>|<span data-ttu-id="a60b2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a60b2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a60b2-114">`EnumFields`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a60b2-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a60b2-115">Neexistují žádná pole pro vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="a60b2-115">There are no fields to enumerate.</span></span> <span data-ttu-id="a60b2-116">V takovém případě `pcTokens` je nulová.</span><span class="sxs-lookup"><span data-stu-id="a60b2-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a60b2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a60b2-117">Requirements</span></span>  
 <span data-ttu-id="a60b2-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a60b2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a60b2-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a60b2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a60b2-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a60b2-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a60b2-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a60b2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a60b2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a60b2-122">See Also</span></span>  
 [<span data-ttu-id="a60b2-123">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a60b2-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a60b2-124">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a60b2-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
