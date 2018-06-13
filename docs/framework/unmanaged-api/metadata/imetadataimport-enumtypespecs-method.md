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
ms.openlocfilehash: e9b9bc8e364342a601c0738d5a64c5eac3cb7e7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447707"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="e349b-102">IMetaDataImport::EnumTypeSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="e349b-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="e349b-103">Zobrazí typ TypeSpec tokeny definované v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="e349b-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e349b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e349b-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e349b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e349b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e349b-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="e349b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e349b-107">Tato hodnota musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="e349b-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="e349b-108">[out] Pole používá k ukládání typ TypeSpec tokenů.</span><span class="sxs-lookup"><span data-stu-id="e349b-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e349b-109">[v] Maximální velikost `rTypeSpecs` pole.</span><span class="sxs-lookup"><span data-stu-id="e349b-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="e349b-110">[out] Počet typ TypeSpec tokeny, vrátí se v `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="e349b-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e349b-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e349b-111">Return Value</span></span>  
  
|<span data-ttu-id="e349b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e349b-112">HRESULT</span></span>|<span data-ttu-id="e349b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e349b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e349b-114">`EnumTypeSpecs` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e349b-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e349b-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="e349b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e349b-116">V takovém případě `pcTypeSpecs` je nulová.</span><span class="sxs-lookup"><span data-stu-id="e349b-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e349b-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e349b-117">Remarks</span></span>  
 <span data-ttu-id="e349b-118">Typ TypeSpec tokeny jsou vytvořené pomocí [imetadataemit::gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="e349b-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e349b-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e349b-119">Requirements</span></span>  
 <span data-ttu-id="e349b-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e349b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e349b-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e349b-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e349b-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e349b-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e349b-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e349b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e349b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e349b-124">See Also</span></span>  
 [<span data-ttu-id="e349b-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e349b-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e349b-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e349b-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
