---
title: "ResolveTypeLib – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ResolveTypeLib
api_location: tlbref.dll
f1_keywords: ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b430b050117243ced9d764045075071278841da2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="b50f5-102">ResolveTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="b50f5-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="b50f5-103">Přeloží jednoduchý název knihovny typů vrácením jeho plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="b50f5-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b50f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b50f5-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b50f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b50f5-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="b50f5-106">[v] A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) obsahující jednoduchý název knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="b50f5-106">[in] A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="b50f5-107">[v] Identifikátor GUID přiřazený knihovny typů v registru.</span><span class="sxs-lookup"><span data-stu-id="b50f5-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="b50f5-108">[v] Lokalizace ID knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="b50f5-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="b50f5-109">[v] Hlavní číslo verze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="b50f5-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="b50f5-110">Například pro verzi *x.y*, hlavní číslo verze je *x*.</span><span class="sxs-lookup"><span data-stu-id="b50f5-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="b50f5-111">[v] Číslo podverze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="b50f5-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="b50f5-112">Například pro verzi *x.y*, je číslo podverze *y*.</span><span class="sxs-lookup"><span data-stu-id="b50f5-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="b50f5-113">[v] A [SYSKIND](http://msdn.microsoft.com/en-us/662048b2-59a8-48ca-9e4f-2f9a5306faa1) příznak, který identifikuje provozní prostředí.</span><span class="sxs-lookup"><span data-stu-id="b50f5-113">[in] A [SYSKIND](http://msdn.microsoft.com/en-us/662048b2-59a8-48ca-9e4f-2f9a5306faa1) flag that identifies the operating environment.</span></span> <span data-ttu-id="b50f5-114">Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="b50f5-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="b50f5-115">[out] Ukazatel [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) obsahující úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametr.</span><span class="sxs-lookup"><span data-stu-id="b50f5-115">[out] A pointer to a [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b50f5-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b50f5-116">Remarks</span></span>  
 <span data-ttu-id="b50f5-117">`ResolveTypeLib` Metoda je volána [loadtypelibwithresolver – funkce](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) během [Tlbexp.exe (Exportér knihovny)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) zpracování.</span><span class="sxs-lookup"><span data-stu-id="b50f5-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="b50f5-118">Vlastní implementace tohoto rozhraní musí vracet [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) obsahující úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametr.</span><span class="sxs-lookup"><span data-stu-id="b50f5-118">Custom implementations of this interface must return a [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b50f5-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b50f5-119">Requirements</span></span>  
 <span data-ttu-id="b50f5-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b50f5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b50f5-121">**Záhlaví:** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="b50f5-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="b50f5-122">**Knihovna:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="b50f5-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="b50f5-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b50f5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b50f5-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b50f5-124">See Also</span></span>  
 [<span data-ttu-id="b50f5-125">Podpůrné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="b50f5-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [<span data-ttu-id="b50f5-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="b50f5-126">LoadTypeLibEx</span></span>](http://msdn.microsoft.com/en-us/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
