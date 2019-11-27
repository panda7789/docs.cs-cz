---
title: Rozhraní metadat
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4672cb813cec4a127f7888a2273eb26c3f34c3d9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431585"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="297fd-102">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="297fd-102">Metadata Interfaces</span></span>
<span data-ttu-id="297fd-103">Tato část popisuje nespravovaná rozhraní, která poskytují přístup k metadatům uvedeným .NET Framework typy, metody, pole a tak dále.</span><span class="sxs-lookup"><span data-stu-id="297fd-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="297fd-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="297fd-104">In This Section</span></span>  
 [<span data-ttu-id="297fd-105">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="297fd-106">Poskytuje metody pro kompilaci dynamického kódu.</span><span class="sxs-lookup"><span data-stu-id="297fd-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="297fd-107">IHostFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="297fd-108">Poskytuje metodu pro hostitele za běhu k označení tokenů metadat ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="297fd-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="297fd-109">IMapToken – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="297fd-110">Poskytuje možnosti mapování mezi importovanými a generovanými podpisy metadat.</span><span class="sxs-lookup"><span data-stu-id="297fd-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="297fd-111">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="297fd-112">Poskytuje metody, které podporují model s obecným popisem používaný modulem CLR (Common Language Runtime) k překladu a spotřebě prostředků.</span><span class="sxs-lookup"><span data-stu-id="297fd-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="297fd-113">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="297fd-114">Poskytuje metody pro přístup k obsahu manifestu sestavení a jeho prohlížení.</span><span class="sxs-lookup"><span data-stu-id="297fd-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="297fd-115">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="297fd-116">Poskytuje metody pro mapování knihoven typů na signatury jejich metadat a jejich převod z jednoho na druhý.</span><span class="sxs-lookup"><span data-stu-id="297fd-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="297fd-117">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="297fd-118">`IMetaDataDispenser` je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="297fd-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="297fd-119">Místo nich se používá `IMetaDataDispenserEx`.</span><span class="sxs-lookup"><span data-stu-id="297fd-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="297fd-120">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="297fd-121">Poskytuje metody, které mapují oblasti paměti pro vytváření a úpravy metadat.</span><span class="sxs-lookup"><span data-stu-id="297fd-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="297fd-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="297fd-123">Poskytuje metody pro vytváření, úpravy a ukládání metadat sestavení v aktuálně definovaném oboru.</span><span class="sxs-lookup"><span data-stu-id="297fd-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="297fd-124">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="297fd-125">Poskytuje metody pro definování a úpravu signatur metadat metod a konstruktorů s parametry typu <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="297fd-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="297fd-126">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="297fd-127">Poskytuje mechanismus zpětného volání pro hlášení chyb během překladu signatury metadat pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="297fd-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="297fd-128">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="297fd-129">Poskytuje metody pro označování a filtrování tokenů metadat, aby nedocházelo k opakujícím se akcím, které již byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="297fd-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="297fd-130">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="297fd-131">Poskytuje metody pro import a manipulaci s typy z jiných sestavení.</span><span class="sxs-lookup"><span data-stu-id="297fd-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="297fd-132">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="297fd-133">Rozšiřuje `IMetaDataImport`, aby poskytoval schopnost pracovat s obecnými typy.</span><span class="sxs-lookup"><span data-stu-id="297fd-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="297fd-134">IMetaDataInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="297fd-135">Poskytuje metodu, která získává informace o mapování metadat ze souboru na disku do paměti.</span><span class="sxs-lookup"><span data-stu-id="297fd-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="297fd-136">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="297fd-137">Poskytuje metody pro ukládání a načítání informací o metadatech v tabulkách.</span><span class="sxs-lookup"><span data-stu-id="297fd-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="297fd-138">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="297fd-139">Rozšiřuje `IMetaDataTables`, aby zahrnoval metody pro práci s datovými proudy metadat.</span><span class="sxs-lookup"><span data-stu-id="297fd-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="297fd-140">IMetaDataValidate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="297fd-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="297fd-141">Poskytuje metody, které slouží k ověřování podpisů metadat.</span><span class="sxs-lookup"><span data-stu-id="297fd-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="297fd-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="297fd-142">Related Sections</span></span>  
 [<span data-ttu-id="297fd-143">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="297fd-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="297fd-144">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="297fd-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="297fd-145">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="297fd-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="297fd-146">Sjednocení pro metadata</span><span class="sxs-lookup"><span data-stu-id="297fd-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
