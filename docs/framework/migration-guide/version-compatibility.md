---
title: Kompatibilita verzí v .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: c3e2368bc5977d7f50ae7ecea8557c5c545e82a4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455603"
---
# <a name="version-compatibility-in-the-net-framework"></a>Kompatibilita verzí v .NET Framework

Zpětná kompatibilita znamená, že aplikace vyvinutá pro konkrétní verzi platformy se spustí v novějších verzích této platformy. .NET Framework se pokusí Maximalizovat zpětnou kompatibilitu: zdrojový kód napsaný pro jednu verzi .NET Framework by měl být zkompilován v pozdějších verzích .NET Framework a binární soubory, které se spouštějí v jedné verzi .NET Framework, by se měly chovat stejně. novější verze .NET Framework.

## <a name="Apps"></a>Kompatibilita verzí pro aplikace

Ve výchozím nastavení je aplikace spuštěna ve verzi .NET Framework, pro kterou byla vytvořena. Pokud tato verze není k dispozici a konfigurační soubor aplikace nedefinuje podporované verze, může dojít k chybě inicializace .NET Framework. V takovém případě se pokus o spuštění aplikace nezdaří.

Chcete-li definovat konkrétní verze, na kterých aplikace běží, přidejte do konfiguračního souboru aplikace jeden nebo více [\<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) prvky. Každý `<supportedRuntime>` element uvádí podporovanou verzi modulu runtime s prvním zadáním preferované verze a poslední určující nejnižší upřednostňovanou verzi.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Další informace najdete v tématu [Postup: Konfigurace aplikace pro podporu .NET Framework 4 nebo 4. x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Kompatibilita verzí pro součásti

Aplikace může řídit verzi .NET Framework, na které běží, ale součást nemůže. Komponenty a knihovny tříd jsou načteny v kontextu konkrétní aplikace a jsou proto automaticky spouštěny ve verzi .NET Framework, na které aplikace běží.

Z důvodu tohoto omezení jsou pro komponenty obzvláště důležité záruky kompatibility. Počínaje .NET Framework 4 můžete určit míru, na kterou se očekává, že bude součást kompatibilní napříč více verzemi, a to použitím atributu <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> na tuto komponentu. Nástroje mohou tento atribut použít k detekci potenciálního porušení záruky kompatibility v budoucích verzích součásti.

## <a name="backward-compatibility-and-the-net-framework"></a>Zpětná kompatibilita a .NET Framework

.NET Framework 4,5 a novější verze jsou zpětně kompatibilní s aplikacemi, které byly vytvořeny v dřívějších verzích .NET Framework. Jinými slovy, aplikace a komponenty sestavené s předchozími verzemi budou fungovat beze změny .NET Framework 4,5 a novějších verzích. Ve výchozím nastavení jsou však aplikace spuštěny ve verzi modulu CLR (Common Language Runtime), pro kterou byly vyvinuty, takže možná budete muset zadat konfigurační soubor, který umožní vaší aplikaci běžet na .NET Framework 4,5 nebo novějších verzích. Další informace najdete v části [Kompatibilita verzí pro aplikace](#Apps) výše v tomto článku.

V praxi může být tato kompatibilita porušena zdánlivě bezvýznamnými změnami v .NET Framework a změnami v programovacích postupech. Například zvýšení výkonu v .NET Framework 4,5 může vystavit konflikt časování, ke kterému nedošlo v dřívějších verzích. Podobně použití pevně zakódované cesty pro .NET Framework sestavení, provádění porovnání rovnosti s konkrétní verzí .NET Framework a získání hodnoty soukromého pole pomocí reflexe nejsou zpětně kompatibilní postupy. Kromě toho každá verze .NET Framework zahrnuje opravy chyb a změny související se zabezpečením, které mohou ovlivnit kompatibilitu některých aplikací a součástí.

Pokud vaše aplikace nebo komponenta nefunguje podle očekávání na .NET Framework 4,5 (včetně jejich vydaných verzí, .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 nebo 4,8), použijte následující kontrolní seznamy:

- Pokud se vaše aplikace vyvinula pro běh v jakékoli verzi .NET Framework počínaje .NET Framework 4,0, přečtěte si téma [Kompatibilita aplikací](application-compatibility.md) a vygenerujte seznamy změn mezi cílovou .NET Framework verzí a verzí, na které vaše aplikace běží.

- Pokud máte aplikaci .NET Framework 3,5, přečtěte si také [.NET Framework 4 problémy s migrací](../migration-guide/net-framework-4-migration-issues.md).

- Pokud máte aplikaci .NET Framework 2,0, přečtěte si také [změny v .NET Framework 3,5 SP1](https://go.microsoft.com/fwlink/?LinkId=186989).

- Pokud máte aplikaci .NET Framework 1,1, podívejte se také [na změny v .NET Framework 2,0](https://go.microsoft.com/fwlink/?LinkID=125263).

- Pokud znovu kompilujete existující zdrojový kód, který se má spustit na .NET Framework 4,5 nebo jeho vydáních, nebo pokud vyvíjíte novou verzi aplikace nebo komponenty, která cílí na .NET Framework 4,5 nebo jeho vydání z existujícího základu zdrojového kódu, podívejte se, [co je Zastaralé v knihovně tříd](../whats-new/whats-obsolete.md) pro zastaralé typy a členy a použijte popsané alternativní řešení. (Dříve zkompilovaný kód bude i nadále spuštěn proti typům a členům, které byly označeny jako zastaralé.)

- Pokud zjistíte, že změna v .NET Framework 4,5 přerušila vaši aplikaci, zkontrolujte [schéma nastavení modulu runtime](../configure-apps/file-schema/runtime/index.md), a zejména [prvek\<AppContextSwitchOverrides >](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), abyste zjistili, zda můžete použít nastavení modulu runtime v konfigurační soubor aplikace k obnovení předchozího chování.

- Pokud jste popsali problém, který není dokumentován, otevřete problém na [webu komunity vývojářů pro .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) nebo otevřete problém v [úložišti Microsoft/dotNET GitHub](https://github.com/microsoft/dotnet/issues).

## <a name="compatibility-and-side-by-side-execution"></a>Kompatibilita a souběžné spouštění

Pokud nemůžete najít vhodné řešení problému, nezapomeňte, že .NET Framework 4,5 (nebo jedna z jeho vydání) se spouští vedle verzí 1,1, 2,0 a 3,5 a jedná se o místní aktualizaci, která nahrazuje verzi 4. Pro aplikace, které cílí na verze 1,1, 2,0 a 3,5, můžete na cílový počítač nainstalovat příslušnou verzi .NET Framework, aby se aplikace spustila ve vhodném prostředí. Další informace o souběžném spouštění najdete v tématu [Souběžné spouštění](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>Viz také:

- [Co je nového](../whats-new/index.md)
- [Zastaralé položky v knihovně tříd](../whats-new/whats-obsolete.md)
- [Kompatibilita aplikací](../migration-guide/application-compatibility.md)
- [Zásady životního cyklu podpory pro Microsoft .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=248212)
- [Problémy s migrací .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md)
