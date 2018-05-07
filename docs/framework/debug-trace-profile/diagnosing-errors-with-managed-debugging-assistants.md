---
title: Diagnostikování chyb pomocí asistentů spravovaného ladění
ms.date: 03/30/2017
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
ms.openlocfilehash: 16a039a5edb0e1023551f97deefbf7874a19638b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="diagnosing-errors-with-managed-debugging-assistants"></a>Diagnostikování chyb pomocí asistentů spravovaného ladění
Spravované ladění Pomocníci ladění (mda) pomůcek, které spolupracují se modul CLR (CLR) k poskytování informací o stav modulu runtime. Asistentům generovat informační zprávy o událostech runtime, které nelze jinak depeše. Mda můžete izolovat aplikace pevný najít chyby, které dojít, když přechod mezi spravovanými a nespravovanými kódu. Můžete povolit nebo zakázat všechny mda přidání klíče registru systému Windows nebo nastavením proměnné prostředí. Konkrétní mda můžete povolit pomocí nastavení konfigurace aplikace. Můžete nastavit další konfiguraci nastavení pro některé jednotlivé mda v konfiguračním souboru aplikace. Protože tyto konfigurační soubory jsou analyzovat při načtení modulu runtime, je nutné povolit MDA před spuštěním spravované aplikace. Nelze ji povolit pro aplikace, které jste již bylo zahájeno.  
  
> [!NOTE]
>  Pokud MDA je povoleno, bude aktivní i, pokud není váš kód provádění pod ladicí program. Pokud MDA událost se vyvolá, když není k dispozici ladicí program, zpráva o události se zobrazí v dialogovém okně neošetřených výjimek, i když není k neošetřené výjimce. Abyste se vyhnuli dialogové okno, odeberte nastavení povolení MDA při není provádění kódu v prostředí ladění.  
  
> [!NOTE]
>  Pokud váš kód je prováděna v sadě Visual Studio integrované vývojové prostředí (IDE), se můžete vyhnout dialogové okno výjimku, který se zobrazí určité události (mda). K tomu, na **ladění** nabídky, klikněte na tlačítko **výjimky**. (Pokud **ladění** nabídky neobsahuje **výjimky** příkaz, klikněte na tlačítko **přizpůsobit** na **nástroje** nabídky přidat.) V **výjimky** dialogové okno, rozbalte seznam **Pomocníci spravovaného ladění** seznamu a poté zrušte zaškrtnutí **vyvolaná** zaškrtnutí políčka pro jednotlivé (mda). Třeba, aby se zabránilo dialogové okno výjimky pro [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) vymazat **vyvolaná** zaškrtněte políčko vedle jeho názvu v **spravované ladění Pomocníci** seznamu. Tohoto dialogového okna můžete také povolit zobrazení MDA výjimka dialogových oken.  
  
 Následující tabulka uvádí mda dodávaných s rozhraním .NET Framework.  
  
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
  
 Ve výchozím nastavení aktivuje rozhraní .NET Framework podmnožinu mda pro všechny spravované ladicí programy. Můžete zobrazit výchozí nastavení v sadě Visual Studio kliknutím **výjimky** na **ladění** nabídce a rozšíření **Pomocníci spravovaného ladění** seznamu.  
  
## <a name="enabling-and-disabling-mdas"></a>Povolení a zákaz mda  
 Můžete povolit nebo zakázat mda pomocí klíče registru, proměnné prostředí a nastavení konfigurace aplikace. Je nutné povolit klíč registru nebo proměnné prostředí pro použití nastavení konfigurace aplikace.  
  
 V sadě Visual Studio 2005 a novějších verzích Pokud proces hostování je povoleno, nelze zakázat mda, které jsou v sadě výchozí nebo povolit mda, které není ve výchozím nastavení. Proces hostování je zapnutá ve výchozím nastavení, takže musí být explicitně zakázány.  
  
 Pokud chcete zakázat hostitelského procesu v sadě Visual Studio, postupujte takto:  
  
1.  V **Průzkumníku**, vyberte projektu.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
     **Návrhář projektu** se zobrazí v okně.  
  
3.  Klikněte **ladění** kartě.  
  
4.  V **povolit ladicí programy** část, zrušte **povolit sady Visual Studio proces hostování** zaškrtávací políčko.  
  
 Zákaz hostitelského procesu však může ovlivnit výkon. Potřeba zakázat mda tak, že zabrání zobrazení dialogového okna (mda) vždy, když obdrží oznámení MDA Visual Studio se můžete vyhnout. To lze provést, klikněte na tlačítko **výjimky** na **ladění** nabídky, rozbalte **Pomocníci spravovaného ladění** seznamu a potom vyberte nebo zrušte **vyvolaná**zaškrtnutí políčka pro jednotlivé (mda).  
  
### <a name="enabling-and-disabling-mdas-by-using-a-registry-key"></a>Povolení a zákaz mda pomocí klíče registru  
 Můžete povolit mda přidáním HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Podklíč NETFramework\MDA (typ REG_SZ, hodnota 1) v registru systému Windows. Do textového souboru s názvem MDAEnable.reg zkopírujte následující příklad. Otevřete Editor registru systému Windows (RegEdit.exe) a z **soubor** nabídce zvolte **Import**. Vyberte soubor MDAEnable.reg povolit mda na tomto počítači. Nastavení podklíč řetězec hodnotu 1 (ne hodnotu DWORD 1) umožňuje při čtení z nastavení MDA *ApplicationName.suffix*. mda.config souboru. (Například Poznámkový blok v souboru konfigurace (mda) by se jmenovala notepad.exe.mda.config)  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 Pokud počítači běží 32bitová aplikace na 64bitový operační systém, by měl klíč MDA nastavit takto:  
  
