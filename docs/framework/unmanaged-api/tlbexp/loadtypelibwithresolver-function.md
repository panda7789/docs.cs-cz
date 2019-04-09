---
title: LoadTypeLibWithResolver – funkce
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c14080e3ac128a6a7fbb48586f59d8a5ea4105f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155652"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="cc747-102">LoadTypeLibWithResolver – funkce</span><span class="sxs-lookup"><span data-stu-id="cc747-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="cc747-103">Načte knihovnu typů a použije zadané [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřešit jakékoli interně odkazované knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="cc747-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc747-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc747-104">Syntax</span></span>  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc747-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc747-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="cc747-106">[in] Cesta k souboru knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="cc747-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="cc747-107">[in] A [REGKIND výčet](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) příznak, který určuje způsob registrace knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="cc747-107">[in] A [REGKIND enumeration](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="cc747-108">Jeho možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="cc747-108">Its possible values are:</span></span>  
  
-   `REGKIND_DEFAULT`<span data-ttu-id="cc747-109">: Použije výchozí chování registrace.</span><span class="sxs-lookup"><span data-stu-id="cc747-109">: Use default registration behavior.</span></span>  
  
-   `REGKIND_REGISTER`<span data-ttu-id="cc747-110">: Zaregistrujte tuto knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="cc747-110">: Register this type library.</span></span>  
  
-   `REGKIND_NONE`<span data-ttu-id="cc747-111">: Neregistrujte tuto knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="cc747-111">: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="cc747-112">[in] Ukazatel na implementaci [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="cc747-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="cc747-113">[out] Odkaz na knihovnu typů, který se načítá.</span><span class="sxs-lookup"><span data-stu-id="cc747-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc747-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cc747-114">Return Value</span></span>  
 <span data-ttu-id="cc747-115">Jedna z hodnot HRESULT uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="cc747-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="cc747-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cc747-116">Return value</span></span>|<span data-ttu-id="cc747-117">Význam</span><span class="sxs-lookup"><span data-stu-id="cc747-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="cc747-118">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="cc747-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="cc747-119">Nedostatek paměti</span><span class="sxs-lookup"><span data-stu-id="cc747-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="cc747-120">Jeden nebo více ukazatelů jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="cc747-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="cc747-121">Jeden nebo více argumentů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="cc747-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="cc747-122">Funkce nemůže zapisovat do souboru.</span><span class="sxs-lookup"><span data-stu-id="cc747-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="cc747-123">Nelze otevřít systémové registrační databázi.</span><span class="sxs-lookup"><span data-stu-id="cc747-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="cc747-124">Knihovnu typů nelze otevřít.</span><span class="sxs-lookup"><span data-stu-id="cc747-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="cc747-125">Nelze načíst knihovnu typů nebo knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="cc747-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc747-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc747-126">Remarks</span></span>  
 <span data-ttu-id="cc747-127">[Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) volání `LoadTypeLibWithResolver` funkce během procesu převodu sestavení na typu knihovny.</span><span class="sxs-lookup"><span data-stu-id="cc747-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="cc747-128">Tato funkce načte zadanou knihovnu typů s minimální přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="cc747-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="cc747-129">Funkce zkontroluje knihovnu typů pro interně odkazované knihovny typů, z nichž každý musí být načten a přidány do knihovny nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="cc747-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="cc747-130">Předtím, než je možné načíst odkazovanou knihovnu typů, cesta k souboru jeho odkazu musí přeložit na úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="cc747-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="cc747-131">To lze provést prostřednictvím [resolvetypelib – metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) poskytnutou neregistrovaným [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), který je předán `pTlbResolver` parametru.</span><span class="sxs-lookup"><span data-stu-id="cc747-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="cc747-132">Pokud známý úplné cesty k souboru z odkazované knihovny typů `LoadTypeLibWithResolver` funkce načte a přidá do nadřazené knihovny typů, vytváření knihovny typů kombinované hlavní odkazované knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="cc747-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="cc747-133">Poté, co funkce odstraňuje a načte všechna interně odkazované knihovny typů, vrátí odkaz na hlavní rozpoznaný typ knihovny `pptlib` parametru.</span><span class="sxs-lookup"><span data-stu-id="cc747-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="cc747-134">`LoadTypeLibWithResolver` Funkce je obvykle volána [Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), který dodává své vlastní interní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace `pTlbResolver` parametr.</span><span class="sxs-lookup"><span data-stu-id="cc747-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="cc747-135">Při volání `LoadTypeLibWithResolver` přímo, je nutné zadat vlastní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace.</span><span class="sxs-lookup"><span data-stu-id="cc747-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc747-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc747-136">Requirements</span></span>  
 <span data-ttu-id="cc747-137">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc747-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc747-138">**Záhlaví:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="cc747-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="cc747-139">**Knihovna:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="cc747-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="cc747-140">**Verze rozhraní .NET framework:** 3.5, 3.0, 2.0</span><span class="sxs-lookup"><span data-stu-id="cc747-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc747-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc747-141">See also</span></span>

- [<span data-ttu-id="cc747-142">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="cc747-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="cc747-143">LoadTypeLibEx – funkce</span><span class="sxs-lookup"><span data-stu-id="cc747-143">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
