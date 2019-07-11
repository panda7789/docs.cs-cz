---
title: IMetaDataImport::EnumMethodsWithName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5de55d74741e9deb33be2f9adf15a970561664b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779737"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="85ce5-102">IMetaDataImport::EnumMethodsWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="85ce5-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="85ce5-103">Podává výčet metod, které mají se zadaným názvem a typem odkazuje zadaný token TypeDef, která jsou definována.</span><span class="sxs-lookup"><span data-stu-id="85ce5-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85ce5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85ce5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85ce5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85ce5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="85ce5-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="85ce5-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="85ce5-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="85ce5-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="85ce5-108">[in] Token TypeDef představující typ, jehož metody pro výčet.</span><span class="sxs-lookup"><span data-stu-id="85ce5-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="85ce5-109">[in] Název, který omezuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="85ce5-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="85ce5-110">[out] Pole pro ukládání tokenů MethodDef.</span><span class="sxs-lookup"><span data-stu-id="85ce5-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="85ce5-111">[in] Maximální velikost `rMethods` pole.</span><span class="sxs-lookup"><span data-stu-id="85ce5-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="85ce5-112">[out] Počet tokenů MethodDef vrácené v `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="85ce5-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85ce5-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85ce5-113">Remarks</span></span>  
 <span data-ttu-id="85ce5-114">Tato metoda vytváří výčet polí a metod, ale nikoli vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="85ce5-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="85ce5-115">Na rozdíl od [imetadataimport::enummethods –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` zahodí všechny tokeny metody, které nemají se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="85ce5-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85ce5-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="85ce5-116">Return Value</span></span>  
  
|<span data-ttu-id="85ce5-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85ce5-117">HRESULT</span></span>|<span data-ttu-id="85ce5-118">Popis</span><span class="sxs-lookup"><span data-stu-id="85ce5-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="85ce5-119">`EnumMethodsWithName` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="85ce5-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="85ce5-120">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="85ce5-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="85ce5-121">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="85ce5-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85ce5-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85ce5-122">Requirements</span></span>  
 <span data-ttu-id="85ce5-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85ce5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85ce5-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="85ce5-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85ce5-125">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85ce5-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85ce5-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85ce5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ce5-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85ce5-127">See also</span></span>

- [<span data-ttu-id="85ce5-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85ce5-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="85ce5-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85ce5-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
