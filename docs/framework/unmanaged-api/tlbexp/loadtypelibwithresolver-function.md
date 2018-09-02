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
ms.openlocfilehash: b6a217e2212bb900d7ba83ccdd9cb00d30454baf
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403767"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="fe48f-102">LoadTypeLibWithResolver – funkce</span><span class="sxs-lookup"><span data-stu-id="fe48f-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="fe48f-103">Načte knihovnu typů a použije zadané [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřešit jakékoli interně odkazované knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fe48f-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe48f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe48f-104">Syntax</span></span>  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe48f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe48f-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="fe48f-106">[in] Cesta k souboru knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fe48f-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="fe48f-107">[in] A [REGKIND výčet](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) příznak, který určuje způsob registrace knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fe48f-107">[in] A [REGKIND enumeration](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="fe48f-108">Jeho možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="fe48f-108">Its possible values are:</span></span>  
  
-   <span data-ttu-id="fe48f-109">`REGKIND_DEFAULT`: Použije výchozí chování registrace.</span><span class="sxs-lookup"><span data-stu-id="fe48f-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
-   <span data-ttu-id="fe48f-110">`REGKIND_REGISTER`: Zaregistrujte tuto knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="fe48f-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
-   <span data-ttu-id="fe48f-111">`REGKIND_NONE`: Neregistrujte tuto knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="fe48f-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="fe48f-112">[in] Ukazatel na implementaci [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="fe48f-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="fe48f-113">[out] Odkaz na knihovnu typů, který se načítá.</span><span class="sxs-lookup"><span data-stu-id="fe48f-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe48f-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fe48f-114">Return Value</span></span>  
 <span data-ttu-id="fe48f-115">Jedna z hodnot HRESULT uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="fe48f-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="fe48f-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fe48f-116">Return value</span></span>|<span data-ttu-id="fe48f-117">Význam</span><span class="sxs-lookup"><span data-stu-id="fe48f-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="fe48f-118">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="fe48f-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="fe48f-119">Nedostatek paměti</span><span class="sxs-lookup"><span data-stu-id="fe48f-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="fe48f-120">Jeden nebo více ukazatelů jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="fe48f-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="fe48f-121">Jeden nebo více argumentů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="fe48f-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="fe48f-122">Funkce nemůže zapisovat do souboru.</span><span class="sxs-lookup"><span data-stu-id="fe48f-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="fe48f-123">Nelze otevřít systémové registrační databázi.</span><span class="sxs-lookup"><span data-stu-id="fe48f-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="fe48f-124">Knihovnu typů nelze otevřít.</span><span class="sxs-lookup"><span data-stu-id="fe48f-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="fe48f-125">Nelze načíst knihovnu typů nebo knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="fe48f-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe48f-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe48f-126">Remarks</span></span>  
 <span data-ttu-id="fe48f-127">[Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) volání `LoadTypeLibWithResolver` funkce během procesu převodu sestavení na typu knihovny.</span><span class="sxs-lookup"><span data-stu-id="fe48f-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="fe48f-128">Tato funkce načte zadanou knihovnu typů s minimální přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="fe48f-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="fe48f-129">Funkce zkontroluje knihovnu typů pro interně odkazované knihovny typů, z nichž každý musí být načten a přidány do knihovny nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="fe48f-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="fe48f-130">Předtím, než je možné načíst odkazovanou knihovnu typů, cesta k souboru jeho odkazu musí přeložit na úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="fe48f-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="fe48f-131">To lze provést prostřednictvím [resolvetypelib – metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) poskytnutou neregistrovaným [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), který je předán `pTlbResolver` parametru.</span><span class="sxs-lookup"><span data-stu-id="fe48f-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="fe48f-132">Pokud známý úplné cesty k souboru z odkazované knihovny typů `LoadTypeLibWithResolver` funkce načte a přidá do nadřazené knihovny typů, vytváření knihovny typů kombinované hlavní odkazované knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fe48f-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="fe48f-133">Poté, co funkce odstraňuje a načte všechna interně odkazované knihovny typů, vrátí odkaz na hlavní rozpoznaný typ knihovny `pptlib` parametru.</span><span class="sxs-lookup"><span data-stu-id="fe48f-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="fe48f-134">`LoadTypeLibWithResolver` Funkce je obvykle volána [Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), který dodává své vlastní interní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace `pTlbResolver` parametr.</span><span class="sxs-lookup"><span data-stu-id="fe48f-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="fe48f-135">Při volání `LoadTypeLibWithResolver` přímo, je nutné zadat vlastní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace.</span><span class="sxs-lookup"><span data-stu-id="fe48f-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe48f-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe48f-136">Requirements</span></span>  
 <span data-ttu-id="fe48f-137">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe48f-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe48f-138">**Záhlaví:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="fe48f-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="fe48f-139">**Knihovna:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="fe48f-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="fe48f-140">**Verze rozhraní .NET framework:** 3.5, 3.0, 2.0</span><span class="sxs-lookup"><span data-stu-id="fe48f-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe48f-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe48f-141">See Also</span></span>  
 [<span data-ttu-id="fe48f-142">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="fe48f-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [<span data-ttu-id="fe48f-143">LoadTypeLibEx – funkce</span><span class="sxs-lookup"><span data-stu-id="fe48f-143">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
