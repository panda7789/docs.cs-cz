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
ms.openlocfilehash: f9f3e3f196f74a7dea3c722925f1d03968688882
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008999"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="facbb-102">IMetaDataConverter::GetMetaDataFromTypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="facbb-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="facbb-103">Získá ukazatel na instanci [IMetaDataImport](imetadataimport-interface.md) , která představuje podpis metadat knihovny typů, na kterou odkazuje zadaná `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="facbb-103">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="facbb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="facbb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="facbb-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="facbb-106">pro Ukazatel na `ITypeInfo` objekt, který odkazuje na knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="facbb-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="facbb-107">mimo Ukazatel na umístění, které přijímá adresu `IMetaDataImport` instance, která představuje podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="facbb-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="facbb-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="facbb-108">Requirements</span></span>  
 <span data-ttu-id="facbb-109">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="facbb-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facbb-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="facbb-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="facbb-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="facbb-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="facbb-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="facbb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facbb-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="facbb-113">See also</span></span>

- [<span data-ttu-id="facbb-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="facbb-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="facbb-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="facbb-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