```  
      Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 V tématu [povolení a zákaz mda pomocí nastavení konfigurace specifické pro aplikaci](#appConfig) Další informace. Nastavení registru mohou být přepsány COMPLUS_MDA proměnné prostředí. V tématu [povolení a zákaz mda pomocí proměnné prostředí](#envVariable) Další informace.  
  
 Mda zakázat, nastavte podklíč (mda) na hodnotu 0 (nula) pomocí Editoru registru systému Windows.  
  
 Ve výchozím nastavení jsou povolené některé mda při spuštění aplikace, který je připojen k ladicí program, i bez přidání klíče registru. Příkladem takových pomocníci jsou [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) a [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md). Tyto Pomocníci můžete vypnout spuštěním souboru MDADisable.reg, jak je popsáno výše v této části.  
  
<a name="envVariable"></a>   
### <a name="enabling-and-disabling-mdas-by-using-an-environment-variable"></a>Povolení a zákaz mda pomocí proměnné prostředí  
 MDA aktivace může také řízena proměnnou prostředí COMPLUS_MDA, která přepisuje klíč registru. Řetězec COMPLUS_MDA je velká a malá písmena, oddělený středníkem seznam názvů (mda) nebo jiné speciální řídicí řetězce. Spuštění v rámci spravované nebo nespravované ladicí program umožňuje sadu mda ve výchozím nastavení. K tomu je potřeba implicitně předřazení seznam oddělený středníkem mda povolené ve výchozím nastavení v části ladicí programy na hodnotu v prostředí proměnná nebo klíč registru. Speciální řídicí řetězce jsou následující:  
  
-   `0` -Deaktivuje všechny mda.  
  
-   `1` -Načte nastavení MDA z *ApplicationName*. mda.config.  
  
-   `managedDebugger` – Explicitně aktivuje všechny mda, které jsou aktivované implicitně při spuštění spravované spustitelný soubor v části ladicí program.  
  
-   `unmanagedDebugger` – Explicitně aktivuje všechny mda, které jsou aktivované implicitně při spuštění spustitelného souboru nespravované pod ladicí program.  
  
 Pokud jsou konfliktní nastavení, nejnovější nastavení přepsat předchozí nastavení:  
  
-   `COMPLUS_MDA=0` Zakáže všechny mda, včetně těch, které implicitně povoleno pod ladicí program.  
  
-   `COMPLUS_MDA=gcUnmanagedToManaged` umožňuje `gcUnmanagedToManaged` kromě všech mda, které jsou implicitně povoleny v rámci ladicí program.  
  
-   `COMPLUS_MDA=0;gcUnmanagedToManaged` umožňuje `gcUnmanagedToManaged` ale zakáže mda, které by jinak implicitně povolit v části ladicí program.  
  
<a name="appConfig"></a>   
### <a name="enabling-and-disabling-mdas-by-using-application-specific-configuration-settings"></a>Povolení a zákaz mda pomocí nastavení konfigurace specifické pro aplikaci  
 Můžete povolit, zakázat a nakonfigurovat některé Pomocníci jednotlivě v konfiguračním souboru (mda) pro aplikaci. Pokud chcete povolit použití konfiguračního souboru aplikace pro konfiguraci mda, musí být nastavena na klíč registru (mda) nebo proměnná prostředí COMPLUS_MDA. Konfigurační soubor aplikace se obvykle nachází ve stejném adresáři jako spustitelný soubor (.exe) soubor aplikace. Název souboru má tvar *ApplicationName*. mda.config, například notepad.exe.mda.config. Pomocníci, které jsou povoleny v konfiguračním souboru aplikace může mít atributy nebo elementy určená speciálně pro řízení chování tohoto pomocníka. Následující příklad ukazuje, jak povolit a nakonfigurovat [zařazování](../../../docs/framework/debug-trace-profile/marshaling-mda.md).  
  
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
  
 `Marshaling` MDA vysílá informace o spravovaný typ, který je právě zařazen do nespravovaný typ pro každý Přechod spravované na nespravované v aplikaci. `Marshaling` (Mda) můžete také filtrovat názvy metody a struktura pole zadaná v `<methodFilter>` a `<fieldFilter>` podřízených elementů v uvedeném pořadí.  
  
 Následující příklad ukazuje, jak povolit více mda pomocí obnoveno výchozí nastavení.  
  
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
>  Pokud zadáte více než jeden pomocníka v konfiguračním souboru, můžete musí seznam v abecedním pořadí. Například, pokud chcete povolit i `virtualCERCall` a `invalidCERCall` mda, je nutné přidat `<invalidCERCall />` položka před `<virtualCERCall />` položku. Pokud položky nejsou v abecedním pořadí, se zobrazí zpráva o výjimce souboru nezpracované neplatná konfigurace.  
  
### <a name="mda-output"></a>Výstup (mda)  
 MDA výstup se podobá následující příklad, který se zobrazuje výstup z `pInvokeStackImbalance` (mda).  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## <a name="see-also"></a>Viz také  
 [Ladění, trasování a profilace](../../../docs/framework/debug-trace-profile/index.md)
