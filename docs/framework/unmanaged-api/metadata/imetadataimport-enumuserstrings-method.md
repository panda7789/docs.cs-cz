---
title: IMetaDataImport::EnumUserStrings – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79e65d86eda2f01e1d6f2af46c5ee8e15ff03ccb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730240"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="2efa5-102">IMetaDataImport::EnumUserStrings – metoda</span><span class="sxs-lookup"><span data-stu-id="2efa5-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="2efa5-103">Vytvoří výčet řetězec tokeny představující pevně zakódované řetězce v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="2efa5-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2efa5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2efa5-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2efa5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2efa5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2efa5-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="2efa5-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2efa5-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="2efa5-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="2efa5-108">[out] Pole pro ukládání tokenů řetězec.</span><span class="sxs-lookup"><span data-stu-id="2efa5-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2efa5-109">[in] Maximální velikost `rStrings` pole.</span><span class="sxs-lookup"><span data-stu-id="2efa5-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="2efa5-110">[out] Počet tokenů řetězec vrácený v `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="2efa5-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2efa5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2efa5-111">Return Value</span></span>  
  
|<span data-ttu-id="2efa5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2efa5-112">HRESULT</span></span>|<span data-ttu-id="2efa5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2efa5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2efa5-114">`EnumUserStrings` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2efa5-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2efa5-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="2efa5-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2efa5-116">V takovém případě `pcStrings` je nula.</span><span class="sxs-lookup"><span data-stu-id="2efa5-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2efa5-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2efa5-117">Remarks</span></span>  
 <span data-ttu-id="2efa5-118">Řetězec tokeny jsou vytvářeny [imetadataemit::defineuserstring –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2efa5-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="2efa5-119">Tato metoda je určena pro použití podle Prohlížeč metadat, nikoli podle kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2efa5-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2efa5-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2efa5-120">Requirements</span></span>  
 <span data-ttu-id="2efa5-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2efa5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2efa5-122">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2efa5-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2efa5-123">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2efa5-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2efa5-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2efa5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2efa5-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2efa5-125">See also</span></span>
- [<span data-ttu-id="2efa5-126">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2efa5-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2efa5-127">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2efa5-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
