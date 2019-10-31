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
ms.openlocfilehash: a028d2a8116de4df79f662ee8b2768e6e070428a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141395"
---
# <a name="metahost_policy_flags-enumeration"></a><span data-ttu-id="12f29-102">METAHOST_POLICY_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="12f29-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="12f29-103">Poskytuje zásady vytváření vazeb, které jsou společné pro většinu hostitelů modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="12f29-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="12f29-104">Tento výčet používá metoda [ICLRMetaHostPolicy –:: GetRequestedRuntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="12f29-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f29-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12f29-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="12f29-106">Členové</span><span class="sxs-lookup"><span data-stu-id="12f29-106">Members</span></span>  
  
|<span data-ttu-id="12f29-107">Člen</span><span class="sxs-lookup"><span data-stu-id="12f29-107">Member</span></span>|<span data-ttu-id="12f29-108">Popis</span><span class="sxs-lookup"><span data-stu-id="12f29-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="12f29-109">Definuje zásadu s vysokou kompatibilitou, která nebere v úvahu žádný modul CLR (Common Language Runtime), který je načten do aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="12f29-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="12f29-110">Místo toho zvažuje pouze nainstalované CLRs a předvolby komponenty, jak je odvozeno od samotného souboru sestavení, deklarované předdefinované verze nebo konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="12f29-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="12f29-111">Aplikuje zásadu upgradu na výsledek vazby na verzi, pokud se nenajde přesná shoda, a to na základě obsahu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="12f29-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="12f29-112">To má stejný účinek jako [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="12f29-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="12f29-113">Výsledky vazby jsou vráceny, jako kdyby byla v novém procesu spuštěna image poskytnutá voláním.</span><span class="sxs-lookup"><span data-stu-id="12f29-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="12f29-114">V současné době `GetRequestedRuntime` ignoruje sadu běhových prostředí spustitelný a váže se k sadě instalovaných modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="12f29-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="12f29-115">Tento příznak umožňuje hostiteli určit, ke kterému modulu runtime se připojí EXE při jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="12f29-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="12f29-116">Pokud `GetRequestedRuntime` není schopen najít modul runtime, který je kompatibilní se vstupními parametry, zobrazí se dialogové okno s chybou.</span><span class="sxs-lookup"><span data-stu-id="12f29-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="12f29-117">Počínaje .NET Framework 4,5 může toto dialogové okno s chybou mít podobu dialogového okna funkce systému Windows, které se zeptá, jestli chce uživatel povolit příslušnou funkci.</span><span class="sxs-lookup"><span data-stu-id="12f29-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="12f29-118">`GetRequestedRuntime` používá bitovou kopii procesu (a odpovídající konfigurační soubor) jako další vstup k procesu vazby.</span><span class="sxs-lookup"><span data-stu-id="12f29-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="12f29-119">Ve výchozím nastavení se `GetRequestedRuntime` nevrátí do cesty k bitové kopii procesu (obvykle se jedná o soubor EXE, který se použil ke spuštění procesu) při určení modulu runtime, ke kterému se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="12f29-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="12f29-120">`GetRequestedRuntime` musí ověřit, zda je příslušná SKU nainstalována, když v konfiguračním souboru nejsou k dispozici žádné informace.</span><span class="sxs-lookup"><span data-stu-id="12f29-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="12f29-121">To umožňuje aplikacím, které nemají konfigurační soubory, řádně selhat na menších SKU, než je výchozí instalace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12f29-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="12f29-122">Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, zda je příslušná SKU nainstalována, pokud není zadán atribut SKU v konfiguračním souboru `<supportedRuntime />` elementu.</span><span class="sxs-lookup"><span data-stu-id="12f29-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="12f29-123">`GetRequestedRuntime` by měl ignorovat SEM_FAILCRITICALERRORS (což je nastaveno voláním funkce [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) ) a zobrazit dialogové okno chyby.</span><span class="sxs-lookup"><span data-stu-id="12f29-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="12f29-124">Ve výchozím nastavení SEM_FAILCRITICALERRORS potlačí chybové dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="12f29-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="12f29-125">Mohla být zděděná z jiného procesu a tichá chyba může být ve vašem scénáři nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="12f29-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12f29-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12f29-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f29-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12f29-127">Requirements</span></span>  
 <span data-ttu-id="12f29-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f29-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f29-129">**Hlavička:** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="12f29-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="12f29-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="12f29-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12f29-131">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f29-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f29-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12f29-132">See also</span></span>

- [<span data-ttu-id="12f29-133">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="12f29-133">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="12f29-134">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="12f29-134">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
