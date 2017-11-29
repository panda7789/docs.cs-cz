---
title: "IMetaDataConverter – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter
helpviewer_keywords: IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f551a774a860f595cc90a7cca9eee2c726ef50ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="7f3dc-102">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f3dc-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="7f3dc-103">Poskytuje metody pro mapování knihoven typů do jejich signatur metadata a převést z jeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="7f3dc-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f3dc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7f3dc-104">Methods</span></span>  
  
|<span data-ttu-id="7f3dc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7f3dc-105">Method</span></span>|<span data-ttu-id="7f3dc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7f3dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f3dc-107">Getmetadatafromtypeinfo – metoda</span><span class="sxs-lookup"><span data-stu-id="7f3dc-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="7f3dc-108">Získá odkazy [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instanci, která představuje metadata podpis pro knihovny typů, který odkazuje zadaný `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="7f3dc-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="7f3dc-109">Getmetadatafromtypelib – metoda</span><span class="sxs-lookup"><span data-stu-id="7f3dc-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="7f3dc-110">Získá odkazy `IMetaDataImport` instanci, která představuje metadata podpis pro knihovny typů reprezentována zadaný `ITypeLib` instance.</span><span class="sxs-lookup"><span data-stu-id="7f3dc-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="7f3dc-111">Gettypelibfrommetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="7f3dc-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="7f3dc-112">Získá odkazy `ITypeLib` instanci, která představuje knihovny typů, který má zadané názvy modulu a knihovny.</span><span class="sxs-lookup"><span data-stu-id="7f3dc-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f3dc-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f3dc-113">Requirements</span></span>  
 <span data-ttu-id="7f3dc-114">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f3dc-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f3dc-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7f3dc-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f3dc-116">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f3dc-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f3dc-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f3dc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f3dc-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f3dc-118">See Also</span></span>  
 [<span data-ttu-id="7f3dc-119">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="7f3dc-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="7f3dc-120">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f3dc-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
