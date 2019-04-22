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
ms.openlocfilehash: cdc1b0de9795a000ee680df880c73acc4f711db2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145324"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="109a8-102">IMetaDataConverter::GetMetaDataFromTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="109a8-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="109a8-103">Získá ukazatel rozhraní k [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instanci, která představuje podpis metadat reprezentována zadané knihovny typů `ITypeLib` instance.</span><span class="sxs-lookup"><span data-stu-id="109a8-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="109a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="109a8-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="109a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="109a8-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="109a8-106">[in] Ukazatel `ITypeLib` objekt, který představuje knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="109a8-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="109a8-107">[out] Ukazatel na umístění, která bude přijímat adresy `IMetaDataImport` instanci, která představuje podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="109a8-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="109a8-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="109a8-108">Requirements</span></span>  
 <span data-ttu-id="109a8-109">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="109a8-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="109a8-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="109a8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="109a8-111">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="109a8-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="109a8-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="109a8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="109a8-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="109a8-113">See also</span></span>

- [<span data-ttu-id="109a8-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="109a8-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="109a8-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="109a8-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
