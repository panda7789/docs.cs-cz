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
ms.openlocfilehash: 51d7cd273aa7a8799a1aac90d828ec81a7670906
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603270"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="f084d-102">LoadTypeLibWithResolver – funkce</span><span class="sxs-lookup"><span data-stu-id="f084d-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="f084d-103">Načte knihovnu typů a použije zadané [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřešit jakékoli interně odkazované knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="f084d-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f084d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f084d-104">Syntax</span></span>  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f084d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f084d-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="f084d-106">[in] Cesta k souboru knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="f084d-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="f084d-107">[in] A [REGKIND výčet](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) příznak, který určuje způsob registrace knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="f084d-107">[in] A [REGKIND enumeration](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="f084d-108">Jeho možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="f084d-108">Its possible values are:</span></span>  
  
- <span data-ttu-id="f084d-109">`REGKIND_DEFAULT`: Použije výchozí chování registrace.</span><span class="sxs-lookup"><span data-stu-id="f084d-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="f084d-110">`REGKIND_REGISTER`: Zaregistrujte tuto knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="f084d-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="f084d-111">`REGKIND_NONE`: Neregistrujte tuto knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="f084d-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="f084d-112">[in] Ukazatel na implementaci [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f084d-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="f084d-113">[out] Odkaz na knihovnu typů, který se načítá.</span><span class="sxs-lookup"><span data-stu-id="f084d-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f084d-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f084d-114">Return Value</span></span>  
 <span data-ttu-id="f084d-115">Jedna z hodnot HRESULT uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f084d-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="f084d-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f084d-116">Return value</span></span>|<span data-ttu-id="f084d-117">Význam</span><span class="sxs-lookup"><span data-stu-id="f084d-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="f084d-118">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="f084d-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="f084d-119">Nedostatek paměti</span><span class="sxs-lookup"><span data-stu-id="f084d-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="f084d-120">Jeden nebo více ukazatelů jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="f084d-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="f084d-121">Jeden nebo více argumentů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="f084d-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="f084d-122">Funkce nemůže zapisovat do souboru.</span><span class="sxs-lookup"><span data-stu-id="f084d-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="f084d-123">Nelze otevřít systémové registrační databázi.</span><span class="sxs-lookup"><span data-stu-id="f084d-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="f084d-124">Knihovnu typů nelze otevřít.</span><span class="sxs-lookup"><span data-stu-id="f084d-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="f084d-125">Nelze načíst knihovnu typů nebo knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="f084d-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f084d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f084d-126">Remarks</span></span>  
 <span data-ttu-id="f084d-127">[Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) volání `LoadTypeLibWithResolver` funkce během procesu převodu sestavení na typu knihovny.</span><span class="sxs-lookup"><span data-stu-id="f084d-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="f084d-128">Tato funkce načte zadanou knihovnu typů s minimální přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="f084d-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="f084d-129">Funkce zkontroluje knihovnu typů pro interně odkazované knihovny typů, z nichž každý musí být načten a přidány do knihovny nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="f084d-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="f084d-130">Předtím, než je možné načíst odkazovanou knihovnu typů, cesta k souboru jeho odkazu musí přeložit na úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="f084d-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="f084d-131">To lze provést prostřednictvím [resolvetypelib – metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) poskytnutou neregistrovaným [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), který je předán `pTlbResolver` parametru.</span><span class="sxs-lookup"><span data-stu-id="f084d-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="f084d-132">Pokud známý úplné cesty k souboru z odkazované knihovny typů `LoadTypeLibWithResolver` funkce načte a přidá do nadřazené knihovny typů, vytváření knihovny typů kombinované hlavní odkazované knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="f084d-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="f084d-133">Poté, co funkce odstraňuje a načte všechna interně odkazované knihovny typů, vrátí odkaz na hlavní rozpoznaný typ knihovny `pptlib` parametru.</span><span class="sxs-lookup"><span data-stu-id="f084d-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="f084d-134">`LoadTypeLibWithResolver` Funkce je obvykle volána [Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), který dodává své vlastní interní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace `pTlbResolver` parametr.</span><span class="sxs-lookup"><span data-stu-id="f084d-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="f084d-135">Při volání `LoadTypeLibWithResolver` přímo, je nutné zadat vlastní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace.</span><span class="sxs-lookup"><span data-stu-id="f084d-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f084d-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f084d-136">Requirements</span></span>  
 <span data-ttu-id="f084d-137">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f084d-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f084d-138">**Záhlaví:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="f084d-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="f084d-139">**Knihovna:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="f084d-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="f084d-140">**Verze rozhraní .NET framework:** 3.5, 3.0, 2.0</span><span class="sxs-lookup"><span data-stu-id="f084d-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f084d-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f084d-141">See also</span></span>

- [<span data-ttu-id="f084d-142">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="f084d-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="f084d-143">LoadTypeLibEx – funkce</span><span class="sxs-lookup"><span data-stu-id="f084d-143">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
