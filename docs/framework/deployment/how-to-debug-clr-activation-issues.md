---
title: Ladění problémů aktivace CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e552f7014c21e2ead61b83ca9909655def6333b
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221073"
---
# <a name="how-to-debug-clr-activation-issues"></a>Ladění problémů aktivace CLR

Pokud narazíte na problémy při získávání aplikace na spouštění se správnou verzí modulu common language runtime (CLR), můžete zobrazit a ladit protokoly aktivace modulu CLR. Tyto protokoly mohou být velmi užitečné při určování původní příčinu chyby aktivace, když aplikace načte jinou verzi CLR, než se očekávalo nebo nebude vůbec načíst modul CLR. [Rozhraní .NET Framework – chyby inicializace: Správa uživatelskou zkušenost](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) popisuje prostředí, když pro aplikaci nebyl nalezen žádný CLR.

Protokolování aktivace modulu CLR může být povoleno systémová pomocí klíčem HKEY_LOCAL_MACHINE registru nebo systémové proměnné prostředí. Vygeneruje se protokol až do položky registru nebo proměnné prostředí se odebere. Alternativně můžete uživatele nebo proměnné prostředí místní proces povolit protokolování pomocí různých rozsahu a doby trvání.

Protokoly aktivace CLR neměly by být zaměňovány s [protokoly vazeb sestavení](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), které jsou úplně jiného.

## <a name="to-enable-clr-activation-logging"></a>Povolení protokolování aktivace CLR

### <a name="using-the-registry"></a>Pomocí registru

1. V editoru registru přejděte na HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (na 32bitovém počítači) nebo HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework složka (na 64bitovém počítači).

2. Přidejte hodnotu řetězce s názvem `CLRLoadLogDir`a nastavte ho na úplnou cestu existující adresář ve kterém chcete ukládat protokoly aktivace modulu CLR.

Aktivace protokolování zůstane povolena, dokud neodeberete řetězcovou hodnotu.

### <a name="using-an-environment-variable"></a>Pomocí proměnné prostředí

- Nastavte `COMPLUS_CLRLoadLogDir` proměnné prostředí na řetězec, který představuje úplnou cestu existující adresář, kam chcete ukládat protokoly aktivace CLR.

     Určuje svého oboru, jak nastavit proměnnou prostředí:

    - Pokud ji nastavíte na úrovni systému, aktivace je povoleno protokolování pro všechny aplikace rozhraní .NET Framework na tomto počítači až do odebrání proměnné prostředí.

    - Pokud ji nastavíte na úrovni uživatele, aktivaci protokolování je povoleno pouze pro aktuální uživatelský účet. Protokolování pokračuje, dokud je proměnná prostředí se odebere.

    - Pokud ji nastavíte z v rámci procesu před načtením modulu CLR, je povoleno protokolování aktivace až do doby ukončení procesu.

    - Pokud ji nastavíte na příkazovém řádku před spuštěním aplikace, je povoleno protokolování aktivace pro každou aplikaci, která se spouští z tohoto příkazového řádku.

     Například pro ukládání protokolů aktivace v adresáři c:\clrloadlogs s rozsahem úrovni procesu, otevřete okno příkazového řádku a zadejte následující příkaz před spuštěním aplikace:

    ```
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a>Příklad

Protokoly aktivace CLR poskytují velké množství dat o CLR – aktivace a použití modulu CLR rozhraní API pro hostování. Většina těchto dat se používá interně společností Microsoft, ale některá data může být také užitečný pro vývojáře, jak je popsáno v tomto článku.

Protokol rozhraní API pro hostování CLR odpovídá pořadí, ve kterém byly volány. Zahrnuje také užitečné údaje o sadu instalovaných modulů runtime v počítači nalezen. Formát protokolu aktivace CLR není samotné popsané, ale je možné podpory vývojářům, kteří potřebují k vyřešení problémů aktivace CLR.

> [!NOTE]
> Aktivace protokolu nelze otevřít, dokud proces, který používá modul CLR byl ukončen.

> [!NOTE]
> Protokoly aktivace CLR nejsou lokalizovány; generují se vždy v anglickém jazyce.

V následujícím příkladu protokolu aktivace je velmi užitečné informace zvýrazní a popsané po protokolu.

```
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

- **Načítání protokolu modulu CLR** poskytuje cestu ke spustitelnému souboru, který spustil proces, který zavedl spravovaného kódu. Všimněte si, že to může být nativních hostitelů.

    ```
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- **Nainstalovat modul Runtime** je sada CLR verze nainstalované na počítači, které jsou kandidáty pro žádost o aktivaci.

    ```
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- **sestaveno s verzí** verzi CLR, který byl použit k vytvoření binární soubor, který byl poskytnut do metody, jako je [iclrmetahostpolicy::getrequestedruntime –](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).

    ```
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- **instalace funkcí na vyžádání** odkazuje na povolení rozhraní .NET Framework 3.5 v systému Windows 8. Zobrazit [rozhraní .NET Framework – chyby inicializace: Správa zkušeností uživatele](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) Další informace o tomto scénáři.

    ```
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a>Viz také:

- [Nasazení](../../../docs/framework/deployment/index.md)
- [Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)