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
ms.openlocfilehash: 6391e819d53c3ed8f0d596b15c4a2bb268f72fd5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436287"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="d82b5-102">IMetaDataConverter::GetMetaDataFromTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="d82b5-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="d82b5-103">Získá ukazatel rozhraní na instanci [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , která představuje podpis metadat knihovny typů reprezentované zadanou instancí `ITypeLib`.</span><span class="sxs-lookup"><span data-stu-id="d82b5-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d82b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d82b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d82b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d82b5-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="d82b5-106">pro Ukazatel na objekt `ITypeLib`, který představuje knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="d82b5-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="d82b5-107">mimo Ukazatel na umístění, které přijímá adresu `IMetaDataImport` instance, která představuje signaturu metadat.</span><span class="sxs-lookup"><span data-stu-id="d82b5-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d82b5-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d82b5-108">Requirements</span></span>  
 <span data-ttu-id="d82b5-109">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d82b5-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d82b5-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d82b5-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d82b5-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="d82b5-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d82b5-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d82b5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82b5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d82b5-113">See also</span></span>

- [<span data-ttu-id="d82b5-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d82b5-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d82b5-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d82b5-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
