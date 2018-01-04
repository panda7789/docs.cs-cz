---
title: "Rozhraní metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4043bdb7ea128e7ac34349dad8c51a0b247df71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-interfaces"></a><span data-ttu-id="d0ccf-102">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="d0ccf-102">Metadata Interfaces</span></span>
<span data-ttu-id="d0ccf-103">Tato část popisuje nespravovaná rozhraní, které poskytují přístup k metadatům vystavené typy rozhraní .NET Framework, metody, pole a tak dále.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0ccf-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d0ccf-104">In This Section</span></span>  
 [<span data-ttu-id="d0ccf-105">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="d0ccf-106">Poskytuje metody pro dynamický kód kompilace.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="d0ccf-107">IHostFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="d0ccf-108">Poskytuje metodu pro spuštění hostitele k označení tokenů metadat pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="d0ccf-109">IMapToken – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="d0ccf-110">Poskytuje možnosti mapování mezi naimportována a vygenerované podpisy metadat.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="d0ccf-111">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="d0ccf-112">Poskytuje metody, které podporují vlastní popis modelu používaný modul CLR (CLR) řešení a využívat prostředky.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="d0ccf-113">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="d0ccf-114">Poskytuje metody pro přístup a kontrolu obsah manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="d0ccf-115">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="d0ccf-116">Poskytuje metody pro mapování knihoven typů do jejich signatur metadata a převést z jeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="d0ccf-117">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="d0ccf-118">`IMetaDataDispenser`je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="d0ccf-119">Místo nich se používá `IMetaDataDispenserEx`.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="d0ccf-120">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="d0ccf-121">Poskytuje metody, které mapují oblasti paměti pro vytvoření nebo úprava metadat.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="d0ccf-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="d0ccf-123">Poskytuje metody pro vytváření, úpravě a ukládat metadata o sestavení v aktuálně definován obor.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="d0ccf-124">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="d0ccf-125">Poskytuje metody pro definování a úprava metadat podpisy metod a konstruktory s parametry typu <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="d0ccf-126">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="d0ccf-127">Poskytuje mechanismus zpětného volání pro oznamování chyb při překladu podpis metadata pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="d0ccf-128">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="d0ccf-129">Poskytuje metody pro označování a filtrování tokenů metadat, aby se zabránilo opakující se akce, které již byla přijata.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="d0ccf-130">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="d0ccf-131">Poskytuje metody pro import a manipulace s typy od ostatních sestavení.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="d0ccf-132">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="d0ccf-133">Rozšiřuje `IMetaDataImport` poskytovat funkce pracovat s obecné typy.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="d0ccf-134">IMetaDataInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="d0ccf-135">Poskytne metodu, která se získá informace o mapování metadat ze souboru na disku do paměti.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="d0ccf-136">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="d0ccf-137">Poskytuje metody pro ukládání a načítání informací metadat v tabulkách.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="d0ccf-138">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="d0ccf-139">Rozšiřuje `IMetaDataTables` zahrnout metody pro práci s datovými proudy metadat.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="d0ccf-140">IMetaDataValidate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ccf-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="d0ccf-141">Poskytuje metody k ověření podpisů metadat.</span><span class="sxs-lookup"><span data-stu-id="d0ccf-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d0ccf-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d0ccf-142">Related Sections</span></span>  
 [<span data-ttu-id="d0ccf-143">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="d0ccf-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="d0ccf-144">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="d0ccf-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="d0ccf-145">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="d0ccf-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="d0ccf-146">Sjednocení pro metadata</span><span class="sxs-lookup"><span data-stu-id="d0ccf-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
