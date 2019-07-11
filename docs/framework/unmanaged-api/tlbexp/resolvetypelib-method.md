---
title: ResolveTypeLib – metoda
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b6db8925fb966f4a8b2a213b0d6e340d0edf107
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756425"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="476db-102">ResolveTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="476db-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="476db-103">Přeloží jednoduchý název knihovny typů tak, že vrací jeho úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="476db-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="476db-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="476db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="476db-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="476db-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje jednoduchý název knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="476db-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="476db-107">[in] Identifikátor GUID přiřazený do knihovny typů v registru.</span><span class="sxs-lookup"><span data-stu-id="476db-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="476db-108">[in] ID lokalizace knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="476db-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="476db-109">[in] Číslo hlavní verze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="476db-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="476db-110">Například pro verzi *x.y*, je číslo hlavní verze *x*.</span><span class="sxs-lookup"><span data-stu-id="476db-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="476db-111">[in] Číslo podverze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="476db-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="476db-112">Například pro verzi *x.y*, je číslo podverze *y*.</span><span class="sxs-lookup"><span data-stu-id="476db-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="476db-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) příznak, který identifikuje provozní prostředí.</span><span class="sxs-lookup"><span data-stu-id="476db-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="476db-114">Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="476db-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="476db-115">[out] Ukazatel [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) obsahující úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="476db-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="476db-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="476db-116">Remarks</span></span>  
 <span data-ttu-id="476db-117">`ResolveTypeLib` Metoda je volána [loadtypelibwithresolver – funkce](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) během [Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) zpracování.</span><span class="sxs-lookup"><span data-stu-id="476db-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="476db-118">Vlastní implementace tohoto rozhraní musí vrátit [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) obsahující úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="476db-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="476db-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="476db-119">Requirements</span></span>  
 <span data-ttu-id="476db-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="476db-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="476db-121">**Záhlaví:** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="476db-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="476db-122">**Knihovna:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="476db-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="476db-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="476db-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476db-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="476db-124">See also</span></span>

- [<span data-ttu-id="476db-125">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="476db-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="476db-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="476db-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
