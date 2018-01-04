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
ms.workload: dotnet
ms.openlocfilehash: 758ea4261b859773c600ca91d52e3a9053776136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="be6a0-102">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be6a0-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="be6a0-103">Poskytuje metody pro mapování knihoven typů do jejich signatur metadata a převést z jeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="be6a0-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be6a0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="be6a0-104">Methods</span></span>  
  
|<span data-ttu-id="be6a0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="be6a0-105">Method</span></span>|<span data-ttu-id="be6a0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="be6a0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be6a0-107">GetMetaDataFromTypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="be6a0-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="be6a0-108">Získá odkazy [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instanci, která představuje metadata podpis pro knihovny typů, který odkazuje zadaný `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="be6a0-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="be6a0-109">GetMetaDataFromTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="be6a0-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="be6a0-110">Získá odkazy `IMetaDataImport` instanci, která představuje metadata podpis pro knihovny typů reprezentována zadaný `ITypeLib` instance.</span><span class="sxs-lookup"><span data-stu-id="be6a0-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="be6a0-111">GetTypeLibFromMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="be6a0-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="be6a0-112">Získá odkazy `ITypeLib` instanci, která představuje knihovny typů, který má zadané názvy modulu a knihovny.</span><span class="sxs-lookup"><span data-stu-id="be6a0-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be6a0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be6a0-113">Requirements</span></span>  
 <span data-ttu-id="be6a0-114">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be6a0-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be6a0-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="be6a0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be6a0-116">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be6a0-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be6a0-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be6a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be6a0-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="be6a0-118">See Also</span></span>  
 [<span data-ttu-id="be6a0-119">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="be6a0-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="be6a0-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be6a0-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
