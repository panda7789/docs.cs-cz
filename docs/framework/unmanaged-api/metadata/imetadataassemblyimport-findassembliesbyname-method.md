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
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177804"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="2dad7-102">IMetaDataAssemblyImport::FindAssembliesByName – metoda</span><span class="sxs-lookup"><span data-stu-id="2dad7-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="2dad7-103">Získá pole sestavení se zadaným `szAssemblyName` parametrem pomocí standardních pravidel používaných cltime jazyka (CLR) pro řešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="2dad7-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dad7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2dad7-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2dad7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2dad7-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="2dad7-106">[v] Kořenový adresář, ve kterém chcete vyhledat dané sestavení.</span><span class="sxs-lookup"><span data-stu-id="2dad7-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="2dad7-107">Pokud je tato `null`hodnota `FindAssembliesByName` nastavena na , bude vypadat pouze v globální mezipaměti sestavení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="2dad7-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="2dad7-108">[v] Seznam podadresářů oddělených středníkem (například "bin;bin2") pod kořenovým adresářem, ve kterém lze vyhledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="2dad7-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="2dad7-109">Tyto adresáře jsou sondovány kromě těch, které jsou zadány ve výchozím pravidlech zjišťování.</span><span class="sxs-lookup"><span data-stu-id="2dad7-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="2dad7-110">[v] Název sestavení najít.</span><span class="sxs-lookup"><span data-stu-id="2dad7-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="2dad7-111">Formát tohoto řetězce je definován na stránce <xref:System.Reflection.AssemblyName>reference třídy pro .</span><span class="sxs-lookup"><span data-stu-id="2dad7-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="2dad7-112">[v] Pole typu [IUnknown,](/cpp/atl/iunknown) ve kterém `IMetadataAssemblyImport` chcete umístit ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2dad7-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2dad7-113">[out] Maximální počet ukazatelů rozhraní, které lze `ppIUnk`umístit do aplikace .</span><span class="sxs-lookup"><span data-stu-id="2dad7-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="2dad7-114">[out] Počet ukazatelů rozhraní vrácena.</span><span class="sxs-lookup"><span data-stu-id="2dad7-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="2dad7-115">To znamená, že počet ukazatelů rozhraní `ppIUnk`skutečně umístěn v .</span><span class="sxs-lookup"><span data-stu-id="2dad7-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2dad7-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2dad7-116">Return Value</span></span>  
  
|<span data-ttu-id="2dad7-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2dad7-117">HRESULT</span></span>|<span data-ttu-id="2dad7-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2dad7-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2dad7-119">`FindAssembliesByName`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2dad7-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2dad7-120">Neexistují žádná sestavení.</span><span class="sxs-lookup"><span data-stu-id="2dad7-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dad7-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2dad7-121">Remarks</span></span>  
 <span data-ttu-id="2dad7-122">Vzhledem k názvu `FindAssembliesByName` sestavení metoda najde sestavení podle standardních pravidel pro řešení odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="2dad7-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="2dad7-123">(Další informace naleznete [v tématu How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umožňuje volajícímu konfigurovat různé aspekty kontextu překládání sestavení, jako je například základna aplikace a soukromá vyhledávací cesta.</span><span class="sxs-lookup"><span data-stu-id="2dad7-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="2dad7-124">Metoda `FindAssembliesByName` vyžaduje CLR, které mají být inicializovány v procesu za účelem vyvolání logiky rozlišení sestavení.</span><span class="sxs-lookup"><span data-stu-id="2dad7-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="2dad7-125">Proto je nutné volat [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (předávání `FindAssembliesByName`COINITEE_DEFAULT) před voláním a potom postupujte s voláním [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="2dad7-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="2dad7-126">`FindAssembliesByName`vrátí ukazatel [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) do souboru obsahujícího manifest sestavení pro název sestavení, který je předán.</span><span class="sxs-lookup"><span data-stu-id="2dad7-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="2dad7-127">Pokud daný název sestavení není zcela zadán (například pokud neobsahuje verzi), může být vráceno více sestavení.</span><span class="sxs-lookup"><span data-stu-id="2dad7-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="2dad7-128">`FindAssembliesByName`je běžně používán kompilátorem, který se pokouší najít odkazované sestavení v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="2dad7-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dad7-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2dad7-129">Requirements</span></span>  
 <span data-ttu-id="2dad7-130">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dad7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dad7-131">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="2dad7-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2dad7-132">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2dad7-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2dad7-133">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dad7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dad7-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2dad7-134">See also</span></span>

- [<span data-ttu-id="2dad7-135">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="2dad7-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="2dad7-136">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2dad7-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
