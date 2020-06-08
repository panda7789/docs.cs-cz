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
ms.openlocfilehash: 91ae326a89e463d26b39c1659d872130042557bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492007"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="4e7d8-102">IMetaDataImport::EnumMethods – metoda</span><span class="sxs-lookup"><span data-stu-id="4e7d8-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="4e7d8-103">Vytvoří výčet tokenů MethodDef představujících metody zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="4e7d8-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e7d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e7d8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e7d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e7d8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4e7d8-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="4e7d8-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4e7d8-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="4e7d8-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="4e7d8-108">pro Token TypeDef představující typ s metodami k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="4e7d8-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="4e7d8-109">mimo Pole, do kterého se mají ukládat tokeny MethodDef</span><span class="sxs-lookup"><span data-stu-id="4e7d8-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4e7d8-110">pro Maximální velikost `rMethods` pole MethodDef.</span><span class="sxs-lookup"><span data-stu-id="4e7d8-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4e7d8-111">mimo Počet tokenů MethodDef vrácených v `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="4e7d8-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e7d8-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4e7d8-112">Return Value</span></span>  
  
|<span data-ttu-id="4e7d8-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4e7d8-113">HRESULT</span></span>|<span data-ttu-id="4e7d8-114">Description</span><span class="sxs-lookup"><span data-stu-id="4e7d8-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4e7d8-115">`EnumMethods`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="4e7d8-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4e7d8-116">Nejsou k dispozici žádné tokeny MethodDef pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="4e7d8-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="4e7d8-117">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="4e7d8-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e7d8-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e7d8-118">Requirements</span></span>  
 <span data-ttu-id="4e7d8-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e7d8-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e7d8-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4e7d8-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e7d8-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4e7d8-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4e7d8-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e7d8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7d8-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e7d8-123">See also</span></span>

- [<span data-ttu-id="4e7d8-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e7d8-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4e7d8-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e7d8-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
