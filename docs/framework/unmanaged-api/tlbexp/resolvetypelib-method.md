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
ms.openlocfilehash: 0f274befe78e45be3e53335572fd9c1e0b401fd3
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040177"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="777d4-102">ResolveTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="777d4-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="777d4-103">Vyřeší jednoduchý název knihovny typů vrácením jeho plně kvalifikované cesty.</span><span class="sxs-lookup"><span data-stu-id="777d4-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="777d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="777d4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="777d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="777d4-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="777d4-106">pro Typ [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje jednoduchý název knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="777d4-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="777d4-107">pro Identifikátor GUID přiřazený knihovně typů v registru.</span><span class="sxs-lookup"><span data-stu-id="777d4-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="777d4-108">pro ID lokalizace knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="777d4-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="777d4-109">pro Hlavní číslo verze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="777d4-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="777d4-110">Například pro verzi *x. y*je hlavní číslo verze *x*.</span><span class="sxs-lookup"><span data-stu-id="777d4-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="777d4-111">pro Číslo dílčí verze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="777d4-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="777d4-112">Například pro verzi *x. y*je číslo dílčí verze *y*.</span><span class="sxs-lookup"><span data-stu-id="777d4-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="777d4-113">pro Příznak [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) , který identifikuje operační prostředí.</span><span class="sxs-lookup"><span data-stu-id="777d4-113">[in] A [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="777d4-114">Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="777d4-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="777d4-115">mimo Ukazatel na parametr [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="777d4-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="777d4-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="777d4-116">Remarks</span></span>  
 <span data-ttu-id="777d4-117">Metoda je volána [funkcí LoadTypeLibWithResolver –](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) během zpracování [Tlbexp. exe (Exportér knihovny typů).](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) `ResolveTypeLib`</span><span class="sxs-lookup"><span data-stu-id="777d4-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="777d4-118">Vlastní implementace tohoto rozhraní musí vracet [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , který obsahuje úplnou cestu knihovny typů s názvem v `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="777d4-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="777d4-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="777d4-119">Requirements</span></span>  
 <span data-ttu-id="777d4-120">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="777d4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="777d4-121">**Hlaviček** TlbRef. idl, TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="777d4-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="777d4-122">**Knihovna** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="777d4-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="777d4-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="777d4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777d4-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="777d4-124">See also</span></span>

- [<span data-ttu-id="777d4-125">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="777d4-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="777d4-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="777d4-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
