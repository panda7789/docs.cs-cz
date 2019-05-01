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
ms.openlocfilehash: bab625b8415183b9cf90c35cba140c4d28095805
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992443"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="dab2c-102">IMetaDataImport::EnumMethods – metoda</span><span class="sxs-lookup"><span data-stu-id="dab2c-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="dab2c-103">Vytvoří výčet MethodDef tokeny představující metody zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="dab2c-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dab2c-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dab2c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dab2c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="dab2c-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="dab2c-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="dab2c-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="dab2c-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="dab2c-108">[in] Token TypeDef představující typ pomocí metody pro výčet.</span><span class="sxs-lookup"><span data-stu-id="dab2c-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="dab2c-109">[out] Pole pro ukládání tokenů MethodDef.</span><span class="sxs-lookup"><span data-stu-id="dab2c-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="dab2c-110">[in] Maximální velikost MethodDef `rMethods` pole.</span><span class="sxs-lookup"><span data-stu-id="dab2c-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="dab2c-111">[out] Počet tokenů MethodDef vrácené v `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="dab2c-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dab2c-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dab2c-112">Return Value</span></span>  
  
|<span data-ttu-id="dab2c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dab2c-113">HRESULT</span></span>|<span data-ttu-id="dab2c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="dab2c-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="dab2c-115">`EnumMethods` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="dab2c-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="dab2c-116">Neexistují žádné tokeny MethodDef k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="dab2c-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="dab2c-117">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="dab2c-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dab2c-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dab2c-118">Requirements</span></span>  
 <span data-ttu-id="dab2c-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dab2c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dab2c-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dab2c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dab2c-121">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dab2c-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dab2c-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dab2c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab2c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dab2c-123">See also</span></span>

- [<span data-ttu-id="dab2c-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dab2c-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="dab2c-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dab2c-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
