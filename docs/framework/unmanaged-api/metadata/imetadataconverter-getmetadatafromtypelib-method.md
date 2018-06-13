---
title: IMetaDataConverter::GetMetaDataFromTypeLib – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdd2aeb54e9d3c78c58b1a8b497839e876038dfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443636"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="a0fe3-102">IMetaDataConverter::GetMetaDataFromTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="a0fe3-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="a0fe3-103">Získá ukazatele rozhraní k [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instanci, která představuje metadata podpis knihovny typů reprezentována zadaný `ITypeLib` instance.</span><span class="sxs-lookup"><span data-stu-id="a0fe3-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0fe3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0fe3-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0fe3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0fe3-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="a0fe3-106">[v] Ukazatel na `ITypeLib` objekt, který reprezentuje knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="a0fe3-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="a0fe3-107">[out] Ukazatel na umístění, která přijímá adresu `IMetaDataImport` instanci, která představuje metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="a0fe3-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0fe3-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0fe3-108">Requirements</span></span>  
 <span data-ttu-id="a0fe3-109">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0fe3-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0fe3-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a0fe3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0fe3-111">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0fe3-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0fe3-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0fe3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0fe3-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0fe3-113">See Also</span></span>  
 [<span data-ttu-id="a0fe3-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0fe3-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a0fe3-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0fe3-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
