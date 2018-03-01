---
title: "IMetaDataConverter::GetMetaDataFromTypeInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 66e090efc9ce8a8fc1ca5de8d8f7a60f9ca17b9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="d16f6-102">IMetaDataConverter::GetMetaDataFromTypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="d16f6-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="d16f6-103">Získá odkazy [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instanci, která představuje metadata podpis knihovny typů, který odkazuje zadaný `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="d16f6-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d16f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d16f6-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d16f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d16f6-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="d16f6-106">[v] Ukazatel na `ITypeInfo` objekt, který odkazuje na knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="d16f6-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="d16f6-107">[out] Ukazatel na umístění, která přijímá adresu `IMetaDataImport` instanci, která představuje metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="d16f6-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d16f6-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d16f6-108">Requirements</span></span>  
 <span data-ttu-id="d16f6-109">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d16f6-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d16f6-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d16f6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d16f6-111">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d16f6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d16f6-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d16f6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d16f6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d16f6-113">See Also</span></span>  
 [<span data-ttu-id="d16f6-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d16f6-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d16f6-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d16f6-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
