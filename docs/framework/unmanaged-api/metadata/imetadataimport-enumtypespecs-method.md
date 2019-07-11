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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81592b6da7fa7cdf275e9fa5b4b82ef0a15061c0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782571"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="fda9f-102">IMetaDataImport::EnumTypeSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="fda9f-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="fda9f-103">Vytvoří výčet token TypeSpec tokeny definované v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="fda9f-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fda9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fda9f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fda9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fda9f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="fda9f-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="fda9f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="fda9f-107">Tato hodnota musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="fda9f-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="fda9f-108">[out] Pole pro ukládání tokenů token TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="fda9f-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fda9f-109">[in] Maximální velikost `rTypeSpecs` pole.</span><span class="sxs-lookup"><span data-stu-id="fda9f-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="fda9f-110">[out] Počet tokenů token TypeSpec vrácené v `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="fda9f-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fda9f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fda9f-111">Return Value</span></span>  
  
|<span data-ttu-id="fda9f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fda9f-112">HRESULT</span></span>|<span data-ttu-id="fda9f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="fda9f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fda9f-114">`EnumTypeSpecs` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="fda9f-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fda9f-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="fda9f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="fda9f-116">V takovém případě `pcTypeSpecs` je nula.</span><span class="sxs-lookup"><span data-stu-id="fda9f-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fda9f-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fda9f-117">Remarks</span></span>  
 <span data-ttu-id="fda9f-118">Token TypeSpec tokeny jsou vytvářeny [imetadataemit::gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fda9f-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fda9f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fda9f-119">Requirements</span></span>  
 <span data-ttu-id="fda9f-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fda9f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fda9f-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fda9f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fda9f-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fda9f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fda9f-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fda9f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda9f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fda9f-124">See also</span></span>

- [<span data-ttu-id="fda9f-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fda9f-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fda9f-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fda9f-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
