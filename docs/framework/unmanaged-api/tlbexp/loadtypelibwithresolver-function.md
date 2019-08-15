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
ms.openlocfilehash: 6b9bec757071a98e085ccdeee3fc66bfc07f52bc
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040168"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="b4a55-102">LoadTypeLibWithResolver – funkce</span><span class="sxs-lookup"><span data-stu-id="b4a55-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="b4a55-103">Načte knihovnu typů a pomocí dodaného [rozhraní ITypeLibResolver –](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřeší všechny interně odkazované knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="b4a55-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4a55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4a55-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4a55-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4a55-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="b4a55-106">pro Cesta k souboru knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="b4a55-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="b4a55-107">pro Příznak [výčtu REGKIND](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind) , který určuje, jak je knihovna typů registrována.</span><span class="sxs-lookup"><span data-stu-id="b4a55-107">[in] A [REGKIND enumeration](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="b4a55-108">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="b4a55-108">Its possible values are:</span></span>  
  
- <span data-ttu-id="b4a55-109">`REGKIND_DEFAULT`: Použijte výchozí chování registrace.</span><span class="sxs-lookup"><span data-stu-id="b4a55-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="b4a55-110">`REGKIND_REGISTER`: Zaregistrujte tuto knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="b4a55-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="b4a55-111">`REGKIND_NONE`: Tuto knihovnu typů neregistrujte.</span><span class="sxs-lookup"><span data-stu-id="b4a55-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="b4a55-112">pro Ukazatel na implementaci [rozhraní ITypeLibResolver –](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b4a55-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="b4a55-113">mimo Odkaz na knihovnu typů, která je načítána.</span><span class="sxs-lookup"><span data-stu-id="b4a55-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4a55-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b4a55-114">Return Value</span></span>  
 <span data-ttu-id="b4a55-115">Jedna z hodnot HRESULT, které jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b4a55-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="b4a55-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b4a55-116">Return value</span></span>|<span data-ttu-id="b4a55-117">Význam</span><span class="sxs-lookup"><span data-stu-id="b4a55-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="b4a55-118">Nástup.</span><span class="sxs-lookup"><span data-stu-id="b4a55-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="b4a55-119">Nedostatek paměti</span><span class="sxs-lookup"><span data-stu-id="b4a55-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="b4a55-120">Jeden nebo více ukazatelů je neplatných.</span><span class="sxs-lookup"><span data-stu-id="b4a55-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="b4a55-121">Jeden nebo více argumentů je neplatných.</span><span class="sxs-lookup"><span data-stu-id="b4a55-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="b4a55-122">Funkce nemohla zapisovat do souboru.</span><span class="sxs-lookup"><span data-stu-id="b4a55-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="b4a55-123">Registrační databázi systému nelze otevřít.</span><span class="sxs-lookup"><span data-stu-id="b4a55-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="b4a55-124">Knihovnu typů nelze otevřít.</span><span class="sxs-lookup"><span data-stu-id="b4a55-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="b4a55-125">Knihovnu typů nebo knihovnu DLL nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="b4a55-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4a55-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4a55-126">Remarks</span></span>  
 <span data-ttu-id="b4a55-127">[Tlbexp. exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) volá `LoadTypeLibWithResolver` funkci během procesu převodu sestavení na typ knihovny.</span><span class="sxs-lookup"><span data-stu-id="b4a55-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="b4a55-128">Tato funkce načte zadanou knihovnu typů s minimálním přístupem k registru.</span><span class="sxs-lookup"><span data-stu-id="b4a55-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="b4a55-129">Funkce pak prověřuje knihovnu typů pro interně odkazované knihovny typů, z nichž každá musí být načtena a přidána do knihovny nadřazené typu.</span><span class="sxs-lookup"><span data-stu-id="b4a55-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="b4a55-130">Předtím, než může být načtena odkazovaná knihovna typů, musí být cesta k referenčnímu souboru přeložena na úplnou cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="b4a55-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="b4a55-131">To je provedeno prostřednictvím [metody ResolveTypeLib –](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) , která je poskytována [rozhraním ITypeLibResolver –](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), které je `pTlbResolver` předáno v parametru.</span><span class="sxs-lookup"><span data-stu-id="b4a55-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="b4a55-132">Je-li známa úplná cesta k souboru odkazované knihovny typů, `LoadTypeLibWithResolver` funkce načte a přidá odkazovanou knihovnu typů do nadřazené knihovny typů a vytvoří kombinovanou hlavní knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="b4a55-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="b4a55-133">Poté, co funkce vyřeší a načte všechny interně odkazované knihovny typů, vrátí odkaz na hlavní přeloženou knihovnu typů v `pptlib` parametru.</span><span class="sxs-lookup"><span data-stu-id="b4a55-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="b4a55-134">Funkce je obecně volána nástrojem [Tlbexp. exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), který poskytuje svou vlastní interní implementaci `pTlbResolver` [rozhraní ITypeLibResolver –](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) v parametru. `LoadTypeLibWithResolver`</span><span class="sxs-lookup"><span data-stu-id="b4a55-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="b4a55-135">Pokud voláte `LoadTypeLibWithResolver` přímo, musíte dodat vlastní implementaci [rozhraní ITypeLibResolver –](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b4a55-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4a55-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4a55-136">Requirements</span></span>  
 <span data-ttu-id="b4a55-137">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4a55-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4a55-138">**Hlaviček** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="b4a55-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="b4a55-139">**Knihovna** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="b4a55-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="b4a55-140">**Verze .NET Framework:** 3,5, 3,0, 2,0</span><span class="sxs-lookup"><span data-stu-id="b4a55-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4a55-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4a55-141">See also</span></span>

- [<span data-ttu-id="b4a55-142">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="b4a55-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="b4a55-143">LoadTypeLibEx – funkce</span><span class="sxs-lookup"><span data-stu-id="b4a55-143">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
