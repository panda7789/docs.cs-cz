---
title: 'Rozhraní .NET framework – chyby inicializace: Správa zkušeností uživatele'
ms.date: 03/30/2017
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28e9aab575876d425112c08b59b9cfc44a8c09a7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379938"
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>Rozhraní .NET framework – chyby inicializace: Správa zkušeností uživatele

Common language runtime (CLR) aktivačního systému určuje verzi modulu CLR, který se použije ke spuštění kódu spravované aplikace. V některých případech nemusí být schopen nalézt verzi modulu CLR pro načtení aktivačního systému. Tuto situaci obvykle dochází, když aplikace vyžaduje verzi CLR, která je neplatná nebo nebyla nainstalována v daném počítači. Pokud se nenajde na požadovanou verzi, CLR aktivačního systému vrátí kód chyby HRESULT z funkce nebo rozhraní, které byla volána a může zobrazit chybová zpráva pro uživatele, který je spuštěna aplikace. Tento článek obsahuje seznam kódů HRESULT a vysvětluje, jak můžete zabránit chybová zpráva se zobrazí.

CLR poskytuje infrastrukturu protokolování si můžete usnadnit ladění problémů aktivace CLR, jak je popsáno v [jak: Ladění problémů aktivace CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md). Tato infrastruktura neměly by být zaměňovány s [protokoly vazeb sestavení](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), které jsou úplně jiného.

## <a name="clr-activation-hresult-codes"></a>Kódy HRESULT aktivace CLR

Aktivace modulu CLR rozhraní API návratové kódy HRESULT nahlásit výsledek operace aktivace na hostitele. CLR hostitele by se měli obrátit vždy tyto návratové hodnoty, než budete pokračovat s další operace.

- CLR_E_SHIM_RUNTIMELOAD

- CLR_E_SHIM_RUNTIMEEXPORT

- CLR_E_SHIM_INSTALLROOT

- CLR_E_SHIM_INSTALLCOMP

- CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND

- CLR_E_SHIM_SHUTDOWNINPROGRESS

## <a name="ui-for-initialization-errors"></a>Uživatelské rozhraní pro chyby inicializace

Pokud systém aktivace CLR nelze načíst správná verze modulu runtime, který vyžaduje aplikaci, zobrazí chybovou zprávu pro uživatele, abychom je informovali, že jejich počítač není správně nakonfigurován ke spuštění aplikace a poskytuje jim příležitosti k nápravě. V této situaci se obvykle zobrazí následující chybová zpráva. Uživatel může zvolit **Ano** přejdete na webu společnosti Microsoft, kde si můžete stáhnout správnou verzi rozhraní .NET Framework pro aplikaci.

![Chyba inicializace rozhraní .NET framework dialogovému oknu](./media/initialization-errors-managing-the-user-experience/initialization-error-dialog.png "typické chybové zprávy pro chyby inicializace")

## <a name="resolving-the-initialization-error"></a>Řešení chyby inicializace

Jako vývojář máte celou řadu možností pro ovládání, chybová zpráva inicializace rozhraní .NET Framework. Například můžete použít rozhraní API příznak zabránit zpráva se zobrazuje, jak je popsáno v další části. Však stále máte k vyřešení problému, který zabránil aplikaci v načtení požadovaný modul runtime. Jinak vaše aplikace nemusí vůbec spustit nebo některé funkce nemusí být k dispozici.

Základní řešení a poskytují nejlepší uživatelské prostředí (méně chybové zprávy), doporučujeme následující postup:

- Pro aplikace .NET Framework 3.5 (a starší): Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze (viz [pokyny](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)).

