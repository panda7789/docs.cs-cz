---
title: 'Chyby inicializace .NET Framework: Správa prostředí pro uživatele'
ms.date: 03/30/2017
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce022e92e8b6770c42800a04a349eff751bdb708
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052067"
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>Chyby inicializace .NET Framework: Správa prostředí pro uživatele

Systém aktivace modulu CLR (Common Language Runtime) určuje verzi modulu CLR, která bude použita ke spuštění kódu spravované aplikace. V některých případech nemusí být aktivační systém schopný najít verzi CLR, která se má načíst. K této situaci obvykle dochází, když aplikace vyžaduje verzi CLR, která je neplatná nebo není v daném počítači nainstalovaná. Pokud se požadovaná verze nenajde, vrátí systém aktivace CLR kód chyby HRESULT z funkce nebo rozhraní, které bylo voláno, a může zobrazit chybovou zprávu uživateli, který aplikaci spouští. Tento článek obsahuje seznam kódů HRESULT a vysvětluje, jak můžete zabránit zobrazení chybové zprávy.

Modul CLR poskytuje infrastrukturu protokolování, která vám umožní ladit problémy s aktivací CLR, jak [je popsáno v tématu How to: Ladění problémů s](how-to-debug-clr-activation-issues.md)aktivací CLR. Tato infrastruktura by se neměla zaměňovat s [protokoly vazeb sestavení](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), které jsou zcela odlišné.

## <a name="clr-activation-hresult-codes"></a>Kódy HRESULT aktivace CLR

Rozhraní API aktivace CLR vrací kódy HRESULT pro hlášení výsledku operace aktivace do hostitele. Hostitelé CLR by měli vždycky tyto návratové hodnoty před dalšími operacemi prostudovat.

- CLR_E_SHIM_RUNTIMELOAD

- CLR_E_SHIM_RUNTIMEEXPORT

- CLR_E_SHIM_INSTALLROOT

- CLR_E_SHIM_INSTALLCOMP

- CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND

- CLR_E_SHIM_SHUTDOWNINPROGRESS

## <a name="ui-for-initialization-errors"></a>Uživatelské rozhraní pro chyby inicializace

Pokud systém aktivace CLR nemůže načíst správnou verzi modulu runtime, který je vyžadován aplikací, zobrazí uživatelům chybovou zprávu s oznámením, že jejich počítač není správně nakonfigurován pro spuštění aplikace a poskytuje jim možnost napravit situaci. V této situaci se obvykle zobrazí následující chybová zpráva. Uživatel může zvolit **Ano** a přejít na web společnosti Microsoft, kde si může stáhnout správnou verzi .NET Framework pro aplikaci.

![Dialogové okno chyby inicializace .NET Framework](./media/initialization-errors-managing-the-user-experience/initialization-error-dialog.png "Typická chybová zpráva pro chyby inicializace")

## <a name="resolving-the-initialization-error"></a>Řešení chyby inicializace

Jako vývojář máte k dispozici řadu možností pro řízení .NET Framework chybové zprávy o inicializaci. Například můžete použít příznak rozhraní API k zabránění zobrazení zprávy, jak je popsáno v další části. Stále však musíte vyřešit problém, který brání vaší aplikaci načíst požadovaný modul runtime. V opačném případě vaše aplikace nemusí běžet vůbec nebo některé funkce nemusí být k dispozici.

Chcete-li vyřešit základní problémy a poskytnout nejlepší uživatelské prostředí (méně chybové zprávy), doporučujeme následující:

- Pro .NET Framework 3,5 (a starší) aplikace: Nakonfigurujte svou aplikaci tak, aby podporovala .NET Framework 4 nebo novější verze (viz [pokyny](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)).

- Pro aplikace .NET Framework 4: Nainstalujte Distribuovatelný balíček .NET Framework 4 jako součást instalace aplikace. V tématu [Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md).

## <a name="controlling-the-error-message"></a>Řízení chybové zprávy

Zobrazuje se chybová zpráva, která oznamuje, že se nenašla požadovaná verze .NET Framework můžete zobrazit jako užitečnou službu nebo menší nepříjemnost pro uživatele. V obou případech můžete toto uživatelské rozhraní řídit předáním příznaků aktivačním rozhraním API.

Metoda [ICLRMetaHostPolicy –:: GetRequestedRuntime –](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) přijímá člena výčtu [METAHOST_POLICY_FLAGS](../unmanaged-api/hosting/metahost-policy-flags-enumeration.md) jako vstup. Pokud se požadovaná verze modulu CLR nenajde, můžete pro vyžádání chybové zprávy zadat příznak METAHOST_POLICY_SHOW_ERROR_DIALOG. Ve výchozím nastavení se chybová zpráva nezobrazí. (Metoda [ICLRMetaHost:: GetRuntime](../unmanaged-api/hosting/iclrmetahost-getruntime-method.md) nepřijímá tento příznak a neposkytuje žádný jiný způsob, jak zobrazit chybovou zprávu.)

Systém Windows poskytuje funkci [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkID=255242) , kterou můžete použít k deklaraci, jestli chcete, aby se chybové zprávy zobrazovaly jako výsledek kódu spuštěného v rámci procesu. Můžete zadat příznak SEM_FAILCRITICALERRORS, který zabrání zobrazení chybové zprávy.

