---
title: IMetaDataAssemblyImport::FindAssembliesByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: c12d3a7a7d1e52529435361aa12e22e4edeecf03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448291"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="630f6-102">IMetaDataAssemblyImport::FindAssembliesByName – metoda</span><span class="sxs-lookup"><span data-stu-id="630f6-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="630f6-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span><span class="sxs-lookup"><span data-stu-id="630f6-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="630f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="630f6-104">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="630f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="630f6-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="630f6-106">[in] The root directory in which to search for the given assembly.</span><span class="sxs-lookup"><span data-stu-id="630f6-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="630f6-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span><span class="sxs-lookup"><span data-stu-id="630f6-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="630f6-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span><span class="sxs-lookup"><span data-stu-id="630f6-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="630f6-109">These directories are probed in addition to those specified in the default probing rules.</span><span class="sxs-lookup"><span data-stu-id="630f6-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="630f6-110">[in] The name of the assembly to find.</span><span class="sxs-lookup"><span data-stu-id="630f6-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="630f6-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="630f6-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="630f6-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span><span class="sxs-lookup"><span data-stu-id="630f6-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="630f6-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="630f6-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="630f6-114">[out] The number of interface pointers returned.</span><span class="sxs-lookup"><span data-stu-id="630f6-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="630f6-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="630f6-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="630f6-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="630f6-116">Return Value</span></span>  
  
|<span data-ttu-id="630f6-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="630f6-117">HRESULT</span></span>|<span data-ttu-id="630f6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="630f6-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="630f6-119">`FindAssembliesByName` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="630f6-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="630f6-120">There are no assemblies.</span><span class="sxs-lookup"><span data-stu-id="630f6-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="630f6-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="630f6-121">Remarks</span></span>  
 <span data-ttu-id="630f6-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span><span class="sxs-lookup"><span data-stu-id="630f6-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="630f6-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span><span class="sxs-lookup"><span data-stu-id="630f6-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="630f6-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span><span class="sxs-lookup"><span data-stu-id="630f6-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="630f6-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="630f6-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="630f6-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span><span class="sxs-lookup"><span data-stu-id="630f6-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="630f6-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span><span class="sxs-lookup"><span data-stu-id="630f6-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="630f6-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span><span class="sxs-lookup"><span data-stu-id="630f6-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="630f6-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="630f6-129">Requirements</span></span>  
 <span data-ttu-id="630f6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="630f6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="630f6-131">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="630f6-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="630f6-132">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="630f6-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="630f6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="630f6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630f6-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="630f6-134">See also</span></span>

- [<span data-ttu-id="630f6-135">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="630f6-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="630f6-136">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="630f6-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
