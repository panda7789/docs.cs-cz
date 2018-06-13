---
title: IMetaDataImport::EnumMethods – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 933694a6a033dbfe817e3848b9008f05b86f51f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449009"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="769bb-102">IMetaDataImport::EnumMethods – metoda</span><span class="sxs-lookup"><span data-stu-id="769bb-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="769bb-103">Vytvoří výčet MethodDef tokeny představující metody zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="769bb-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="769bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="769bb-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="769bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="769bb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="769bb-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="769bb-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="769bb-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="769bb-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="769bb-108">[v] TypeDef token představující typ pomocí metody k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="769bb-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="769bb-109">[out] Pole pro uložení MethodDef tokenů.</span><span class="sxs-lookup"><span data-stu-id="769bb-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="769bb-110">[v] Maximální velikost MethodDef `rMethods` pole.</span><span class="sxs-lookup"><span data-stu-id="769bb-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="769bb-111">[out] Počet MethodDef tokeny, vrátí se v `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="769bb-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="769bb-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="769bb-112">Return Value</span></span>  
  
|<span data-ttu-id="769bb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="769bb-113">HRESULT</span></span>|<span data-ttu-id="769bb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="769bb-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="769bb-115">`EnumMethods` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="769bb-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="769bb-116">Neexistují žádné MethodDef tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="769bb-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="769bb-117">V takovém případě `pcTokens` je nulová.</span><span class="sxs-lookup"><span data-stu-id="769bb-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="769bb-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="769bb-118">Requirements</span></span>  
 <span data-ttu-id="769bb-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="769bb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="769bb-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="769bb-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="769bb-121">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="769bb-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="769bb-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="769bb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769bb-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="769bb-123">See Also</span></span>  
 [<span data-ttu-id="769bb-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="769bb-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="769bb-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="769bb-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
