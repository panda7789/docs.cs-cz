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
ms.openlocfilehash: 751794746e26bd8f0ec2cd6db2f62876e78674e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460272"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="676bd-102">LoadTypeLibWithResolver – funkce</span><span class="sxs-lookup"><span data-stu-id="676bd-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="676bd-103">Načte knihovny typů a používá zadaných [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřešit všechny knihovny interně odkazovaného typu.</span><span class="sxs-lookup"><span data-stu-id="676bd-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="676bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="676bd-104">Syntax</span></span>  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="676bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="676bd-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="676bd-106">[v] Cesta k souboru knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="676bd-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="676bd-107">[v] A [REGKIND výčtu](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) příznak, který řídí, jak zaregistrovat knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="676bd-107">[in] A [REGKIND enumeration](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) flag that controls how the type library is registered.</span></span> <span data-ttu-id="676bd-108">Jeho možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="676bd-108">Its possible values are:</span></span>  
  
-   <span data-ttu-id="676bd-109">`REGKIND_DEFAULT`: Použijte výchozí chování registrace.</span><span class="sxs-lookup"><span data-stu-id="676bd-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
-   <span data-ttu-id="676bd-110">`REGKIND_REGISTER`: Zaregistrujte tuto knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="676bd-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
-   <span data-ttu-id="676bd-111">`REGKIND_NONE`: Neregistrovat toto knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="676bd-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="676bd-112">[v] Ukazatel na implementaci [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="676bd-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="676bd-113">[out] Odkaz na knihovnu typů, který je právě načítán.</span><span class="sxs-lookup"><span data-stu-id="676bd-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="676bd-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="676bd-114">Return Value</span></span>  
 <span data-ttu-id="676bd-115">Jedna z hodnot HRESULT uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="676bd-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="676bd-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="676bd-116">Return value</span></span>|<span data-ttu-id="676bd-117">Význam</span><span class="sxs-lookup"><span data-stu-id="676bd-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="676bd-118">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="676bd-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="676bd-119">Nedostatek paměti</span><span class="sxs-lookup"><span data-stu-id="676bd-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="676bd-120">Jeden nebo více následující ukazatele jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="676bd-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="676bd-121">Jeden nebo více parametrů jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="676bd-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="676bd-122">Funkci nelze zapisovat do souboru.</span><span class="sxs-lookup"><span data-stu-id="676bd-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="676bd-123">Registrační databáze systému nelze otevřít.</span><span class="sxs-lookup"><span data-stu-id="676bd-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="676bd-124">Knihovny typů nelze otevřít.</span><span class="sxs-lookup"><span data-stu-id="676bd-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="676bd-125">Nelze načíst knihovny typů nebo DLL.</span><span class="sxs-lookup"><span data-stu-id="676bd-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="676bd-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="676bd-126">Remarks</span></span>  
 <span data-ttu-id="676bd-127">[Tlbexp.exe (Exportér knihovny)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) volání `LoadTypeLibWithResolver` funkce během procesu převodu sestavení na typu knihovny.</span><span class="sxs-lookup"><span data-stu-id="676bd-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="676bd-128">Tato funkce načte knihovnu zadaného typu s minimální přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="676bd-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="676bd-129">Funkce zkontroluje knihovnu typů pro interně odkazovaného typu knihovny, každý z nich musí být načteny a přidány do knihovny nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="676bd-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="676bd-130">Předtím, než můžete načíst knihovnu odkazovaného typu, musí být vyřešeny jeho cesta k souboru odkaz na úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="676bd-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="676bd-131">To se provádí prostřednictvím [resolvetypelib – metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) který zajišťuje [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), který se předává v `pTlbResolver` parametr.</span><span class="sxs-lookup"><span data-stu-id="676bd-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="676bd-132">Pokud je úplná cesta odkazovaného typu knihovny se označuje, `LoadTypeLibWithResolver` funkce načte a přidá odkazovaného typu knihovny do knihovny typů nadřazenou, vytvoření knihovny kombinované hlavní typu.</span><span class="sxs-lookup"><span data-stu-id="676bd-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="676bd-133">Po funkce přeloží a načte všechny knihovny interně odkazovaného typu, vrátí odkaz na knihovnu hlavní přeložit typ v `pptlib` parametr.</span><span class="sxs-lookup"><span data-stu-id="676bd-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="676bd-134">`LoadTypeLibWithResolver` Funkce obecně volá [Tlbexp.exe (Exportér knihovny)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), které poskytuje vlastní interní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace v `pTlbResolver` parametr.</span><span class="sxs-lookup"><span data-stu-id="676bd-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="676bd-135">Když zavoláte `LoadTypeLibWithResolver` přímo, je nutné zadat vlastní [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementace.</span><span class="sxs-lookup"><span data-stu-id="676bd-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="676bd-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="676bd-136">Requirements</span></span>  
 <span data-ttu-id="676bd-137">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="676bd-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="676bd-138">**Záhlaví:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="676bd-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="676bd-139">**Knihovna:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="676bd-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="676bd-140">**Verze rozhraní .NET framework:** 3.5, 2.0 a 3.0</span><span class="sxs-lookup"><span data-stu-id="676bd-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="676bd-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="676bd-141">See Also</span></span>  
 [<span data-ttu-id="676bd-142">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="676bd-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="676bd-143">[LoadTypeLibEx – funkce](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="676bd-143">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span></span>
