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
ms.openlocfilehash: 8f8c0c2cb8dea8ad2b9c0040654122ef5942aca0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008388"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="0ab34-102">IMetaDataConverter::GetMetaDataFromTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="0ab34-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="0ab34-103">Získá ukazatel rozhraní na instanci [IMetaDataImport](imetadataimport-interface.md) , která představuje podpis metadat knihovny typů reprezentované zadanou `ITypeLib` instancí.</span><span class="sxs-lookup"><span data-stu-id="0ab34-103">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ab34-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ab34-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ab34-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="0ab34-106">pro Ukazatel na `ITypeLib` objekt, který představuje knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="0ab34-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="0ab34-107">mimo Ukazatel na umístění, které přijímá adresu `IMetaDataImport` instance, která představuje podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="0ab34-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ab34-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ab34-108">Requirements</span></span>  
 <span data-ttu-id="0ab34-109">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ab34-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ab34-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0ab34-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ab34-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="0ab34-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ab34-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ab34-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab34-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ab34-113">See also</span></span>

- [<span data-ttu-id="0ab34-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ab34-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0ab34-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ab34-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
