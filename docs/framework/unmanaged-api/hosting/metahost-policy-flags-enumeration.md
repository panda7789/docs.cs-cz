---
title: METAHOST_POLICY_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31ff93b6935c2237a5935c4b40cc30b4129edcd0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230600"
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="92c25-102">METAHOST_POLICY_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="92c25-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="92c25-103">Poskytuje zásady vazby, které jsou společné pro většinu hostitelská prostředí modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="92c25-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="92c25-104">Tento výčet je používán [iclrmetahostpolicy::getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="92c25-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c25-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92c25-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="92c25-106">Členové</span><span class="sxs-lookup"><span data-stu-id="92c25-106">Members</span></span>  
  
|<span data-ttu-id="92c25-107">Člen</span><span class="sxs-lookup"><span data-stu-id="92c25-107">Member</span></span>|<span data-ttu-id="92c25-108">Popis</span><span class="sxs-lookup"><span data-stu-id="92c25-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="92c25-109">Definuje vysokou kompatibilitu zásady, které nebere v úvahu všechny common language runtime (CLR, který je načten do aktuální proces).</span><span class="sxs-lookup"><span data-stu-id="92c25-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="92c25-110">Místo toho bude považovat jenom nainstalované CLRs a předvolby komponenty, odvozena z samotný soubor sestavení, verzi deklarované vytvořené před nebo konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="92c25-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="92c25-111">Aplikuje zásad upgradu na výsledek vazby verze, když se najde přesná shoda, na základě obsahu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="92c25-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="92c25-112">To má stejný účinek jako [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="92c25-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="92c25-113">Vazba výsledky jsou vráceny, jako kdyby byly k dispozici k volání image spustit nový proces.</span><span class="sxs-lookup"><span data-stu-id="92c25-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="92c25-114">V současné době `GetRequestedRuntime` ignoruje sadu zaveditelný moduly runtime a sváže s sady instalovaných modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="92c25-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="92c25-115">Tento příznak umožňuje hostiteli zjistit, které modul runtime vytvoří vazbu EXE, když se spustí.</span><span class="sxs-lookup"><span data-stu-id="92c25-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="92c25-116">Zobrazí se dialogové okno chyby, pokud `GetRequestedRuntime` se nepodařilo najít modul runtime, který je kompatibilní se vstupními parametry.</span><span class="sxs-lookup"><span data-stu-id="92c25-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="92c25-117">Počínaje [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], toto dialogové okno chyby můžete mít formu funkce Windows dialogové okno s dotazem, jestli mu chcete povolit příslušné funkce.</span><span class="sxs-lookup"><span data-stu-id="92c25-117">Beginning with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="92c25-118">`GetRequestedRuntime` jako další vstup pro proces vytváření vazby používá image procesu (a všechny odpovídající konfigurační soubor).</span><span class="sxs-lookup"><span data-stu-id="92c25-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="92c25-119">Ve výchozím nastavení `GetRequestedRuntime` nepřecházel k cestě image proces (obvykle EXE, který byl použit ke spuštění procesu) při určování, modul runtime k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="92c25-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="92c25-120">`GetRequestedRuntime` musíte zkontrolovat, jestli je nainstalovaná odpovídající SKU, když v konfiguračním souboru nejsou dostupné žádné informace.</span><span class="sxs-lookup"><span data-stu-id="92c25-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="92c25-121">To umožňuje aplikacím, které nemají konfiguračních souborů, aby řádně selhat na SKU nižší než výchozí instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92c25-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="92c25-122">Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, jestli je nainstalovaná odpovídající SKU, pokud je zadán atribut SKU v konfiguračním souboru `<supportedRuntime />` elementu.</span><span class="sxs-lookup"><span data-stu-id="92c25-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="92c25-123">`GetRequestedRuntime` musíte zkontrolovat, jestli je nainstalovaná odpovídající SKU, když v konfiguračním souboru nejsou dostupné žádné informace.</span><span class="sxs-lookup"><span data-stu-id="92c25-123">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="92c25-124">To umožňuje aplikacím, které nemají konfiguračních souborů, aby řádně selhat na SKU nižší než výchozí instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92c25-124">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="92c25-125">Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, jestli je nainstalovaná odpovídající SKU, pokud je zadán atribut SKU v konfiguračním souboru `<supportedRuntime />` elementu.</span><span class="sxs-lookup"><span data-stu-id="92c25-125">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="92c25-126">`GetRequestedRuntime` Ignorovat SEM_FAILCRITICALERRORS (který je nastaven při volání [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) funkce) a zobrazit dialog s chybou.</span><span class="sxs-lookup"><span data-stu-id="92c25-126">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="92c25-127">Ve výchozím nastavení potlačí SEM_FAILCRITICALERRORS dialog s chybou.</span><span class="sxs-lookup"><span data-stu-id="92c25-127">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="92c25-128">To může byly zděděny z jiného procesu a tiché chyba může nežádoucí ve vašem scénáři.</span><span class="sxs-lookup"><span data-stu-id="92c25-128">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92c25-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92c25-129">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c25-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92c25-130">Requirements</span></span>  
 <span data-ttu-id="92c25-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c25-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c25-132">**Záhlaví:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="92c25-132">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="92c25-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92c25-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92c25-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c25-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c25-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92c25-135">See also</span></span>

- [<span data-ttu-id="92c25-136">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="92c25-136">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="92c25-137">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="92c25-137">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
