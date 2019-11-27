---
title: IMetaDataImport::EnumTypeSpecs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 42b8360ac6a7bb62f29046475d6cc98124619770
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449966"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="07590-102">IMetaDataImport::EnumTypeSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="07590-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="07590-103">Vytvoří výčet tokenů token TypeSpec definovaných v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="07590-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07590-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07590-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07590-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07590-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="07590-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="07590-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="07590-107">Tato hodnota musí být pro první volání této metody NULL.</span><span class="sxs-lookup"><span data-stu-id="07590-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="07590-108">mimo Pole, které se používá k uložení tokenů token TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="07590-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="07590-109">pro Maximální velikost `rTypeSpecs` pole</span><span class="sxs-lookup"><span data-stu-id="07590-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="07590-110">mimo Počet tokenů token TypeSpec vrácených v `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="07590-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07590-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="07590-111">Return Value</span></span>  
  
|<span data-ttu-id="07590-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07590-112">HRESULT</span></span>|<span data-ttu-id="07590-113">Popis</span><span class="sxs-lookup"><span data-stu-id="07590-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="07590-114">`EnumTypeSpecs` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="07590-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="07590-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="07590-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="07590-116">V takovém případě je `pcTypeSpecs` nula.</span><span class="sxs-lookup"><span data-stu-id="07590-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07590-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07590-117">Remarks</span></span>  
 <span data-ttu-id="07590-118">Tokeny token TypeSpec jsou vytvořeny metodou [IMetaDataEmit:: gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="07590-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07590-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07590-119">Requirements</span></span>  
 <span data-ttu-id="07590-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07590-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07590-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="07590-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07590-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="07590-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="07590-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07590-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07590-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07590-124">See also</span></span>

- [<span data-ttu-id="07590-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="07590-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="07590-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="07590-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
