---
title: Kompatibilita verzí v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: 2e268753bf5941e9d28ee2bdd82ce77016ddf01a
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102980"
---
# <a name="version-compatibility"></a>Kompatibilita verzí

Zpětná kompatibilita znamená, že aplikace, která byla vyvinuta pro konkrétní verzi platformy, bude spuštěna v novějších verzích této platformy. Rozhraní .NET Framework se pokusí maximalizovat zpětnou kompatibilitu: Zdrojový kód napsaný pro jednu verzi rozhraní .NET Framework by měl zkompilovat v novějších verzích rozhraní .NET Framework a binární soubory spuštěné v jedné verzi rozhraní .NET Framework by se měly v novějších verzích rozhraní .NET Framework chovat stejně.

## <a name="version-compatibility-for-apps"></a><a name="Apps"></a>Kompatibilita verzí aplikací

Ve výchozím nastavení aplikace běží na verzi rozhraní .NET Framework, pro kterou byla vytvořena. Pokud tato verze není k dispozici a konfigurační soubor aplikace nedefinuje podporované verze, může dojít k chybě inicializace rozhraní .NET Framework. V takovém případě se nezdaří pokus o spuštění aplikace.

Chcete-li definovat konkrétní verze, ve kterých vaše aplikace běží, přidejte jeden nebo více [ \<podporovaných Modul uběh>](../configure-apps/file-schema/startup/supportedruntime-element.md) prvky do konfiguračního souboru aplikace. Každý `<supportedRuntime>` prvek uvádí podporovanou verzi modulu runtime, přičemž první určuje nejvíce upřednostňovanou verzi a poslední určuje nejméně upřednostňovanou verzi.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Další informace naleznete v [tématu How to: Configure a App to Support .NET Framework 4 or 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Kompatibilita verzí pro součásti

Aplikace může řídit verzi rozhraní .NET Framework, na kterém je spuštěna, ale komponenta nemůže. Komponenty a knihovny tříd se načítají v kontextu konkrétní aplikace, a proto se automaticky spouštějí ve verzi rozhraní .NET Framework, na které aplikace běží.

Z důvodu tohoto omezení jsou záruky kompatibility obzvláště důležité pro součásti. Počínaje rozhraním .NET Framework 4 můžete určit míru, do jaké má součást zůstat <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> kompatibilní ve více verzích, použitím atributu pro tuto komponentu. Nástroje mohou tento atribut použít ke zjištění potenciálního porušení záruky kompatibility v budoucích verzích součásti.

## <a name="backward-compatibility"></a>Zpětná kompatibilita

Rozhraní .NET Framework 4.5 a novější verze jsou zpětně kompatibilní s aplikacemi, které byly vytvořeny s dřívějšími verzemi rozhraní .NET Framework. Jinými slovy, aplikace a součásti vytvořené s předchozími verzemi budou fungovat beze změn v rozhraní .NET Framework 4.5 a novějších verzích. Ve výchozím nastavení však aplikace běží na verzi běžného jazyka runtime, pro které byly vyvinuty, takže budete muset poskytnout konfigurační soubor, který umožní vaší aplikaci spustit v rozhraní .NET Framework 4.5 nebo novější verze. Další informace naleznete v části [Kompatibilita verzí pro aplikace](#Apps) dříve v tomto článku.

V praxi lze tuto kompatibilitu přerušovat zdánlivě bezvýznamnými změnami v rozhraní .NET Framework a změnami v programovacích technikách. Například zlepšení výkonu v rozhraní .NET Framework 4.5 může vystavit spor, který nedošlo v předchozích verzích. Podobně pomocí pevně zakódované cesty k sestavením rozhraní .NET Framework, provádění porovnání rovnosti s konkrétní verzí rozhraní .NET Framework a získání hodnoty soukromého pole pomocí reflexe nejsou zpětně kompatibilní postupy. Kromě toho každá verze rozhraní .NET Framework obsahuje opravy chyb a změny související se zabezpečením, které mohou ovlivnit kompatibilitu některých aplikací a součástí.

Pokud vaše aplikace nebo komponenta nefunguje podle očekávání v rozhraní .NET Framework 4.5 (včetně jeho bodových vydání, rozhraní .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 nebo 4.8), použijte následující kontrolní seznamy:

- Pokud byla vaše aplikace vyvinuta tak, aby běžela v libovolné verzi rozhraní .NET Framework počínaje rozhraním .NET Framework 4.0, přečtěte si informace o [kompatibilitě aplikací,](application-compatibility.md) kde se vygeneruje seznamy změn mezi cílovou verzí rozhraní .NET Framework a verzí, na které je vaše aplikace spuštěná.

- Pokud máte aplikaci .NET Framework 3.5, přečtěte si také [informace o problémech s migrací rozhraní .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md).

- Pokud máte aplikaci .NET Framework 2.0, přečtěte si také [informace o změnách v rozhraní .NET Framework 3.5 SP1](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10)).

- Pokud máte aplikaci .NET Framework 1.1, přečtěte si také [informace o změnách v rozhraní .NET Framework 2.0](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10)).

- Pokud znovu kompilujete existující zdrojový kód pro spuštění v rozhraní .NET Framework 4.5 nebo jeho bodových verzích nebo pokud vyvíjíte novou verzi aplikace nebo součásti, která cílí na rozhraní .NET Framework 4.5 nebo její bodové verze z existujícího základu zdrojového kódu, [zkontrolujte, co je zastaralé v knihovně tříd](../whats-new/whats-obsolete.md) pro zastaralé typy a členy a použijte popsané řešení. (Dříve zkompilovaný kód bude nadále spuštěn proti typům a členům, které byly označeny jako zastaralé.)

- Pokud zjistíte, že změna v rozhraní .NET Framework 4.5 porušila vaši aplikaci, zkontrolujte [schéma nastavení běhu](../configure-apps/file-schema/runtime/index.md)a zejména [ \<> Element AppContextSwitchOverrides](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), abyste zjistili, zda můžete použít nastavení runtime v konfiguračním souboru aplikace k obnovení předchozího chování.

- Pokud narazíte na problém, který není zdokumentován, otevřete problém na [webu komunity vývojářů pro rozhraní .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) nebo otevřete problém v [úložišti Microsoft/dotnet GitHub](https://github.com/microsoft/dotnet/issues).

## <a name="side-by-side-execution"></a>Souběžné spouštění

Pokud nemůžete najít vhodné řešení pro váš problém, nezapomeňte, že rozhraní .NET Framework 4.5 (nebo jeden z jeho bodových verzí) běží vedle sebe s verzemi 1.1, 2.0 a 3.5 a je na místě aktualizace, která nahrazuje verzi 4. Pro aplikace, které cílí na verze 1.1, 2.0 a 3.5, můžete nainstalovat příslušnou verzi rozhraní .NET Framework do cílového počítače a spustit aplikaci v nejlepším prostředí. Další informace o souběžném provádění naleznete v [tématu Side-by-Side Execution](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>Viz také

- [Co je nového](../whats-new/index.md)
- [Zastaralé položky v knihovně tříd](../whats-new/whats-obsolete.md)
- [Kompatibilita aplikací](../migration-guide/application-compatibility.md)
- [Zásady oficiální podpory rozhraní .NET Framework](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Problémy s migrací rozhraní .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md)
