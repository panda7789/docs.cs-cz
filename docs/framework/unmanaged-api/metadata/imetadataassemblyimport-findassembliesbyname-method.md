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
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="ef459-102">IMetaDataAssemblyImport::FindAssembliesByName – metoda</span><span class="sxs-lookup"><span data-stu-id="ef459-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="ef459-103">Získá pole sestavení se zadaným parametrem `szAssemblyName` pomocí standardních pravidel používaných modulem CLR (Common Language Runtime) pro překlad odkazů.</span><span class="sxs-lookup"><span data-stu-id="ef459-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef459-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef459-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ef459-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef459-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="ef459-106">pro Kořenový adresář, ve kterém se má vyhledat dané sestavení</span><span class="sxs-lookup"><span data-stu-id="ef459-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="ef459-107">Pokud je tato hodnota nastavena na `null`, `FindAssembliesByName` bude hledána pouze v globální mezipaměti sestavení (GAC) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef459-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="ef459-108">pro Seznam podadresářů oddělených středníkem (například "bin; BIN2") v kořenovém adresáři, ve kterém chcete vyhledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef459-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="ef459-109">Kromě těch, které jsou zadány ve výchozích pravidlech zjišťování, jsou tyto adresáře zjišťovány.</span><span class="sxs-lookup"><span data-stu-id="ef459-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="ef459-110">pro Název sestavení, které chcete najít.</span><span class="sxs-lookup"><span data-stu-id="ef459-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="ef459-111">Formát tohoto řetězce je definován na stránce Reference třídy pro <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="ef459-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="ef459-112">pro Pole typu [IUnknown](/cpp/atl/iunknown) , do kterého chcete umístit ukazatele rozhraní `IMetadataAssemblyImport`.</span><span class="sxs-lookup"><span data-stu-id="ef459-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ef459-113">mimo Maximální počet ukazatelů rozhraní, které lze umístit do `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="ef459-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="ef459-114">mimo Počet vrácených ukazatelů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ef459-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="ef459-115">To znamená, že počet ukazatelů rozhraní skutečně umístěných v `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="ef459-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef459-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ef459-116">Return Value</span></span>  
  
|<span data-ttu-id="ef459-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef459-117">HRESULT</span></span>|<span data-ttu-id="ef459-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ef459-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ef459-119">`FindAssembliesByName` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ef459-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ef459-120">Neexistují žádná sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef459-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef459-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef459-121">Remarks</span></span>  
 <span data-ttu-id="ef459-122">V případě názvu sestavení vyhledá `FindAssembliesByName` metoda sestavení pomocí standardních pravidel pro překládání odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef459-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="ef459-123">(Další informace naleznete v tématu [jak modul runtime vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umožňuje volající konfiguraci různých aspektů kontextu překladače sestavení, jako je například základ aplikace a cesta k privátnímu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="ef459-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="ef459-124">Metoda `FindAssembliesByName` vyžaduje, aby byl modul CLR inicializován v procesu, aby bylo možné vyvolat logiku rozlišení sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef459-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="ef459-125">Proto je nutné před voláním `FindAssembliesByName`volat [CoInitializeEE –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (předávání COINITEE_DEFAULT) a pak sledovat volání [CoUninitializeCor –](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="ef459-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="ef459-126">`FindAssembliesByName` vrátí ukazatel [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) do souboru obsahujícího manifest sestavení pro název sestavení, který je předaný.</span><span class="sxs-lookup"><span data-stu-id="ef459-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="ef459-127">Pokud zadaný název sestavení není plně zadán (například pokud nezahrnuje verzi), může být vráceno více sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef459-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="ef459-128">`FindAssembliesByName` se běžně používá kompilátorem, který se pokouší najít odkazované sestavení v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="ef459-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef459-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef459-129">Requirements</span></span>  
 <span data-ttu-id="ef459-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef459-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef459-131">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ef459-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef459-132">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="ef459-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef459-133">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef459-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef459-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef459-134">See also</span></span>

- [<span data-ttu-id="ef459-135">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="ef459-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ef459-136">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef459-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
