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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d3377617ddd6b82ad88d22f6ffda04b1d6ae837
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096121"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="2e402-102">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e402-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="2e402-103">Poskytuje metody pro mapování knihovny typů na jejich podpisy metadat a pro převod z jednoho na druhý.</span><span class="sxs-lookup"><span data-stu-id="2e402-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e402-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2e402-104">Methods</span></span>  
  
|<span data-ttu-id="2e402-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2e402-105">Method</span></span>|<span data-ttu-id="2e402-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2e402-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e402-107">GetMetaDataFromTypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="2e402-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="2e402-108">Získá ukazatel [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instanci, která představuje podpis metadat pro knihovnu typů odkazuje zadaný `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="2e402-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="2e402-109">GetMetaDataFromTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="2e402-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="2e402-110">Získá ukazatel na `IMetaDataImport` instanci, která představuje podpis metadat pro knihovnu typů reprezentována zadaný `ITypeLib` instance.</span><span class="sxs-lookup"><span data-stu-id="2e402-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="2e402-111">GetTypeLibFromMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="2e402-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="2e402-112">Získá ukazatel `ITypeLib` instanci, která představuje knihovnu typů, který má zadané názvy modulů a knihovna.</span><span class="sxs-lookup"><span data-stu-id="2e402-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e402-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e402-113">Requirements</span></span>  
 <span data-ttu-id="2e402-114">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e402-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e402-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2e402-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e402-116">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e402-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="2e402-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2e402-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e402-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e402-118">See also</span></span>

- [<span data-ttu-id="2e402-119">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="2e402-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="2e402-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e402-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
