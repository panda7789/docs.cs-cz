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
ms.openlocfilehash: 66a09baea1df2e2de418bdce8821672802f1f51f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491729"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="7f5de-102">IMetaDataImport::EnumMethodsWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="7f5de-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="7f5de-103">Vytvoří výčet metod, které mají zadaný název a které jsou definovány typem, na který odkazuje zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="7f5de-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f5de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f5de-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7f5de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f5de-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7f5de-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="7f5de-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7f5de-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="7f5de-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="7f5de-108">pro Token TypeDef představující typ, jehož metody se mají vytvořit.</span><span class="sxs-lookup"><span data-stu-id="7f5de-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="7f5de-109">pro Název, který omezuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="7f5de-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="7f5de-110">mimo Pole použité k uložení tokenů MethodDef</span><span class="sxs-lookup"><span data-stu-id="7f5de-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7f5de-111">pro Maximální velikost `rMethods` pole.</span><span class="sxs-lookup"><span data-stu-id="7f5de-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7f5de-112">mimo Počet tokenů MethodDef vrácených v `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="7f5de-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f5de-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f5de-113">Remarks</span></span>  
 <span data-ttu-id="7f5de-114">Tato metoda vytváří výčet polí a metod, ale ne vlastností nebo událostí.</span><span class="sxs-lookup"><span data-stu-id="7f5de-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="7f5de-115">Na rozdíl od [IMetaDataImport:: enummethods –](imetadataimport-enummethods-method.md) `EnumMethodsWithName` zahodí všechny tokeny metod, které nemají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="7f5de-115">Unlike [IMetaDataImport::EnumMethods](imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f5de-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7f5de-116">Return Value</span></span>  
  
|<span data-ttu-id="7f5de-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f5de-117">HRESULT</span></span>|<span data-ttu-id="7f5de-118">Description</span><span class="sxs-lookup"><span data-stu-id="7f5de-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7f5de-119">`EnumMethodsWithName`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="7f5de-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7f5de-120">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="7f5de-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="7f5de-121">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="7f5de-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f5de-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f5de-122">Requirements</span></span>  
 <span data-ttu-id="7f5de-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f5de-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f5de-124">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7f5de-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f5de-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7f5de-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f5de-126">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f5de-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f5de-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f5de-127">See also</span></span>

- [<span data-ttu-id="7f5de-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f5de-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7f5de-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f5de-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
