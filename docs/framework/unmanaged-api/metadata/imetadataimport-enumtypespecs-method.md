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
ms.openlocfilehash: 7a4273b36ce3e761348a091df3acb41212e1df05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722312"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="1c0e1-102">IMetaDataImport::EnumTypeSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="1c0e1-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="1c0e1-103">Vytvoří výčet token TypeSpec tokeny definované v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="1c0e1-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c0e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c0e1-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c0e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c0e1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1c0e1-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="1c0e1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="1c0e1-107">Tato hodnota musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="1c0e1-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="1c0e1-108">[out] Pole pro ukládání tokenů token TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="1c0e1-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1c0e1-109">[in] Maximální velikost `rTypeSpecs` pole.</span><span class="sxs-lookup"><span data-stu-id="1c0e1-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="1c0e1-110">[out] Počet tokenů token TypeSpec vrácené v `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="1c0e1-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c0e1-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1c0e1-111">Return Value</span></span>  
  
|<span data-ttu-id="1c0e1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c0e1-112">HRESULT</span></span>|<span data-ttu-id="1c0e1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1c0e1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1c0e1-114">`EnumTypeSpecs` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="1c0e1-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1c0e1-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="1c0e1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="1c0e1-116">V takovém případě `pcTypeSpecs` je nula.</span><span class="sxs-lookup"><span data-stu-id="1c0e1-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c0e1-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c0e1-117">Remarks</span></span>  
 <span data-ttu-id="1c0e1-118">Token TypeSpec tokeny jsou vytvářeny [imetadataemit::gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1c0e1-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c0e1-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c0e1-119">Requirements</span></span>  
 <span data-ttu-id="1c0e1-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c0e1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c0e1-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1c0e1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c0e1-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c0e1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c0e1-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c0e1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0e1-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c0e1-124">See also</span></span>
- [<span data-ttu-id="1c0e1-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c0e1-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1c0e1-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c0e1-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
