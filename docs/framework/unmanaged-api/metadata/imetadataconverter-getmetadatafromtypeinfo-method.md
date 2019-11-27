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
ms.openlocfilehash: df7be11e8f275824fca658a9604178e7cf28e3ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436288"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="dc66d-102">IMetaDataConverter::GetMetaDataFromTypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="dc66d-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="dc66d-103">Získá ukazatel na instanci [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , která představuje podpis metadat knihovny typů, na kterou odkazuje zadaná instance `ITypeInfo`.</span><span class="sxs-lookup"><span data-stu-id="dc66d-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc66d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc66d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc66d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc66d-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="dc66d-106">pro Ukazatel na objekt `ITypeInfo`, který odkazuje na knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="dc66d-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="dc66d-107">mimo Ukazatel na umístění, které přijímá adresu `IMetaDataImport` instance, která představuje signaturu metadat.</span><span class="sxs-lookup"><span data-stu-id="dc66d-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc66d-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc66d-108">Requirements</span></span>  
 <span data-ttu-id="dc66d-109">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc66d-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc66d-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dc66d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc66d-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="dc66d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc66d-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc66d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc66d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc66d-113">See also</span></span>

- [<span data-ttu-id="dc66d-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc66d-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dc66d-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc66d-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
