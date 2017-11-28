---
title: "GetTypeLibInfo – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetTypeLibInfo
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: GetTypeLibInfo
helpviewer_keywords: GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a5dc55a9538798b81dce9db02583c271b9f2ed54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="fdda1-102">GetTypeLibInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="fdda1-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="fdda1-103">Vrátí informace o knihovně zadaný typ tak, že prověří jeho [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="fdda1-103">Returns information about the specified type library by examining its [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdda1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdda1-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="fdda1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdda1-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="fdda1-106">[v] Název souboru knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fdda1-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="fdda1-107">[out] Identifikátor GUID knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fdda1-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="fdda1-108">[out] Lokalizace ID knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fdda1-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="fdda1-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) příznak, který identifikuje cílový operační systém pro knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fdda1-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="fdda1-110">Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="fdda1-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="fdda1-111">[out] Hlavní číslo verze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fdda1-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="fdda1-112">Například pro verzi *x.y*, hlavní číslo verze je *x*.</span><span class="sxs-lookup"><span data-stu-id="fdda1-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="fdda1-113">[out] Číslo podverze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="fdda1-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="fdda1-114">Například pro verzi *x.y*, je číslo podverze *y*.</span><span class="sxs-lookup"><span data-stu-id="fdda1-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdda1-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdda1-115">Remarks</span></span>  
 <span data-ttu-id="fdda1-116">`GetTypeLibInfo` Funkce je volána [Tlbexp.exe (Exportér knihovny)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="fdda1-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="fdda1-117">Tento nástroj generuje knihovny typů, které popisuje typy v sestavení běžné language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fdda1-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="fdda1-118">Pokud je libovolný parametr hodnotu null, funkce vrátí hodnotu `HRESULT` z `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="fdda1-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="fdda1-119">Funkce `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="fdda1-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdda1-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdda1-120">Requirements</span></span>  
 <span data-ttu-id="fdda1-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdda1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdda1-122">**Záhlaví:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="fdda1-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="fdda1-123">**Knihovna:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="fdda1-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="fdda1-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdda1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdda1-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdda1-125">See Also</span></span>  
 [<span data-ttu-id="fdda1-126">Podpůrné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="fdda1-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="fdda1-127">[LoadTypeLibEx – funkce](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="fdda1-127">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span></span>
