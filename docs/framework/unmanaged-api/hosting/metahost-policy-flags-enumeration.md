---
title: "METAHOST_POLICY_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: METAHOST_POLICY_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: METAHOST_POLICY_FLAGS
helpviewer_keywords: METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8946fdcc7c23e11a3f3d78070532ac0bf72b33b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="7337d-102">METAHOST_POLICY_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="7337d-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="7337d-103">Poskytuje vazby zásady, které jsou společné pro většinu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7337d-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="7337d-104">Tento výčet je používán [iclrmetahostpolicy::getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="7337d-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7337d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7337d-105">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="7337d-106">Členové</span><span class="sxs-lookup"><span data-stu-id="7337d-106">Members</span></span>  
  
|<span data-ttu-id="7337d-107">Člen</span><span class="sxs-lookup"><span data-stu-id="7337d-107">Member</span></span>|<span data-ttu-id="7337d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7337d-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="7337d-109">Definuje zásady vysokou kompatibility, které nebere v úvahu žádné modul common language runtime (CLR), který je načten do aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="7337d-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="7337d-110">Místo toho považuje pouze nainstalované CLRs a předvolby součásti, odvozené z samotný soubor sestavení, verze deklarované vytvořené proti nebo konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7337d-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="7337d-111">Pro výsledek vazby verze platí zásady upgradu, pokud není nalezena přesná shoda na základě obsahu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="7337d-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="7337d-112">Tato akce nemá stejný účinek jako [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="7337d-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="7337d-113">Vazba výsledky se vrátí, jako kdyby bitovou kopii zadaná pro volání nebyly spuštěny v nový proces.</span><span class="sxs-lookup"><span data-stu-id="7337d-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="7337d-114">V současné době `GetRequestedRuntime` ignoruje sadu načíst moduly runtime a sváže s sadu nainstalované moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="7337d-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="7337d-115">Tento příznak umožňuje hostitelům určit, které runtime EXE vytvoří vazbu k při jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="7337d-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="7337d-116">Zobrazí se dialogové okno chyby, pokud `GetRequestedRuntime` se nepodařilo najít modul runtime, který je kompatibilní s vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="7337d-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="7337d-117">Od verze [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], toto dialogové okno chyby můžete mít formu funkce Windows dialogové okno s dotazem, zda uživatel chcete povolit příslušné funkce.</span><span class="sxs-lookup"><span data-stu-id="7337d-117">Beginning with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="7337d-118">`GetRequestedRuntime`používá jako další vstup pro proces vytváření vazby bitovou kopii procesu (a všechny odpovídající soubor konfigurace).</span><span class="sxs-lookup"><span data-stu-id="7337d-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="7337d-119">Ve výchozím nastavení `GetRequestedRuntime` nepřecházely k cesta bitové kopie proces (obvykle EXE, který byl použitý ke spuštění procesu) při určování modulu runtime pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7337d-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="7337d-120">`GetRequestedRuntime`musí zkontrolovat, zda je nainstalována příslušné SKU, pokud v konfiguračním souboru nejsou dostupné žádné informace.</span><span class="sxs-lookup"><span data-stu-id="7337d-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="7337d-121">To umožňuje aplikacím, které nemají konfigurační soubory řádně selhání na menší SKU než výchozí instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7337d-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="7337d-122">Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, jestli je nainstalovaná odpovídající verze SKU, pokud atribut SKU je uveden v konfiguračním souboru `<supportedRuntime />` elementu.</span><span class="sxs-lookup"><span data-stu-id="7337d-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="7337d-123">`GetRequestedRuntime`musí zkontrolovat, zda je nainstalována příslušné SKU, pokud v konfiguračním souboru nejsou dostupné žádné informace.</span><span class="sxs-lookup"><span data-stu-id="7337d-123">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="7337d-124">To umožňuje aplikacím, které nemají konfigurační soubory řádně selhání na menší SKU než výchozí instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7337d-124">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="7337d-125">Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, jestli je nainstalovaná odpovídající verze SKU, pokud atribut SKU je uveden v konfiguračním souboru `<supportedRuntime />` elementu.</span><span class="sxs-lookup"><span data-stu-id="7337d-125">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="7337d-126">`GetRequestedRuntime`třeba ignorovat SEM_FAILCRITICALERRORS (který je nastaven při volání [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) funkce) a zobrazit dialogové okno chyby.</span><span class="sxs-lookup"><span data-stu-id="7337d-126">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="7337d-127">Ve výchozím nastavení potlačí SEM_FAILCRITICALERRORS dialogové okno chyby.</span><span class="sxs-lookup"><span data-stu-id="7337d-127">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="7337d-128">Ho může mít bylo zděděno z jiného procesu a tichou chyba může být žádoucí ve vašem scénáři.</span><span class="sxs-lookup"><span data-stu-id="7337d-128">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7337d-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7337d-129">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7337d-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7337d-130">Requirements</span></span>  
 <span data-ttu-id="7337d-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7337d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7337d-132">**Záhlaví:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="7337d-132">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="7337d-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7337d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7337d-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7337d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7337d-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="7337d-135">See Also</span></span>  
 [<span data-ttu-id="7337d-136">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="7337d-136">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="7337d-137">Getrequestedruntime – metoda</span><span class="sxs-lookup"><span data-stu-id="7337d-137">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
