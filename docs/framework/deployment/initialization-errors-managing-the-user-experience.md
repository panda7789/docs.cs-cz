---
title: 'Chyby inicializace rozhraní .NET Framework: Správa uživatelského prostředí'
ms.date: 03/30/2017
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
ms.openlocfilehash: 73a0ffd4a39b144a61bf559ac424414728fb9a3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716457"
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>Chyby inicializace rozhraní .NET Framework: Správa uživatelského prostředí

Aktivační systém CLR (COMMON Language runtime) určuje verzi clr, která bude použita ke spuštění spravovaného kódu aplikace. V některých případech aktivační systém nemusí být schopen najít verzi CLR načíst. K této situaci obvykle dochází, když aplikace vyžaduje verzi CLR, která je neplatná nebo není nainstalována v daném počítači. Pokud požadovaná verze není nalezena, aktivační systém CLR vrátí kód chyby HRESULT z funkce nebo rozhraní, které bylo voláno, a může zobrazit chybovou zprávu uživateli, který je spuštěna aplikace. Tento článek obsahuje seznam kódů HRESULT a vysvětluje, jak můžete zabránit zobrazení chybové zprávy.

Clr poskytuje infrastrukturu protokolování, která vám pomůže ladit problémy s aktivací CLR, jak je popsáno v [tématu Jak: Ladění problémů s aktivací CLR](how-to-debug-clr-activation-issues.md). Tato infrastruktura by neměla být zaměňována s [protokoly vazby sestavení](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), které jsou zcela odlišné.

## <a name="clr-activation-hresult-codes"></a>Kódy HRESULT aktivace CLR

Aktivační api CLR vrátí kódy HRESULT, aby ohlásily výsledek aktivační operace hostiteli. Hostitelé CLR by měli vždy konzultovat tyto vrácené hodnoty před pokračováním v dalších operacích.

- CLR_E_SHIM_RUNTIMELOAD

- CLR_E_SHIM_RUNTIMEEXPORT

- CLR_E_SHIM_INSTALLROOT

- CLR_E_SHIM_INSTALLCOMP

- CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND

- CLR_E_SHIM_SHUTDOWNINPROGRESS

## <a name="ui-for-initialization-errors"></a>UI pro chyby inicializace

Pokud aktivační systém CLR nemůže načíst správnou verzi runtime, kterou vyžaduje aplikace, zobrazí uživatelům chybovou zprávu, která je informuje, že jejich počítač není správně nakonfigurován pro spuštění aplikace, a poskytuje jim příležitost k nápravě situace. V této situaci je obvykle zobrazena následující chybová zpráva. Uživatel může zvolit **možnost Ano** a přejít na web společnosti Microsoft, kde si může stáhnout správnou verzi rozhraní .NET Framework pro aplikaci.

![Dialogové okno Chyba inicializace rozhraní .NET Framework](./media/initialization-errors-managing-the-user-experience/initialization-error-dialog.png "Typická chybová zpráva pro chyby inicializace")

## <a name="resolving-the-initialization-error"></a>Řešení chyby inicializace

Jako vývojář máte řadu možností pro řízení chybové zprávy inicializace rozhraní .NET Framework. Můžete například použít příznak rozhraní API, abyste zabránili zobrazení zprávy, jak je popsáno v další části. Stále však musíte vyřešit problém, který zabránil aplikaci v načtení požadovaného běhu. V opačném případě aplikace nemusí být spuštěna vůbec nebo některé funkce nemusí být k dispozici.

Chcete-li vyřešit základní problémy a poskytnout nejlepší uživatelské prostředí (méně chybových zpráv), doporučujeme následující:

- Pro aplikace rozhraní .NET Framework 3.5 (a starší): Nakonfigurujte aplikaci tak, aby podporovala rozhraní .NET Framework 4 nebo novější verze (viz [pokyny).](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)

- Pro aplikace rozhraní .NET Framework 4: Nainstalujte balíček .NET Framework 4 redistributable jako součást instalace aplikace. Viz [Příručka pro nasazení pro vývojáře](deployment-guide-for-developers.md).

## <a name="controlling-the-error-message"></a>Ovládání chybové zprávy

Zobrazení chybové zprávy pro komunikaci, že požadovaná verze rozhraní .NET Framework nebyla nalezena, lze zobrazit jako užitečnou službu nebo jako menší nepříjemnost pro uživatele. V obou případech můžete řídit toto ui předáním příznaků aktivační chod API.

Metoda [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) přijímá [METAHOST_POLICY_FLAGS](../unmanaged-api/hosting/metahost-policy-flags-enumeration.md) jako vstup METAHOST_POLICY_FLAGS výčtu. Můžete zahrnout příznak METAHOST_POLICY_SHOW_ERROR_DIALOG požádat o chybovou zprávu, pokud není nalezena požadovaná verze CLR. Ve výchozím nastavení se chybová zpráva nezobrazí. (Metoda [ICLRMetaHost::GetRuntime](../unmanaged-api/hosting/iclrmetahost-getruntime-method.md) tento příznak nepřijímá a neposkytuje žádný jiný způsob zobrazení chybové zprávy.)

