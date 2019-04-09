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
ms.openlocfilehash: d734f35b5878ec39e4f2159c326283d168e3be2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197890"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="3dbfb-102">ResolveTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="3dbfb-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="3dbfb-103">Přeloží jednoduchý název knihovny typů tak, že vrací jeho úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dbfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dbfb-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dbfb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dbfb-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="3dbfb-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje jednoduchý název knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="3dbfb-107">[in] Identifikátor GUID přiřazený do knihovny typů v registru.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="3dbfb-108">[in] ID lokalizace knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="3dbfb-109">[in] Číslo hlavní verze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="3dbfb-110">Například pro verzi *x.y*, je číslo hlavní verze *x*.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="3dbfb-111">[in] Číslo podverze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="3dbfb-112">Například pro verzi *x.y*, je číslo podverze *y*.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="3dbfb-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) příznak, který identifikuje provozní prostředí.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="3dbfb-114">Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="3dbfb-115">[out] Ukazatel [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) obsahující úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dbfb-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3dbfb-116">Remarks</span></span>  
 <span data-ttu-id="3dbfb-117">`ResolveTypeLib` Metoda je volána [loadtypelibwithresolver – funkce](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) během [Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) zpracování.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="3dbfb-118">Vlastní implementace tohoto rozhraní musí vrátit [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) obsahující úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="3dbfb-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dbfb-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3dbfb-119">Requirements</span></span>  
 <span data-ttu-id="3dbfb-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dbfb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dbfb-121">**Záhlaví:** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="3dbfb-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="3dbfb-122">**Knihovna:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="3dbfb-122">**Library:** TlbRef.lib</span></span>  
  
 **<span data-ttu-id="3dbfb-123">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3dbfb-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3dbfb-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3dbfb-124">See also</span></span>

- [<span data-ttu-id="3dbfb-125">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="3dbfb-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="3dbfb-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="3dbfb-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
