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
ms.openlocfilehash: 05902436c09d082f90af01f48c7e918650317ce7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009415"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="6cbc8-102">IMetaDataAssemblyImport::FindAssembliesByName – metoda</span><span class="sxs-lookup"><span data-stu-id="6cbc8-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="6cbc8-103">Získá pole sestavení se zadaným `szAssemblyName` parametrem pomocí standardních pravidel používaných modulem CLR (Common Language Runtime) pro překlad odkazů.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cbc8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cbc8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6cbc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cbc8-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="6cbc8-106">pro Kořenový adresář, ve kterém se má vyhledat dané sestavení</span><span class="sxs-lookup"><span data-stu-id="6cbc8-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="6cbc8-107">Pokud je tato hodnota nastavena na `null` , `FindAssembliesByName` bude hledána pouze v globální mezipaměti sestavení (GAC) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="6cbc8-108">pro Seznam podadresářů oddělených středníkem (například "bin; BIN2") v kořenovém adresáři, ve kterém chcete vyhledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="6cbc8-109">Kromě těch, které jsou zadány ve výchozích pravidlech zjišťování, jsou tyto adresáře zjišťovány.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="6cbc8-110">pro Název sestavení, které chcete najít.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="6cbc8-111">Formát tohoto řetězce je definován na stránce Reference třídy pro <xref:System.Reflection.AssemblyName> .</span><span class="sxs-lookup"><span data-stu-id="6cbc8-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="6cbc8-112">pro Pole typu [IUnknown](/cpp/atl/iunknown) , do kterého se mají umístit `IMetadataAssemblyImport` ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6cbc8-113">mimo Maximální počet ukazatelů rozhraní, které lze umístit do `ppIUnk` .</span><span class="sxs-lookup"><span data-stu-id="6cbc8-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="6cbc8-114">mimo Počet vrácených ukazatelů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="6cbc8-115">To znamená, že počet ukazatelů rozhraní, které jsou ve skutečnosti umístěny v `ppIUnk` .</span><span class="sxs-lookup"><span data-stu-id="6cbc8-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cbc8-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6cbc8-116">Return Value</span></span>  
  
|<span data-ttu-id="6cbc8-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6cbc8-117">HRESULT</span></span>|<span data-ttu-id="6cbc8-118">Description</span><span class="sxs-lookup"><span data-stu-id="6cbc8-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6cbc8-119">`FindAssembliesByName`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6cbc8-120">Neexistují žádná sestavení.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cbc8-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cbc8-121">Remarks</span></span>  
 <span data-ttu-id="6cbc8-122">V případě názvu sestavení `FindAssembliesByName` vyhledá metoda sestavení pomocí standardních pravidel pro překlad odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="6cbc8-123">(Další informace naleznete v tématu [jak modul runtime vyhledává sestavení](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName`umožňuje volající konfiguraci různých aspektů kontextu překladače sestavení, jako je například základ aplikace a cesta k privátnímu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-123">(For more information, see [How the Runtime Locates Assemblies](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="6cbc8-124">`FindAssembliesByName`Metoda vyžaduje, aby byl modul CLR inicializován v procesu, aby bylo možné vyvolat logiku rozlišení sestavení.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="6cbc8-125">Proto je nutné před voláním volat [CoInitializeEE –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (předání COINITEE_DEFAULT) `FindAssembliesByName` a pak sledovat volání [CoUninitializeCor –](../hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="6cbc8-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="6cbc8-126">`FindAssembliesByName`vrátí ukazatel [IMetaDataImport](imetadataimport-interface.md) na soubor obsahující manifest sestavení pro název sestavení, který je předaný.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-126">`FindAssembliesByName` returns an [IMetaDataImport](imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="6cbc8-127">Pokud zadaný název sestavení není plně zadán (například pokud nezahrnuje verzi), může být vráceno více sestavení.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="6cbc8-128">`FindAssembliesByName`je běžně používán kompilátorem, který se pokouší najít odkazované sestavení v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cbc8-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cbc8-129">Requirements</span></span>  
 <span data-ttu-id="6cbc8-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cbc8-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cbc8-131">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6cbc8-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6cbc8-132">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6cbc8-133">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cbc8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cbc8-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cbc8-134">See also</span></span>

- [<span data-ttu-id="6cbc8-135">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="6cbc8-135">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6cbc8-136">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cbc8-136">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
