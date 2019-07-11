---
title: IMetaDataConverter::GetMetaDataFromTypeInfo – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 906ab3603d9a4926642848b547a793f129f949ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782038"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="d8f24-102">IMetaDataConverter::GetMetaDataFromTypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="d8f24-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="d8f24-103">Získá ukazatel [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instanci, která představuje podpis metadat knihovny typů odkazuje zadaný `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="d8f24-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8f24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8f24-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8f24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8f24-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="d8f24-106">[in] Ukazatel `ITypeInfo` objekt, který odkazuje na knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="d8f24-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="d8f24-107">[out] Ukazatel na umístění, která bude přijímat adresy `IMetaDataImport` instanci, která představuje podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="d8f24-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8f24-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8f24-108">Requirements</span></span>  
 <span data-ttu-id="d8f24-109">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8f24-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8f24-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d8f24-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8f24-111">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8f24-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8f24-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8f24-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f24-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8f24-113">See also</span></span>

- [<span data-ttu-id="d8f24-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8f24-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d8f24-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8f24-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
