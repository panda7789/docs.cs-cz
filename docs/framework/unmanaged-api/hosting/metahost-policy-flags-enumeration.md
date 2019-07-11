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
ms.openlocfilehash: 1d35bd5f8aaa2dc0df0044671414a5a936fed24d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781059"
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="d4494-102">METAHOST_POLICY_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="d4494-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="d4494-103">Poskytuje zásady vazby, které jsou společné pro většinu hostitelská prostředí modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d4494-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="d4494-104">Tento výčet je používán [iclrmetahostpolicy::getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d4494-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4494-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4494-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="d4494-106">Členové</span><span class="sxs-lookup"><span data-stu-id="d4494-106">Members</span></span>  
  
|<span data-ttu-id="d4494-107">Člen</span><span class="sxs-lookup"><span data-stu-id="d4494-107">Member</span></span>|<span data-ttu-id="d4494-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d4494-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="d4494-109">Definuje vysokou kompatibilitu zásady, které nebere v úvahu všechny common language runtime (CLR, který je načten do aktuální proces).</span><span class="sxs-lookup"><span data-stu-id="d4494-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="d4494-110">Místo toho bude považovat jenom nainstalované CLRs a předvolby komponenty, odvozena z samotný soubor sestavení, verzi deklarované vytvořené před nebo konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d4494-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="d4494-111">Aplikuje zásad upgradu na výsledek vazby verze, když se najde přesná shoda, na základě obsahu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="d4494-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="d4494-112">To má stejný účinek jako [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="d4494-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="d4494-113">Vazba výsledky jsou vráceny, jako kdyby byly k dispozici k volání image spustit nový proces.</span><span class="sxs-lookup"><span data-stu-id="d4494-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="d4494-114">V současné době `GetRequestedRuntime` ignoruje sadu zaveditelný moduly runtime a sváže s sady instalovaných modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="d4494-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="d4494-115">Tento příznak umožňuje hostiteli zjistit, které modul runtime vytvoří vazbu EXE, když se spustí.</span><span class="sxs-lookup"><span data-stu-id="d4494-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="d4494-116">Zobrazí se dialogové okno chyby, pokud `GetRequestedRuntime` se nepodařilo najít modul runtime, který je kompatibilní se vstupními parametry.</span><span class="sxs-lookup"><span data-stu-id="d4494-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="d4494-117">Od verze rozhraní .NET Framework 4.5, toto dialogové okno chyby můžou mít podobu z funkce Windows dialogové okno s dotazem, jestli mu chcete povolit příslušné funkce.</span><span class="sxs-lookup"><span data-stu-id="d4494-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="d4494-118">`GetRequestedRuntime` jako další vstup pro proces vytváření vazby používá image procesu (a všechny odpovídající konfigurační soubor).</span><span class="sxs-lookup"><span data-stu-id="d4494-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="d4494-119">Ve výchozím nastavení `GetRequestedRuntime` nepřecházel k cestě image proces (obvykle EXE, který byl použit ke spuštění procesu) při určování, modul runtime k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="d4494-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="d4494-120">`GetRequestedRuntime` musíte zkontrolovat, jestli je nainstalovaná odpovídající SKU, když v konfiguračním souboru nejsou dostupné žádné informace.</span><span class="sxs-lookup"><span data-stu-id="d4494-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="d4494-121">To umožňuje aplikacím, které nemají konfiguračních souborů, aby řádně selhat na SKU nižší než výchozí instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d4494-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="d4494-122">Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, jestli je nainstalovaná odpovídající SKU, pokud je zadán atribut SKU v konfiguračním souboru `<supportedRuntime />` elementu.</span><span class="sxs-lookup"><span data-stu-id="d4494-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="d4494-123">`GetRequestedRuntime` Ignorovat SEM_FAILCRITICALERRORS (který je nastaven při volání [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) funkce) a zobrazit dialog s chybou.</span><span class="sxs-lookup"><span data-stu-id="d4494-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="d4494-124">Ve výchozím nastavení potlačí SEM_FAILCRITICALERRORS dialog s chybou.</span><span class="sxs-lookup"><span data-stu-id="d4494-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="d4494-125">To může byly zděděny z jiného procesu a tiché chyba může nežádoucí ve vašem scénáři.</span><span class="sxs-lookup"><span data-stu-id="d4494-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4494-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4494-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4494-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4494-127">Requirements</span></span>  
 <span data-ttu-id="d4494-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4494-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4494-129">**Záhlaví:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="d4494-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="d4494-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4494-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4494-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4494-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4494-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4494-132">See also</span></span>

- [<span data-ttu-id="d4494-133">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="d4494-133">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="d4494-134">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="d4494-134">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
