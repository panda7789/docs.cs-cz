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
ms.openlocfilehash: b0817288040550b5f4c3c4ec063f6a7fdb004137
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450062"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="b8251-102">IMetaDataImport::EnumMethodsWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="b8251-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="b8251-103">Vytvoří výčet metod, které mají zadaný název a které jsou definovány typem, na který odkazuje zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="b8251-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8251-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8251-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b8251-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8251-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b8251-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="b8251-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b8251-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="b8251-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="b8251-108">pro Token TypeDef představující typ, jehož metody se mají vytvořit.</span><span class="sxs-lookup"><span data-stu-id="b8251-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="b8251-109">pro Název, který omezuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="b8251-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="b8251-110">mimo Pole použité k uložení tokenů MethodDef</span><span class="sxs-lookup"><span data-stu-id="b8251-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b8251-111">pro Maximální velikost `rMethods` pole</span><span class="sxs-lookup"><span data-stu-id="b8251-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b8251-112">mimo Počet tokenů MethodDef vrácených v `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="b8251-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8251-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8251-113">Remarks</span></span>  
 <span data-ttu-id="b8251-114">Tato metoda vytváří výčet polí a metod, ale ne vlastností nebo událostí.</span><span class="sxs-lookup"><span data-stu-id="b8251-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="b8251-115">Na rozdíl od [IMetaDataImport:: enummethods –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)`EnumMethodsWithName` zahodí všechny tokeny metod, které nemají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="b8251-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8251-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b8251-116">Return Value</span></span>  
  
|<span data-ttu-id="b8251-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8251-117">HRESULT</span></span>|<span data-ttu-id="b8251-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b8251-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b8251-119">`EnumMethodsWithName` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b8251-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b8251-120">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="b8251-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="b8251-121">V takovém případě je `pcTokens` nula.</span><span class="sxs-lookup"><span data-stu-id="b8251-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8251-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8251-122">Requirements</span></span>  
 <span data-ttu-id="b8251-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8251-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8251-124">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b8251-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8251-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b8251-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8251-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8251-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8251-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8251-127">See also</span></span>

- [<span data-ttu-id="b8251-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8251-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b8251-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8251-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
