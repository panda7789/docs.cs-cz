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
ms.openlocfilehash: 218b65b5899692774c434ae136a3976ecb97ea2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177311"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="96244-102">IMetaDataImport::EnumMethods – metoda</span><span class="sxs-lookup"><span data-stu-id="96244-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="96244-103">Výčet tokenů MethodDef představujících metody zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="96244-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96244-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96244-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96244-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96244-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="96244-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="96244-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="96244-107">To musí být NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="96244-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="96244-108">[v] A TypeDef token představující typ s metodami pro výčet.</span><span class="sxs-lookup"><span data-stu-id="96244-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="96244-109">[out] Pole pro uložení tokenů MethodDef.</span><span class="sxs-lookup"><span data-stu-id="96244-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="96244-110">[v] Maximální velikost pole MethodDef. `rMethods`</span><span class="sxs-lookup"><span data-stu-id="96244-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="96244-111">[out] Počet tokenů MethodDef vrácených v `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="96244-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96244-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="96244-112">Return Value</span></span>  
  
|<span data-ttu-id="96244-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96244-113">HRESULT</span></span>|<span data-ttu-id="96244-114">Popis</span><span class="sxs-lookup"><span data-stu-id="96244-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="96244-115">`EnumMethods`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="96244-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="96244-116">Neexistují žádné tokeny MethodDef k výčetu.</span><span class="sxs-lookup"><span data-stu-id="96244-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="96244-117">V tom `pcTokens` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="96244-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96244-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96244-118">Requirements</span></span>  
 <span data-ttu-id="96244-119">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96244-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96244-120">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="96244-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96244-121">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96244-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96244-122">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96244-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96244-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="96244-123">See also</span></span>

- [<span data-ttu-id="96244-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96244-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="96244-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96244-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
