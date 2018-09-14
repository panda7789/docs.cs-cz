---
title: Diagnostikování chyb pomocí asistentů spravovaného ladění
ms.date: 08/14/2018
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45588503"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>Diagnostikování chyb pomocí asistentů spravovaného ladění

Spravované Asistenti ladění (mda) jsou pomůcky pro ladění, které fungují ve spojení s modul CLR (CLR), která poskytují informace o stavu modulu runtime. Asistentů generovat informační zprávy o událostech modulu runtime, které nelze zachytit jinak. Mda můžete použít k izolování aplikace obtížné najít chyby, ke kterým dochází při přechodu mezi spravovaným a nespravovaným kódem.

Je možné [povolit nebo zakázat](#enable-and-disable-mdas) všechny mda přidání klíče registru Windows nebo nastavením proměnné prostředí. Konkrétní mda můžete povolit pomocí nastavení konfigurace aplikace. Další nastavení konfigurace pro některé jednotlivých mda můžete nastavit v konfiguračním souboru aplikace. Protože tyto konfigurační soubory jsou analyzovány při načtení modulu runtime, je nutné povolit MDA před spuštěním spravované aplikace. Nelze ji povolit pro aplikace, které jste už začali.

V následující tabulce jsou uvedeny mda, které se dodávají s rozhraním .NET Framework:

|||
|-|-|
|[asynchronousThreadAbort](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[bindingFailure](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|
|[callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|
|[dangerousThreadingAPI](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|
|[dirtyCastAndCallOnInterface](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[disconnectedContext](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|
|[dllMainReturnsFalse](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|
|[failedQI](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[fatalExecutionEngineError](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|
|[gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|
|[illegalPrepareConstrainedRegion](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|
|[invalidCERCall](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|
|[invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|
|[invalidMemberDeclaration](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|
|[invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|
|[loaderLock](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[loadFromContext](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|
|[marshalCleanupError](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|
|[memberInfoCacheCreation](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[moduloObjectHashcode](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|
|[nonComVisibleBaseClass](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[notMarshalable](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|
|[openGenericCERCall](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|
|[pInvokeLog](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|
|[raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[reentrancy](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|
|[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|
|[streamWriterBufferedDataLost](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[virtualCERCall](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|

Ve výchozím nastavení aktivuje rozhraní .NET Framework podmnožinu mda pro všechny spravované ladicí programy. Můžete zobrazit výchozí nastavení v sadě Visual Studio výběrem **Windows** > **nastavení výjimek** na **ladění** nabídky a pak rozšiřuje **Asistentů spravovaného ladění** seznamu.

![Okno pro nastavení výjimek v sadě Visual Studio](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>Povolení a zakázání mda

Můžete povolit nebo zakázat mda pomocí klíče registru, proměnné prostředí a nastavení konfigurace aplikace. Povolte klíč registru nebo proměnné prostředí použít nastavení konfigurace aplikace.

> [!TIP]
> Místo zákaz mda, můžete sady Visual Studio zabránit v zobrazování dialogových oken MDA při každém přijetí oznámení o MDA. Chcete-li to mohli udělat, zvolte **Windows** > **nastavení výjimek** na **ladění** nabídky, rozbalte **spravované ladění Asistenti**seznamu a pak zaškrtněte nebo zrušte **přerušení při vyvolání** zaškrtávací políčko pro jednotlivé MDA.

### <a name="registry-key"></a>Klíč registru

Chcete-li povolit mda, přidejte **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\MDA** podklíč (typ REG_SZ, hodnota 1) v registru Windows. Následující příklad zkopírujte do textového souboru s názvem *MDAEnable.reg*. Otevřete Editor registru (RegEdit.exe), Windows a **souboru** nabídku zvolte **Import**. Vyberte *MDAEnable.reg* souboru mda na tomto počítači. Nastavení podklíče na hodnotu řetězce **1** (nikoli hodnotu DWORD s názvem **1**) povolí čtení nastavení MDA ze *ApplicationName.suffix*. mda.config souboru. Například konfigurační soubor MDA pro poznámkový blok by se pojmenoval notepad.exe.mda.config.

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

Pokud počítači běží 32bitová aplikace na 64bitový operační systém, by měl vypadat asi takto nastaven klíč MDA:

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

Zobrazit [nastavení konfigurace specifické pro aplikaci](#application-specific-configuration-settings) Další informace. Nastavení registru mohou být přepsány COMPLUS_MDA proměnné prostředí. Zobrazit [proměnné prostředí](#environment-variable) Další informace.

Mda zakázat, nastavte na podklíč MDA **0** (nula) pomocí Editoru registru Windows.

Ve výchozím nastavení jsou některé mda povoleny při spuštění aplikace, která je připojena k ladicímu programu, i bez přidání klíče registru. Můžete zakázat tyto Asistenti spuštěním *MDADisable.reg* souboru, jak je popsáno výše v této části.

### <a name="environment-variable"></a>Proměnná prostředí

Aktivace MDA lze také ovládat proměnnou prostředí COMPLUS_MDA, která přepisuje klíč registru. Řetězec COMPLUS_MDA je velká a malá písmena, oddělené středníky seznam názvů MDA nebo jiné speciální řídicí řetězce. Spouštění v ladicím programu spravované nebo nespravované povoluje sadu mda ve výchozím nastavení. To se provádí implicitně předponou v podobě seznam oddělený středníkem mda povolená ve výchozím nastavení v části ladicích programů na hodnotu proměnné nebo registru klíč prostředí. Speciální řídicí řetězce jsou následující:

- `0` -Deaktivuje všechny mda.

- `1` -Načte nastavení MDA ze *ApplicationName*. mda.config.

- `managedDebugger` -Explicitně aktivuje všechny mda, které jsou aktivovány implicitně při spuštění spravovaného spustitelný soubor v ladicím programu.

- `unmanagedDebugger` -Explicitně aktivuje všechny mda, které jsou aktivované implicitně, když se spustí spustitelný soubor nespravované v ladicím programu.

Pokud konfliktní nastavení se nejnovější nastavení přepíše předchozí nastavení:

- `COMPLUS_MDA=0` Zakáže všechny mda, včetně těch, které implicitně povoleno v ladicím programu.

- `COMPLUS_MDA=gcUnmanagedToManaged` umožňuje `gcUnmanagedToManaged` kromě jakékoli mda, u kterých jde implicitně v ladicím programu.

- `COMPLUS_MDA=0;gcUnmanagedToManaged` umožňuje `gcUnmanagedToManaged` ale zakáže mda, které by jinak implicitně povoleno v ladicím programu.

### <a name="application-specific-configuration-settings"></a>Nastavení konfigurace specifické pro aplikaci

Můžete povolit, zakázat a nakonfigurovat některé Asistenti jednotlivě v konfiguračním souboru MDA pro aplikaci. Pokud chcete povolit použití konfiguračního souboru aplikace pro konfiguraci mda, musí být nastavena MDA klíč registru nebo COMPLUS_MDA proměnné prostředí. Konfigurační soubor aplikace je obvykle umístěn ve stejném adresáři jako spustitelný soubor (.exe) soubor aplikace. Název souboru má podobu *ApplicationName*. mda.config, například notepad.exe.mda.config. Pomocníci, které jsou povoleny v konfiguračním souboru aplikace může mít atributy nebo elementy speciálně pro řízení chování této Pomocníka s nastavením.

Následující příklad ukazuje, jak povolit a konfigurovat [zařazování](../../../docs/framework/debug-trace-profile/marshaling-mda.md):

```xml
<mdaConfig>
  <assistants>
    <marshaling>
      <methodFilter>
        <match name="*"/>
      </methodFilter>
      <fieldFilter>
        <match name="*"/>
      </fieldFilter>
    </marshaling>
  </assistants>
</mdaConfig>
```

`Marshaling` MDA generuje informace o spravovaný typ, který je právě zařazení na nespravovaný typ pro každý Přechod spravované na nespravované aplikace. `Marshaling` MDA můžete také filtrovat názvy metody a pole struktury zadat v **methodFilter** a **fieldFilter** podřízené prvky v uvedeném pořadí.

Následující příklad ukazuje, jak povolit více mda pomocí jejich výchozí nastavení:

```xml
<mdaConfig>
  <assistants>
    <illegalPrepareConstrainedRegion />
    <invalidCERCall />
    <openGenericCERCall />
    <virtualCERCall />
  </assistants>
</mdaConfig>
```

> [!IMPORTANT]
> Pokud zadáte více než jeden Pomocníka s nastavením v konfiguračním souboru, uveďte je v abecedním pořadí. Například, pokud chcete povolit obě `virtualCERCall` a `invalidCERCall` mda, je nutné přidat `<invalidCERCall />` položka před `<virtualCERCall />` položka. Pokud záznamy nejsou v abecedním pořadí, zobrazí se zprávou výjimky neošetřené neplatnou konfigurací souboru.

## <a name="mda-exceptions"></a>Výjimky MDA

Pokud je povolena MDA, je aktivní i když váš kód neprobíhá v ladicím programu. Pokud MDA událost se vyvolá, když ladicí program není k dispozici, zpráva o události se zobrazí v dialogovém okně neošetřenou výjimku, i když není k neošetřené výjimce. Aby se zabránilo dialogových oken, odeberte nastavení MDA povolení při není provádění kódu v prostředí ladění.

Když se spustí váš kód v sadě Visual Studio integrované vývojové prostředí (IDE), se můžete vyhnout, který se zobrazí pro konkrétní události MDA dialogovém okně výjimky. K tomu, na **ladění** nabídce zvolte **Windows** > **nastavení výjimek**. V **nastavení výjimek** okna, rozbalte **asistentů spravovaného ladění** seznamu a poté zrušte zaškrtnutí **přerušení při vyvolání** zaškrtávací políčko pro jednotlivé MDA. Můžete také použít dialogové okno k *povolit* zobrazení MDA výjimka dialogových oknech.

## <a name="mda-output"></a>Výstup MDA

MDA výstup je podobný následujícím příkladu, který se zobrazuje výstup z `PInvokeStackImbalance` MDA:

**Volání funkce PInvoke "MDATest! MDATest.Program::StdCall' má nevyvážená zásobníku. To je pravděpodobné, protože spravovaný podpis PInvoke neodpovídá nespravovanému cílovému podpisu. Zkontrolujte, jestli se konvence volání a parametry podpisu PInvoke odpovídají cílovému nespravovanému podpisu.**

## <a name="see-also"></a>Viz také:

- [Ladění, trasování a profilace](../../../docs/framework/debug-trace-profile/index.md)
