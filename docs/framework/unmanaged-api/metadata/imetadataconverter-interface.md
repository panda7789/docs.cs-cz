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
ms.openlocfilehash: 29709a4297d53cc5e40daf732ac89751ead95152
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449038"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="fd3d9-102">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd3d9-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="fd3d9-103">Poskytuje metody pro mapování knihoven typů do jejich signatur metadata a převést z jeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="fd3d9-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd3d9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fd3d9-104">Methods</span></span>  
  
|<span data-ttu-id="fd3d9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fd3d9-105">Method</span></span>|<span data-ttu-id="fd3d9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fd3d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd3d9-107">GetMetaDataFromTypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="fd3d9-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="fd3d9-108">Získá odkazy [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instanci, která představuje metadata podpis pro knihovny typů, který odkazuje zadaný `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="fd3d9-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="fd3d9-109">GetMetaDataFromTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="fd3d9-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="fd3d9-110">Získá odkazy `IMetaDataImport` instanci, která představuje metadata podpis pro knihovny typů reprezentována zadaný `ITypeLib` instance.</span><span class="sxs-lookup"><span data-stu-id="fd3d9-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="fd3d9-111">GetTypeLibFromMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="fd3d9-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="fd3d9-112">Získá odkazy `ITypeLib` instanci, která představuje knihovny typů, který má zadané názvy modulu a knihovny.</span><span class="sxs-lookup"><span data-stu-id="fd3d9-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd3d9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd3d9-113">Requirements</span></span>  
 <span data-ttu-id="fd3d9-114">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd3d9-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd3d9-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fd3d9-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd3d9-116">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd3d9-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd3d9-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd3d9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd3d9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd3d9-118">See Also</span></span>  
 [<span data-ttu-id="fd3d9-119">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="fd3d9-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="fd3d9-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd3d9-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
