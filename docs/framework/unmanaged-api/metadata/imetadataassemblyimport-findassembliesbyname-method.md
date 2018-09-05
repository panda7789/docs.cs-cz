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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9babd5e50166be2c2d1b7bc32a5fc11d1ad8ba9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723474"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="98560-102">IMetaDataAssemblyImport::FindAssembliesByName – metoda</span><span class="sxs-lookup"><span data-stu-id="98560-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="98560-103">Získává pole sestavení se zadaným `szAssemblyName` parametr pomocí standardních pravidel použijí modulem common language runtime (CLR) k vyřešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="98560-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98560-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98560-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="98560-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98560-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="98560-106">[in] Kořenový adresář, do kterého chcete vyhledat dané sestavení.</span><span class="sxs-lookup"><span data-stu-id="98560-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="98560-107">Pokud tato hodnota nastavená na `null`, `FindAssembliesByName` bude vypadat pouze v globální mezipaměti sestavení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="98560-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="98560-108">[in] Seznam oddělený středníkem podadresáře (například "bin; bin2"), v kořenovém adresáři, ve kterém chcete hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="98560-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="98560-109">Tyto adresáře jsou vystavovány kromě platformám zadaným v výchozí pravidla zjišťování.</span><span class="sxs-lookup"><span data-stu-id="98560-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="98560-110">[in] Název sestavení k vyhledání.</span><span class="sxs-lookup"><span data-stu-id="98560-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="98560-111">Formát tohoto řetězce je definována na referenční stránce třídy pro <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="98560-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="98560-112">[in] Pole typu [IUnknown](/cpp/atl/iunknown) ve které chcete umístit `IMetadataAssemblyImport` ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="98560-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="98560-113">[out] Maximální počet ukazatele rozhraní, které mohou být umístěny v `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="98560-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="98560-114">[out] Číslo vrácen ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="98560-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="98560-115">To znamená, počet ukazatelů rozhraní skutečně umístit v `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="98560-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98560-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="98560-116">Return Value</span></span>  
  
|<span data-ttu-id="98560-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98560-117">HRESULT</span></span>|<span data-ttu-id="98560-118">Popis</span><span class="sxs-lookup"><span data-stu-id="98560-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="98560-119">`FindAssembliesByName` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="98560-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="98560-120">Neexistují žádná sestavení.</span><span class="sxs-lookup"><span data-stu-id="98560-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98560-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98560-121">Remarks</span></span>  
 <span data-ttu-id="98560-122">Název sestavení, `FindAssembliesByName` metoda vyhledá sestavení pomocí následujících standardní pravidla pro překlad odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="98560-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="98560-123">(Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umožňuje volajícímu nakonfigurovat různé aspekty kontextu překladač sestavení, jako je například základní a privátní vyhledávací cestu aplikace.</span><span class="sxs-lookup"><span data-stu-id="98560-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="98560-124">`FindAssembliesByName` Metoda vyžaduje CLR v procesu inicializovat, aby bylo možné vyvolávajícími logiku sestavení řešení.</span><span class="sxs-lookup"><span data-stu-id="98560-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="98560-125">Proto je nutné volat [coinitializeee –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (předávání COINITEE_DEFAULT) před voláním `FindAssembliesByName`a pak postupujte podle voláním [couninitializecor –](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="98560-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="98560-126">`FindAssembliesByName` Vrátí [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) ukazatel na soubor obsahující manifest sestavení pro název sestavení, které je předáno.</span><span class="sxs-lookup"><span data-stu-id="98560-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="98560-127">Pokud daný název sestavení není zadán úplně (například, pokud neobsahuje verzi), může být vrácena více sestavení.</span><span class="sxs-lookup"><span data-stu-id="98560-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="98560-128">`FindAssembliesByName` běžně používá kompilátor, který se pokusí najít odkazované sestavení v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="98560-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98560-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98560-129">Requirements</span></span>  
 <span data-ttu-id="98560-130">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98560-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98560-131">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="98560-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98560-132">**Knihovna:** použit jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98560-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98560-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98560-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98560-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="98560-134">See Also</span></span>  
 [<span data-ttu-id="98560-135">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="98560-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="98560-136">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98560-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
