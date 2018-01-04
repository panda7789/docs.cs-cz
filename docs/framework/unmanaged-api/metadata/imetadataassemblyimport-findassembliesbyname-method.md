---
title: "IMetaDataAssemblyImport::FindAssembliesByName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindAssembliesByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6518fdcf1bef8eaea74818f69f46bb6df26e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="883bb-102">IMetaDataAssemblyImport::FindAssembliesByName – metoda</span><span class="sxs-lookup"><span data-stu-id="883bb-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="883bb-103">Získá pole sestavení se zadaným `szAssemblyName` parametr pomocí standardní pravidla zaměstnaní modul CLR (CLR) pro řešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="883bb-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="883bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="883bb-104">Syntax</span></span>  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="883bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="883bb-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="883bb-106">[v] Kořenový adresář, do kterého chcete vyhledat zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="883bb-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="883bb-107">Pokud tato hodnota nastavena na `null`, `FindAssembliesByName` hledat pouze v globální mezipaměti sestavení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="883bb-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="883bb-108">[v] Seznam oddělený středníkem podadresáře (například "bin; přihrádka 2), v kořenovém adresáři, ve kterém se má hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="883bb-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="883bb-109">Tyto adresáře jsou zjištěný kromě platformám zadaným v výchozí pravidla zjišťování.</span><span class="sxs-lookup"><span data-stu-id="883bb-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="883bb-110">[v] Název sestavení najít.</span><span class="sxs-lookup"><span data-stu-id="883bb-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="883bb-111">Formát tohoto řetězce je definována v stránce referenční třídy <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="883bb-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="883bb-112">[v] Pole typu <<!--zzxref:IUnknown --> `IUnknown`> ve které se umístí `IMetadataAssemblyImport` rozhraní ukazatele.</span><span class="sxs-lookup"><span data-stu-id="883bb-112">[in] An array of type <<!--zzxref:IUnknown --> `IUnknown`> in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="883bb-113">[out] Maximální počet ukazatele rozhraní, které mohou být umístěny v `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="883bb-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="883bb-114">[out] Vrátí počet ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="883bb-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="883bb-115">To znamená, počet ukazatele rozhraní ve skutečnosti umístěných v `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="883bb-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="883bb-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="883bb-116">Return Value</span></span>  
  
|<span data-ttu-id="883bb-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="883bb-117">HRESULT</span></span>|<span data-ttu-id="883bb-118">Popis</span><span class="sxs-lookup"><span data-stu-id="883bb-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="883bb-119">`FindAssembliesByName`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="883bb-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="883bb-120">Neexistují žádné sestavení.</span><span class="sxs-lookup"><span data-stu-id="883bb-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="883bb-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="883bb-121">Remarks</span></span>  
 <span data-ttu-id="883bb-122">Název sestavení, `FindAssembliesByName` metoda vyhledá sestavení pomocí následujících standardní pravidla pro řešení odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="883bb-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="883bb-123">(Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umožňuje volajícímu nakonfigurovat různé aspekty kontextu překladač sestavení, jako je například cesta k aplikaci základní a privátní vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="883bb-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="883bb-124">`FindAssembliesByName` Metoda vyžaduje CLR na inicializaci v procesu k vyvolání logice sestavení řešení.</span><span class="sxs-lookup"><span data-stu-id="883bb-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="883bb-125">Proto musí volat [coinitializeee –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (předávání COINITEE_DEFAULT) před voláním `FindAssembliesByName`a pak postupujte podle pomocí volání [couninitializecor –](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="883bb-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="883bb-126">`FindAssembliesByName`Vrátí [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) ukazatele souboru, který obsahuje manifest sestavení pro název sestavení, který se předává v.</span><span class="sxs-lookup"><span data-stu-id="883bb-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="883bb-127">Pokud název zadaného sestavení není plně určena (například pokud neobsahuje verze), může být vrácena více sestavení.</span><span class="sxs-lookup"><span data-stu-id="883bb-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="883bb-128">`FindAssembliesByName`běžně používá kompilátoru, která se pokusí najít odkazované sestavení při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="883bb-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="883bb-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="883bb-129">Requirements</span></span>  
 <span data-ttu-id="883bb-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="883bb-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="883bb-131">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="883bb-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="883bb-132">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="883bb-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="883bb-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="883bb-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="883bb-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="883bb-134">See Also</span></span>  
 [<span data-ttu-id="883bb-135">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="883bb-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="883bb-136">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="883bb-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
