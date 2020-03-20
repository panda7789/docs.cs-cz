---
title: Jak ladit problémy s aktivací CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 602ee3c88237a902d48339836fbe25f636ae9705
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716511"
---
# <a name="how-to-debug-clr-activation-issues"></a>Jak ladit problémy s aktivací CLR

Pokud narazíte na problémy při získávání aplikace ke spuštění se správnou verzí clr jazyka, můžete zobrazit a ladit protokoly aktivace CLR. Tyto protokoly mohou být velmi užitečné při určování hlavní příčinu problému aktivace, když aplikace buď načte jinou verzi CLR, než bylo očekáváno, nebo nenačte CLR vůbec. [Chyby inicializace rozhraní .NET Framework: Správa uživatelského prostředí](initialization-errors-managing-the-user-experience.md) popisuje prostředí, kdy pro aplikaci není nalezen žádný clr.

Protokolování aktivace CLR lze povolit v celém systému pomocí klíče registru HKEY_LOCAL_MACHINE nebo proměnné systémového prostředí. Protokol bude generován, dokud nebude odebrána položka registru nebo proměnná prostředí. Alternativně můžete použít proměnnou prostředí uživatele nebo místního procesu k povolení protokolování s jiným rozsahem a dobou trvání.

Protokoly aktivace CLR by neměly být zaměňovány s [protokoly vazby sestavení](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), které jsou zcela odlišné.

## <a name="to-enable-clr-activation-logging"></a>Povolení protokolování aktivace CLR

### <a name="using-the-registry"></a>Použití registru

1. V Editoru registru přejděte na\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework (v 32bitovém počítači) nebo HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework (v 64bitovém počítači).

2. Přidejte hodnotu `CLRLoadLogDir`řetězce s názvem a nastavte ji na úplnou cestu existujícího adresáře, do kterého chcete uložit protokoly aktivace CLR.

Protokolování aktivace zůstane povoleno, dokud neodeberete hodnotu řetězce.

### <a name="using-an-environment-variable"></a>Použití proměnné prostředí

- Nastavte `COMPLUS_CLRLoadLogDir` proměnnou prostředí na řetězec, který představuje úplnou cestu existujícího adresáře, do kterého chcete uložit protokoly aktivace CLR.

    Způsob nastavení proměnné prostředí určuje její obor:

  - Pokud ji nastavíte na úrovni systému, protokolování aktivace je povoleno pro všechny aplikace rozhraní .NET Framework v tomto počítači, dokud nebude proměnná prostředí odebrána.

  - Pokud ji nastavíte na úrovni uživatele, protokolování aktivace je povoleno pouze pro aktuální uživatelský účet. Protokolování pokračuje, dokud není odebrána proměnná prostředí.

  - Pokud jej nastavíte z procesu před načtením CLR, protokolování aktivace je povolena, dokud proces neskončí.

  - Pokud ji nastavíte na příkazovém řádku před spuštěním aplikace, protokolování aktivace je povoleno pro všechny aplikace, které jsou spuštěny z tohoto příkazového řádku.

    Chcete-li například uložit protokoly aktivace do adresáře c:\clloadlogs s rozsahem na úrovni procesu, otevřete před spuštěním aplikace následující okno a zadejte následující příkaz:

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a>Příklad

Protokoly aktivace CLR poskytují velké množství dat o aktivaci CLR a použití hostitelských api CLR. Většina těchto dat je používána interně společností Microsoft, ale některá data mohou být také užitečná pro vývojáře, jak je popsáno v tomto článku.

Protokol odráží pořadí, ve kterém byly volány CLR hostování API. Obsahuje také užitečná data o sadě nainstalovaných runtimes zjištěných v počítači. Formát protokolu aktivace CLR není sám zdokumentován, ale může být použit k pomoci vývojářům, kteří potřebují vyřešit problémy s aktivací CLR.

> [!NOTE]
> Protokol aktivace nelze otevřít, dokud nebude ukončen proces, který používá clr.

> [!NOTE]
> Protokoly aktivace CLR nejsou lokalizovány. jsou vždy generovány v anglickém jazyce.

V následujícím příkladu protokolu aktivace jsou zvýrazněny a popsány nejužitečnější informace za protokolem.

```output
532,205950.367,CLR Loading log for C:\Tests\myapp.exe
532,205950.367,Log started at 4:26:12 PM on 10/6/2011
532,205950.367,-----------------------------------
532,205950.382,FunctionCall: _CorExeMain
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
532,205950.382,Input values for ComputeVersionString follow this line
532,205950.382,-----------------------------------
532,205950.382,Default Application Name: C:\Tests\myapp.exe
532,205950.382,IsLegacyBind is: 0
532,205950.382,IsCapped is 0
532,205950.382,SkuCheckFlags are 0
532,205950.382,ShouldEmulateExeLaunch is 0
532,205950.382,LegacyBindRequired is 0
532,205950.382,-----------------------------------
532,205950.382,Parsing config file: C:\Tests\myapp.exe
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.
532,205950.398,SEM_FAILCRITICALERRORS is set to 0
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
532,205950.398,FunctionCall: RealDllMain. Reason: 0
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0
```

- **Protokol načítání CLR** poskytuje cestu ke spustitelnému souboru, který spustil proces, který načetl spravovaný kód. Všimněte si, že to může být nativní hostitel.

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- **Nainstalovaný runtime** je sada verzí CLR nainstalovaných v počítači, které jsou kandidáty pro požadavek na aktivaci.

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- **postavens verzí** je verze CLR, která byla použita k sestavení binárního souboru, který byl poskytnut metodě, jako je [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- **instalace funkce na vyžádání** odkazuje na povolení rozhraní .NET Framework 3.5 v systému Windows 8. Další informace o tomto scénáři naleznete v [tématu Chyby inicializace rozhraní .NET Framework: Správa uživatelského prostředí.](initialization-errors-managing-the-user-experience.md)

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a>Viz také

- [Nasazení](index.md)
- [Postup: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novějších verzí](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
