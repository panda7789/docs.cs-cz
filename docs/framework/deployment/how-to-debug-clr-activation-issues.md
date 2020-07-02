---
title: Jak ladit problémy s aktivací CLR
description: Viz jak ladit problémy s aktivací modulu CLR (Common Language Runtime) v rozhraní .NET. Zobrazit a ladit protokoly aktivace CLR, které mohou být užitečné při určování hlavních příčin.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 5215e82aebf93fa8d6d1937563ab348126a01d97
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622611"
---
# <a name="how-to-debug-clr-activation-issues"></a>Jak ladit problémy s aktivací CLR

Pokud narazíte na problémy při provádění aplikace se správnou verzí modulu CLR (Common Language Runtime), můžete zobrazit a ladit aktivační protokoly CLR. Tyto protokoly můžou být velmi užitečné při určování hlavní příčiny problému s aktivací, když vaše aplikace buď načte jinou verzi CLR, než se očekávalo, nebo vůbec nenačte CLR. [Chyby inicializace .NET Framework: Správa uživatelského prostředí](initialization-errors-managing-the-user-experience.md) , které popisuje prostředí, když pro aplikaci není nalezeno CLR.

Protokolování aktivace CLR lze povolit v rámci systému pomocí HKEY_LOCAL_MACHINE klíče registru nebo proměnné prostředí systému. Protokol bude vygenerován, dokud nebude odebrána položka registru nebo proměnná prostředí. Alternativně můžete použít proměnnou uživatelského prostředí nebo uživatele nebo procesu k povolení protokolování s jiným rozsahem a dobou trvání.

Protokoly aktivace CLR by se neměly zaměňovat s [protokoly vazeb sestavení](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), které jsou zcela odlišné.

## <a name="to-enable-clr-activation-logging"></a>Povolení protokolování aktivace CLR

### <a name="using-the-registry"></a>Použití registru

1. V editoru registru přejděte na HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework (na 32 počítači) nebo HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework složka (na 64 počítači).

2. Přidejte řetězcovou hodnotu s názvem `CLRLoadLogDir` a nastavte ji na úplnou cestu k existujícímu adresáři, kam chcete ukládat protokoly aktivace CLR.

Protokolování aktivace zůstane povolené, dokud neodeberete řetězcovou hodnotu.

### <a name="using-an-environment-variable"></a>Použití proměnné prostředí

- Nastavte `COMPLUS_CLRLoadLogDir` proměnnou prostředí na řetězec, který představuje úplnou cestu k existujícímu adresáři, do kterého chcete ukládat protokoly aktivace modulu CLR.

    Způsob nastavení proměnné prostředí určuje jeho rozsah:

  - Pokud nastavíte tuto možnost na úrovni systému, povolí se protokolování aktivace pro všechny .NET Framework aplikace na daném počítači, dokud se neodebere proměnná prostředí.

  - Pokud nastavíte tuto možnost na úrovni uživatele, protokolování aktivace je povoleno pouze pro aktuální uživatelský účet. Protokolování pokračuje, dokud nebude proměnná prostředí odebrána.

  - Pokud jej před načtením modulu CLR nastavíte v rámci procesu, protokolování aktivace bude povoleno až do ukončení procesu.

  - Pokud ho před spuštěním aplikace nastavíte na příkazovém řádku, povolí se protokolování aktivace pro všechny aplikace, které se spouštějí z tohoto příkazového řádku.

    Chcete-li například uložit aktivační protokoly v adresáři c:\clrloadlogs s rozsahem na úrovni procesu, otevřete okno příkazového řádku a před spuštěním aplikace zadejte následující text:

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a>Příklad

Protokoly aktivace CLR poskytují velké množství dat o aktivaci CLR a použití rozhraní API pro hostování rozhraní CLR. Většinu těchto dat používá společnost Microsoft interně, ale některá z nich mohou být užitečná také pro vývojáře, jak je popsáno v tomto článku.

Protokol odráží pořadí, ve kterém byly volány rozhraní API hostování modulu CLR. Zahrnuje také užitečná data o sadě nainstalovaných modulů runtime zjištěných v počítači. Formát protokolu aktivace CLR není dokumentován, ale lze jej použít k podpoře vývojářů, kteří potřebují vyřešit problémy s aktivací CLR.

> [!NOTE]
> Aktivační protokol nelze otevřít, dokud nebude ukončen proces, který používá modul CLR.

> [!NOTE]
> Protokoly aktivace CLR nejsou lokalizovány; jsou vždycky vygenerované v anglickém jazyce.

V následujícím příkladu aktivačního protokolu jsou nejužitečnější informace zvýrazněny a popsány po protokolu.

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

- **Protokol načítání CLR** poskytuje cestu ke spustitelnému souboru, který spustil proces, který zavedl spravovaný kód. Všimněte si, že se může jednat o nativního hostitele.

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- **Instalovaný modul runtime** je sada verzí CLR nainstalovaná na počítači, které jsou kandidáty na žádost o aktivaci.

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- **sestaveno s verzí** je verze modulu CLR, která byla použita k sestavení binárního souboru, který byl poskytnut metodě jako [ICLRMetaHostPolicy –:: GetRequestedRuntime –](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- **instalace funkcí na vyžádání** odkazuje na povolení .NET Framework 3,5 ve Windows 8. Další informace o tomto scénáři najdete v tématu [.NET Framework chyby inicializace: Správa uživatelského prostředí](initialization-errors-managing-the-user-experience.md) .

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a>Viz také:

- [Nasazení](index.md)
- [Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