V některých scénářích je však důležité přepsat nastavení SEM_FAILCRITICALERRORS nastavené procesem aplikace. Například pokud máte nativní komponentu modelu COM, která je hostitelem CLR a která je hostována v procesu, kde je nastavena SEM_FAILCRITICALERRORS, může být vhodné přepsat příznak v závislosti na dopadu zobrazení chybových zpráv v rámci tohoto konkrétního procesu aplikace. V takovém případě můžete použít jeden z následujících příznaků k přepsání SEM_FAILCRITICALERRORS:

- Použijte METAHOST_POLICY_IGNORE_ERROR_MODE s metodou [ICLRMetaHostPolicy –:: GetRequestedRuntime –](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) .

- Použijte RUNTIME_INFO_IGNORE_ERROR_MODE s funkcí [GetRequestedRuntimeInfo –](../unmanaged-api/hosting/getrequestedruntimeinfo-function.md) .

## <a name="ui-policy-for-clr-provided-hosts"></a>Zásady uživatelského rozhraní pro hostitele poskytované modulem CLR

CLR obsahuje sadu hostitelů pro celou řadu scénářů a tito hostitelé zobrazí chybovou zprávu, pokud narazí na problémy s načtením požadované verze modulu runtime. Následující tabulka obsahuje seznam hostitelů a jejich zásad chybových zpráv.

|Hostitel CLR|Popis|Zásada chybové zprávy|Může se chybová zpráva zakázat?|
|--------------|-----------------|--------------------------|------------------------------------|
|Spravovaný hostitel EXE|Spustí spravované exe.|Zobrazuje se v případě chybějící verze .NET Framework.|Ne|
|Spravovaný hostitel COM|Načte spravované komponenty modelu COM do procesu.|Zobrazuje se v případě chybějící verze .NET Framework.|Ano, nastavením příznaku SEM_FAILCRITICALERRORS|
|Hostitel ClickOnce|Spustí ClickOnce aplikace.|Je zobrazen v případě chybějící verze .NET Framework počínaje .NET Framework 4,5|Ne|
|Hostitel XBAP|Spustí aplikace WPF XBAP.|Je zobrazen v případě chybějící verze .NET Framework počínaje .NET Framework 4,5|Ne|

## <a name="windows-8-behavior-and-ui"></a>Chování Windows 8 a uživatelské rozhraní

Systém aktivace CLR poskytuje stejné chování a uživatelské rozhraní [!INCLUDE[win8](../../../includes/win8-md.md)] jako v jiných verzích operačního systému Windows, s výjimkou případů, kdy dojde k potížím při načítání CLR 2,0. [!INCLUDE[win8](../../../includes/win8-md.md)]zahrnuje .NET Framework 4,5, který používá CLR 4,5. [!INCLUDE[win8](../../../includes/win8-md.md)] Nezahrnuje však .NET Framework 2,0, 3,0 nebo 3,5, které všechny používají CLR 2,0. V důsledku toho aplikace, které závisí na CLR 2,0, ve výchozím nastavení [!INCLUDE[win8](../../../includes/win8-md.md)] neběží. Místo toho se zobrazí následující dialogové okno, které uživatelům umožní nainstalovat .NET Framework 3,5. Uživatelé také mohou povolit .NET Framework 3,5 v Ovládacích panelech. Obě možnosti jsou popsány v článku [instalace .NET Framework 3,5 ve Windows 10, Windows 8.1 a Windows 8](../install/dotnet-35-windows-10.md).

![Dialogové okno pro 3,5 instalaci v systému Windows 8](./media/initialization-errors-managing-the-user-experience/install-framework-on-demand-dialog.png "Výzva k instalaci .NET Framework 3,5 na vyžádání")

> [!NOTE]
> .NET Framework 4,5 nahrazuje .NET Framework 4 (CLR 4) v počítači uživatele. Proto aplikace .NET Framework 4 běží bez problémů bez zobrazení tohoto dialogového okna v [!INCLUDE[win8](../../../includes/win8-md.md)].

Když je nainstalovaná .NET Framework 3,5, můžou uživatelé spouštět aplikace, které na svých [!INCLUDE[win8](../../../includes/win8-md.md)] počítačích závisejí na .NET Framework 2,0, 3,0 nebo 3,5. Můžou taky spouštět .NET Framework 1,0 a 1,1 aplikace za předpokladu, že tyto aplikace nejsou explicitně nakonfigurované tak, aby se spouštěly jenom v .NET Framework 1,0 nebo 1,1. Viz [migrace z .NET Framework 1,1](../migration-guide/migrating-from-the-net-framework-1-1.md).

Počínaje .NET Framework 4,5 byl vylepšeno protokolování aktivace CLR, aby zahrnovalo položky protokolu, které se zaznamenávají, kdy a proč se zobrazila chybová zpráva o inicializaci. Další informace najdete v tématu [jak: Ladění problémů s](how-to-debug-clr-activation-issues.md)aktivací CLR.

## <a name="see-also"></a>Viz také:

- [Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md)
- [Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Postupy: Ladění problémů s aktivací CLR](how-to-debug-clr-activation-issues.md)
- [Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8](../install/dotnet-35-windows-10.md)