- Pro aplikace rozhraní .NET Framework 4: Nainstalujte redistribuovatelný balíček .NET Framework 4 jako součást instalace aplikace. Zobrazit [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="controlling-the-error-message"></a>Řízení chybová zpráva

Zobrazení chybovou zprávu pro komunikaci, nebyla nalezena požadovaná verze rozhraní .NET Framework lze zobrazit jako užitečné službu nebo dílčí obtěžování hlukem uživatelům. V obou případech se můžete řídit tohoto uživatelského rozhraní pomocí předání příznaky pro aktivaci rozhraní API.

[Iclrmetahostpolicy::getrequestedruntime –](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda přijímá [metahost_policy_flags –](../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) člena výčtu jako vstup. Můžete zahrnout příznak METAHOST_POLICY_SHOW_ERROR_DIALOG požádat o chybovou zprávu, pokud není nalezena požadovaná verze modulu CLR. Ve výchozím nastavení se zobrazí chybová zpráva. ( [Iclrmetahost::getruntime –](../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) metoda nepřijímá tento příznak a neposkytuje žádným jiným způsobem, zobrazí se chybová zpráva.)

Poskytuje Windows [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkID=255242) funkce, která vám pomůže se deklarovat, zda má být zobrazen jako výsledek kódu, který běží v rámci procesu chybové zprávy. Můžete zadat příznak SEM_FAILCRITICALERRORS zabránit se zobrazí chybová zpráva.

V některých scénářích, je potřeba přepsat nastavení SEM_FAILCRITICALERRORS nastavil procesu aplikace. Pokud máte nativní komponenty modelu COM, který je hostitelem modulu CLR a, která je hostována v procesu, kde SEM_FAILCRITICALERRORS je nastaven, můžete chtít přepsat příznak, v závislosti na dopadu zobrazení chybové zprávy v rámci tohoto konkrétního procesu aplikace. V takovém případě vám pomůže následující příznaky přepsat SEM_FAILCRITICALERRORS:

- Použít METAHOST_POLICY_IGNORE_ERROR_MODE s [iclrmetahostpolicy::getrequestedruntime –](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.

- Použít RUNTIME_INFO_IGNORE_ERROR_MODE s [getrequestedruntimeinfo –](../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) funkce.

## <a name="ui-policy-for-clr-provided-hosts"></a>Zásady uživatelského rozhraní pro zadaný CLR hostitele

Modul CLR zahrnuje sadu hostitelů pro různé scénáře a všichni tito hostitelé zobrazení chybové zprávy, když narazí na problémy s načtením požadovaná verze modulu runtime. Následující tabulka obsahuje seznam hostitelů a jejich zásady chyb na zprávu.

|Hostitel modulu CLR|Popis|Zásada pro zprávu chyby|Chybová zpráva se dají zakázat?|
|--------------|-----------------|--------------------------|------------------------------------|
|Spravovaného hostitele EXE|Spustí spravovaných souborů exe.|Je zobrazena v případě chybějící verzi rozhraní .NET Framework|Ne|
|Spravovaného hostitele modelu COM|Načte spravované komponenty modelu COM do procesu.|Je zobrazena v případě chybějící verzi rozhraní .NET Framework|Ano, tak, že nastavíte SEM_FAILCRITICALERRORS příznak|
|Hostitel technologie ClickOnce|Spouštění aplikací ClickOnce.|Je zobrazena v případě chybějící verzi rozhraní .NET Framework, od verze rozhraní .NET Framework 4.5|Ne|
|XBAP hostitele|Spouštění aplikací WPF XBAP.|Je zobrazena v případě chybějící verzi rozhraní .NET Framework, od verze rozhraní .NET Framework 4.5|Ne|

## <a name="windows-8-behavior-and-ui"></a>Chování systému Windows 8 a uživatelského rozhraní

Systém aktivace CLR poskytuje stejné chování a uživatelského rozhraní na [!INCLUDE[win8](../../../includes/win8-md.md)] stejně jako v jiných verzích operačního systému Windows, kromě případů, kdy se setká s problémy při načítání modul CLR 2.0. [!INCLUDE[win8](../../../includes/win8-md.md)] zahrnuje rozhraní .NET Framework 4.5, který používá CLR 4.5. Ale [!INCLUDE[win8](../../../includes/win8-md.md)] neobsahuje rozhraní .NET Framework 2.0, 3.0 nebo 3.5, který použít modul CLR 2.0. V důsledku toho se aplikace, které závisí na modul CLR 2.0 nespouštějte na [!INCLUDE[win8](../../../includes/win8-md.md)] ve výchozím nastavení. Místo toho zobrazí se následující dialogové okno Povolit uživatele k instalaci rozhraní .NET Framework 3.5. Uživatelé můžou také povolit rozhraní .NET Framework 3.5 v Ovládacích panelech. Obě možnosti jsou popsány v následujícím článku [nainstalovat rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md).

![Dialogové okno pro instalaci verze 3.5 v systému Windows 8](./media/initialization-errors-managing-the-user-experience/install-framework-on-demand-dialog.png "výzva k instalaci rozhraní .NET Framework 3.5 na vyžádání")

> [!NOTE]
> Rozhraní .NET Framework 4.5 nahrazuje rozhraní .NET Framework 4 (CLR 4) na počítači uživatele. Proto rozhraní .NET Framework 4 aplikace běží bez problémů, bez zobrazení v tomto dialogovém okně [!INCLUDE[win8](../../../includes/win8-md.md)].

Při instalaci rozhraní .NET Framework 3.5, můžou uživatelé spouštět aplikace, které závisí na rozhraní .NET Framework 2.0, 3.0 nebo 3.5 na jejich [!INCLUDE[win8](../../../includes/win8-md.md)] počítače. Rozhraní .NET Framework 1.0 a 1.1 aplikace můžou běžet také za předpokladu, že tyto aplikace nejsou explicitně nakonfigurováno pro běh pouze v rozhraní .NET Framework 1.0 nebo 1.1. Zobrazit [migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).

Od verze rozhraní .NET Framework 4.5, protokolování aktivace modulu CLR byla vylepšena zahrnout položky protokolu, které zaznamenávají, kdy a proč se zobrazí chybová zpráva inicializace. Další informace najdete v tématu [jak: Ladění problémů aktivace CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md).

## <a name="see-also"></a>Viz také:

- [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Postupy: Ladění problémů aktivace CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)
- [Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)
