---
title: "IMetaDataImport2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2
helpviewer_keywords: IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1b00879f1d22d49e5f0dc3bdb072e0545feda68d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="3f466-102">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f466-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="3f466-103">Rozšiřuje [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní poskytovat funkce pracovat s obecné typy.</span><span class="sxs-lookup"><span data-stu-id="3f466-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f466-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3f466-104">Methods</span></span>  
  
|<span data-ttu-id="3f466-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3f466-105">Method</span></span>|<span data-ttu-id="3f466-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3f466-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f466-107">Enumgenericparamconstraints – metoda</span><span class="sxs-lookup"><span data-stu-id="3f466-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="3f466-108">Získá enumerátor pro pole obecný parametr omezení spojené s obecný parametr reprezentována zadaný token.</span><span class="sxs-lookup"><span data-stu-id="3f466-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="3f466-109">Enumgenericparams – metoda</span><span class="sxs-lookup"><span data-stu-id="3f466-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="3f466-110">Získá enumerátor pro pole obecný parametr tokeny přidružený k zadané TypeDef nebo MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="3f466-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="3f466-111">Enummethodspecs – metoda</span><span class="sxs-lookup"><span data-stu-id="3f466-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="3f466-112">Získá enumerátor pro pole MethodSpec tokeny přidružený k zadané MethodDef nebo MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="3f466-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="3f466-113">Getgenericparamconstraintprops – metoda</span><span class="sxs-lookup"><span data-stu-id="3f466-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="3f466-114">Získá metadata spojená s omezením obecný parametr reprezentována token zadané omezení.</span><span class="sxs-lookup"><span data-stu-id="3f466-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="3f466-115">Getgenericparamprops – metoda</span><span class="sxs-lookup"><span data-stu-id="3f466-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="3f466-116">Získá metadata přidružená obecný parametr reprezentována zadaný token.</span><span class="sxs-lookup"><span data-stu-id="3f466-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="3f466-117">Getmethodspecprops – metoda</span><span class="sxs-lookup"><span data-stu-id="3f466-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="3f466-118">Získá metadata podpis metody odkazuje zadaný MethodSpec token.</span><span class="sxs-lookup"><span data-stu-id="3f466-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="3f466-119">GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="3f466-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="3f466-120">Získá hodnotu identifikace povaha kód na přenosné spustitelný soubor (PE) souboru, obvykle DLL nebo EXE soubor, definovaná v aktuálním oboru metadat</span><span class="sxs-lookup"><span data-stu-id="3f466-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="3f466-121">Getversionstring – metoda</span><span class="sxs-lookup"><span data-stu-id="3f466-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="3f466-122">Získá číslo verze modulu runtime, který byl použit k vytvoření sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f466-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f466-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f466-123">Requirements</span></span>  
 <span data-ttu-id="3f466-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f466-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f466-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f466-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f466-126">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f466-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f466-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f466-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f466-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f466-128">See Also</span></span>  
 <xref:System.Reflection.PortableExecutableKinds>  
 [<span data-ttu-id="3f466-129">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="3f466-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="3f466-130">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f466-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
