---
title: IMetaDataConverter – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: b771b368c069a4577d266b47bfb4a5ee1935e48e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436267"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="f84bc-102">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f84bc-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="f84bc-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span><span class="sxs-lookup"><span data-stu-id="f84bc-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f84bc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f84bc-104">Methods</span></span>  
  
|<span data-ttu-id="f84bc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f84bc-105">Method</span></span>|<span data-ttu-id="f84bc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f84bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f84bc-107">GetMetaDataFromTypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="f84bc-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="f84bc-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="f84bc-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="f84bc-109">GetMetaDataFromTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="f84bc-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="f84bc-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span><span class="sxs-lookup"><span data-stu-id="f84bc-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="f84bc-111">GetTypeLibFromMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="f84bc-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="f84bc-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span><span class="sxs-lookup"><span data-stu-id="f84bc-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f84bc-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f84bc-113">Requirements</span></span>  
 <span data-ttu-id="f84bc-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f84bc-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f84bc-115">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f84bc-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f84bc-116">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f84bc-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f84bc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f84bc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f84bc-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f84bc-118">See also</span></span>

- [<span data-ttu-id="f84bc-119">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="f84bc-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="f84bc-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f84bc-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
