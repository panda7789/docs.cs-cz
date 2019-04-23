---
title: IMetaDataImport2::EnumGenericParams – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7edd2eeafcce6a22c3256d0684a9c4f961b34002
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157635"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="ce8de-102">IMetaDataImport2::EnumGenericParams – metoda</span><span class="sxs-lookup"><span data-stu-id="ce8de-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="ce8de-103">Získá enumerátor pro celou řadu obecný parametr tokeny přidružené k zadaným TypeDef nebo MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="ce8de-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce8de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce8de-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce8de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce8de-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ce8de-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="ce8de-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="ce8de-107">[in] Token TypeDef nebo MethodDef jehož generické parametry jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="ce8de-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="ce8de-108">[out] Pole obecných parametrů k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="ce8de-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ce8de-109">[in] Maximální požadovaný počet tokenů, které mají být umístěny `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="ce8de-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="ce8de-110">[out] Vrácený počet tokenů umístit v `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="ce8de-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce8de-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ce8de-111">Return Value</span></span>  
  
|<span data-ttu-id="ce8de-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce8de-112">HRESULT</span></span>|<span data-ttu-id="ce8de-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ce8de-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ce8de-114">`EnumGenericParams` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ce8de-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ce8de-115">`phEnum` nemá žádné elementy člena.</span><span class="sxs-lookup"><span data-stu-id="ce8de-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="ce8de-116">V takovém případě `pcGenericParams` je nastavena na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="ce8de-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce8de-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce8de-117">Requirements</span></span>  
 <span data-ttu-id="ce8de-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce8de-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce8de-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ce8de-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce8de-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce8de-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ce8de-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce8de-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8de-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce8de-122">See also</span></span>

- [<span data-ttu-id="ce8de-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce8de-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="ce8de-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce8de-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
