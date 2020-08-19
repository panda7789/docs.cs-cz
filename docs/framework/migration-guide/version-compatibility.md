---
title: Kompatibilita verzí v .NET Framework
description: Přečtěte si o kompatibilitě mezi verzemi .NET Framework, včetně zpětné kompatibility a souběžného spouštění.
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: 92cfdc1a2a530f9790a693d0aa1ca5f65ff1af9f
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558761"
---
# <a name="version-compatibility"></a>Kompatibilita verzí

Zpětná kompatibilita znamená, že aplikace vyvinutá pro konkrétní verzi platformy se spustí v novějších verzích této platformy. .NET Framework se snaží maximalizovat zpětnou kompatibilitu: zdrojový kód napsaný pro jednu verzi .NET Framework by měl kompilovat v novějších verzích .NET Framework a binární soubory, které běží v jedné verzi .NET Framework, by se měly chovat stejně jako v novějších verzích .NET Framework.

## <a name="version-compatibility-for-apps"></a><a name="Apps"></a> Kompatibilita verzí pro aplikace

Ve výchozím nastavení je aplikace spuštěna ve verzi .NET Framework, pro kterou byla vytvořena. Pokud tato verze není k dispozici a konfigurační soubor aplikace nedefinuje podporované verze, může dojít k chybě inicializace .NET Framework. V takovém případě se pokus o spuštění aplikace nezdaří.

Chcete-li definovat konkrétní verze, na kterých aplikace běží, přidejte [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) do konfiguračního souboru aplikace jeden nebo více prvků. Každý `<supportedRuntime>` prvek uvádí podporovanou verzi modulu runtime s prvním zadáním preferované verze a poslední určující nejnižší upřednostňovanou verzi.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Další informace najdete v tématu [Postup: Konfigurace aplikace pro podporu .NET Framework 4 nebo 4. x](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Kompatibilita verzí pro součásti

Aplikace může řídit verzi .NET Framework, na které běží, ale součást nemůže. Komponenty a knihovny tříd jsou načteny v kontextu konkrétní aplikace a jsou proto automaticky spouštěny ve verzi .NET Framework, na které aplikace běží.

Z důvodu tohoto omezení jsou pro komponenty obzvláště důležité záruky kompatibility. Počínaje .NET Framework 4 můžete určit míru, na kterou se očekává, že bude součást kompatibilní napříč více verzemi, a to použitím <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> atributu pro tuto součást. Nástroje mohou tento atribut použít k detekci potenciálního porušení záruky kompatibility v budoucích verzích součásti.

## <a name="backward-compatibility"></a>Zpětná kompatibilita

.NET Framework 4,5 a novější verze jsou zpětně kompatibilní s aplikacemi, které byly vytvořeny v dřívějších verzích .NET Framework. Jinými slovy, aplikace a komponenty sestavené s předchozími verzemi budou fungovat beze změny .NET Framework 4,5 a novějších verzích. Ve výchozím nastavení jsou však aplikace spuštěny ve verzi modulu CLR (Common Language Runtime), pro kterou byly vyvinuty, takže možná budete muset zadat konfigurační soubor, který umožní vaší aplikaci běžet na .NET Framework 4,5 nebo novějších verzích. Další informace najdete v části [Kompatibilita verzí pro aplikace](#Apps) výše v tomto článku.

V praxi může být tato kompatibilita porušena zdánlivě bezvýznamnými změnami v .NET Framework a změnami v programovacích postupech. Například zvýšení výkonu v .NET Framework 4,5 může vystavit konflikt časování, ke kterému nedošlo v dřívějších verzích. Podobně použití pevně zakódované cesty pro .NET Framework sestavení, provádění porovnání rovnosti s konkrétní verzí .NET Framework a získání hodnoty soukromého pole pomocí reflexe nejsou zpětně kompatibilní postupy. Kromě toho každá verze .NET Framework zahrnuje opravy chyb a změny související se zabezpečením, které mohou ovlivnit kompatibilitu některých aplikací a součástí.

Pokud vaše aplikace nebo komponenta nefunguje podle očekávání na .NET Framework 4,5 (včetně jejich vydaných verzí, .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 nebo 4,8), použijte následující kontrolní seznamy:

- Pokud se vaše aplikace vyvinula pro běh v jakékoli verzi .NET Framework počínaje .NET Framework 4,0, přečtěte si téma [Kompatibilita aplikací](application-compatibility.md) a vygenerujte seznamy změn mezi cílovou .NET Framework verzí a verzí, na které vaše aplikace běží.

- Pokud máte aplikaci .NET Framework 3,5, přečtěte si také [.NET Framework 4 problémy s migrací](net-framework-4-migration-issues.md).

- Pokud máte aplikaci .NET Framework 2,0, přečtěte si také [změny v .NET Framework 3,5 SP1](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10)).

- Pokud máte aplikaci .NET Framework 1,1, podívejte se také [na změny v .NET Framework 2,0](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10)).

- Pokud znovu kompilujete existující zdrojový kód pro spuštění v .NET Framework 4,5 nebo jeho vydáních, nebo pokud vyvíjíte novou verzi aplikace nebo komponenty, která cílí na .NET Framework 4,5 nebo jeho vydání z existujícího základu zdrojového kódu, vyhledejte [v knihovně tříd, která je zastaralá](../whats-new/whats-obsolete.md) pro zastaralé typy a členy a použijte popsanou alternativní řešení. (Dříve zkompilovaný kód bude i nadále spuštěn proti typům a členům, které byly označeny jako zastaralé.)

- Pokud zjistíte, že změna v .NET Framework 4,5 přerušila vaši aplikaci, zkontrolujte [schéma nastavení modulu runtime](../configure-apps/file-schema/runtime/index.md)a zejména [ \<AppContextSwitchOverrides> element](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), abyste zjistili, zda můžete použít nastavení modulu runtime v konfiguračním souboru aplikace k obnovení předchozího chování.

- Pokud jste popsali problém, který není dokumentován, otevřete problém na [webu komunity vývojářů pro .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) nebo otevřete problém v [úložišti Microsoft/dotNET GitHub](https://github.com/microsoft/dotnet/issues).

## <a name="side-by-side-execution"></a>Souběžné spouštění

Pokud nemůžete najít vhodné řešení problému, nezapomeňte, že .NET Framework 4,5 (nebo některá z jeho vydání) se spouští souběžně s verzemi 1,1, 2,0 a 3,5 a jedná se o místní aktualizaci, která nahrazuje verzi 4. Pro aplikace, které cílí na verze 1,1, 2,0 a 3,5, můžete na cílový počítač nainstalovat příslušnou verzi .NET Framework, aby se aplikace spouštěla ve vhodném prostředí. Další informace o souběžném spouštění najdete v tématu [Souběžné spouštění](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>Viz také

- [Co je nového](../whats-new/index.md)
- [Zastaralé položky v knihovně tříd](../whats-new/whats-obsolete.md)
- [Kompatibilita aplikací](application-compatibility.md)
- [.NET Framework oficiálních zásad podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Problémy s migrací .NET Framework 4](net-framework-4-migration-issues.md)
