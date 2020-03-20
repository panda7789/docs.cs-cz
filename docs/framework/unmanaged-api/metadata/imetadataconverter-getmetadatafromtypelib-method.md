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
ms.openlocfilehash: 09a1605deda5b51be604c3b8f0c69fa5adcf9dc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175951"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="144c4-102">IMetaDataConverter::GetMetaDataFromTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="144c4-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="144c4-103">Získá ukazatel rozhraní na instanci [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) která představuje podpis metadat `ITypeLib` knihovny typů reprezentované zadanou instancí.</span><span class="sxs-lookup"><span data-stu-id="144c4-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="144c4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="144c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="144c4-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="144c4-106">[v] Ukazatel na `ITypeLib` objekt, který představuje knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="144c4-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="144c4-107">[out] Ukazatel na umístění, které přijímá `IMetaDataImport` adresu instance, která představuje podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="144c4-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="144c4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="144c4-108">Requirements</span></span>  
 <span data-ttu-id="144c4-109">**Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="144c4-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="144c4-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="144c4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="144c4-111">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="144c4-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="144c4-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="144c4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="144c4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="144c4-113">See also</span></span>

- [<span data-ttu-id="144c4-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="144c4-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="144c4-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="144c4-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
