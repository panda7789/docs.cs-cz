---
title: GetTypeLibInfo – funkce
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbd7cd2d5ec515c529905ad524cedf257155b7e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569359"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="3e9c4-102">GetTypeLibInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="3e9c4-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="3e9c4-103">Vrátí informace o zadané knihovny typů prozkoumáním jeho [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) struktury.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-103">Returns information about the specified type library by examining its [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e9c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e9c4-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e9c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e9c4-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="3e9c4-106">[in] Název souboru knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="3e9c4-107">[out] Identifikátor GUID knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="3e9c4-108">[out] ID lokalizace knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="3e9c4-109">[out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) příznak, který identifikuje cílový operační systém pro knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-109">[out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="3e9c4-110">Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="3e9c4-111">[out] Číslo hlavní verze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="3e9c4-112">Například pro verzi *x.y*, je číslo hlavní verze *x*.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="3e9c4-113">[out] Číslo podverze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="3e9c4-114">Například pro verzi *x.y*, je číslo podverze *y*.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e9c4-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e9c4-115">Remarks</span></span>  
 <span data-ttu-id="3e9c4-116">`GetTypeLibInfo` Funkce je volána [Tlbexp.exe (Exportér knihovny typů)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="3e9c4-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="3e9c4-117">Tento nástroj generuje knihovnu typů popisující typy v sestavení common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3e9c4-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="3e9c4-118">Pokud libovolný parametr má hodnotu null, funkce vrátí `HRESULT` z `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="3e9c4-119">V opačném případě vrátí `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="3e9c4-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e9c4-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e9c4-120">Requirements</span></span>  
 <span data-ttu-id="3e9c4-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e9c4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e9c4-122">**Záhlaví:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="3e9c4-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="3e9c4-123">**Knihovna:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="3e9c4-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="3e9c4-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e9c4-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9c4-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e9c4-125">See also</span></span>
- [<span data-ttu-id="3e9c4-126">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="3e9c4-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="3e9c4-127">LoadTypeLibEx – funkce</span><span class="sxs-lookup"><span data-stu-id="3e9c4-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