Systém Windows poskytuje funkci [SetErrorMode,](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) kterou můžete použít k deklarování, zda chcete zobrazit chybové zprávy jako výsledek kódu, který běží v rámci procesu. Můžete zadat příznak SEM_FAILCRITICALERRORS, abyste zabránili zobrazení chybové zprávy.

V některých případech je však důležité přepsat nastavení SEM_FAILCRITICALERRORS nastavené procesem aplikace. Například pokud máte nativní komponentu MODELU COM, která je hostitelem CLR a která je hostována v procesu, kde je nastavena SEM_FAILCRITICALERRORS, můžete přepsat příznak, v závislosti na dopadu zobrazení chybových zpráv v rámci tohoto konkrétního procesu aplikace. V takovém případě můžete použít jeden z následujících příznaků přepsat SEM_FAILCRITICALERRORS:

- Použijte METAHOST_POLICY_IGNORE_ERROR_MODE s metodou [ICLRMetaHostPolicy::GetRequestedRuntime.](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)

- Použijte RUNTIME_INFO_IGNORE_ERROR_MODE s funkcí [GetRequestedRuntimeInfo.](../unmanaged-api/hosting/getrequestedruntimeinfo-function.md)

## <a name="ui-policy-for-clr-provided-hosts"></a>Zásady ui pro hostitele poskytované CLR

CLR obsahuje sadu hostitelů pro různé scénáře a tito hostitelé všichni zobrazit chybovou zprávu, když narazí na problémy načítání požadované verze runtime. V následující tabulce je uveden seznam hostitelů a jejich zásady chybových zpráv.

|Hostitel CLR|Popis|Zásady chybových zpráv|Může být chybová zpráva zakázána?|
|--------------|-----------------|--------------------------|------------------------------------|
|Spravovaný hostitel EXE|Spustí spravované EXES.|Zobrazí se v případě chybějící verze rozhraní .NET Framework.|Ne|
|Spravovaný hostitel COM|Načte spravované součásti modelu COM do procesu.|Zobrazí se v případě chybějící verze rozhraní .NET Framework.|Ano, nastavením příznaku SEM_FAILCRITICALERRORS|
|Hostitel ClickOnce|Spustí aplikace ClickOnce.|Zobrazí se v případě chybějící verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.5.|Ne|
|Hostitel XBAP|Spouští aplikace WPF XBAP.|Zobrazí se v případě chybějící verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.5.|Ne|

## <a name="windows-8-behavior-and-ui"></a>Chování systému Windows 8 a ui

Aktivační systém CLR poskytuje stejné chování a uI v systému Windows 8 jako v jiných verzích operačního systému Windows, s výjimkou případů, kdy narazí na problémy načítání CLR 2.0. Windows 8 obsahuje rozhraní .NET Framework 4.5, který používá CLR 4.5. Systém Windows 8 však neobsahuje rozhraní .NET Framework 2.0, 3.0 nebo 3.5, které všechny používají CLR 2.0. V důsledku toho aplikace, které závisí na CLR 2.0 nespustí v systému Windows 8 ve výchozím nastavení. Místo toho zobrazí následující dialogové okno, které uživatelům umožní nainstalovat rozhraní .NET Framework 3.5. Uživatelé mohou také povolit rozhraní .NET Framework 3.5 v Ovládacích panelech. Obě možnosti jsou popsány v článku [Instalace rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8](../install/dotnet-35-windows-10.md).

![Dialogové okno pro instalaci 3.5 ve Windows 8](./media/initialization-errors-managing-the-user-experience/install-framework-on-demand-dialog.png "Výzva k instalaci rozhraní .NET Framework 3.5 na vyžádání")

> [!NOTE]
> Rozhraní .NET Framework 4.5 nahrazuje rozhraní .NET Framework 4 (CLR 4) v počítači uživatele. Proto aplikace rozhraní .NET Framework 4 běží bez problémů, bez zobrazení tohoto dialogového okna v systému Windows 8.

Po instalaci rozhraní .NET Framework 3.5 mohou uživatelé ve svých počítačích se systémem Windows 8 spouštět aplikace závislé na rozhraní .NET Framework 2.0, 3.0 nebo 3.5. Mohou také spouštět aplikace rozhraní .NET Framework 1.0 a 1.1 za předpokladu, že tyto aplikace nejsou explicitně nakonfigurovány tak, aby se spouštěli pouze v rozhraní .NET Framework 1.0 nebo 1.1. Viz [migrace z rozhraní .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).

Počínaje rozhraním .NET Framework 4.5 bylo vylepšeno protokolování aktivace CLR tak, aby zahrnovalo položky protokolu, které zaznamenávají, kdy a proč se zobrazí chybová zpráva inicializace. Další informace naleznete v [tématu How to: Debug CLR Activation Issues](how-to-debug-clr-activation-issues.md).

## <a name="see-also"></a>Viz také

- [Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md)
- [Postup: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novějších verzí](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Postupy: Ladění problémů aktivace CLR](how-to-debug-clr-activation-issues.md)
- [Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8](../install/dotnet-35-windows-10.md)
