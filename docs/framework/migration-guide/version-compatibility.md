---
title: Kompatibilita verzí v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8db23f8e670406faff01644e751a948096f5fc7c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592887"
---
# <a name="version-compatibility-in-the-net-framework"></a>Kompatibilita verzí v rozhraní .NET Framework

Zpětná kompatibilita znamená, že aplikace vyvinutá pro konkrétní verzi platformy poběží v novějších verzích této platformy. Rozhraní .NET Framework se snaží maximalizovat zpětnou kompatibilitu: Zdrojový kód napsaný pro jednu verzi rozhraní .NET Framework by měl kompilovat v novějších verzích rozhraní .NET Framework a binární soubory, které běží na jednu verzi rozhraní .NET Framework by se měly chovat identicky v novějších verzích rozhraní .NET Framework.

## <a name="Apps"></a> Kompatibilita verzí pro aplikace

Ve výchozím nastavení je aplikace spuštěna ve verzi rozhraní .NET Framework, pro kterou byla vytvořena. Pokud tato verze není k dispozici a konfigurační soubor aplikace nedefinuje podporované verze, může dojít k chybě inicializace rozhraní .NET Framework. V takovém případě se nezdaří pokus o spuštění aplikace.

Chcete-li definovat konkrétní verze, na kterých běží vaše aplikace, přidejte jeden nebo více [ \<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) prvky do konfiguračního souboru aplikace. Každý `<supportedRuntime>` element uvádí podporovanou verzi modulu runtime, přičemž první zadání nejvíce upřednostňovanou verzi a poslední zadání pak nejméně preferovanou verzi.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Další informace najdete v tématu [jak: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Kompatibilita verzí pro komponenty

Aplikace může kontrolovat verzi rozhraní .NET Framework, na kterém běží, ale součást nikoli. Komponenty a knihovny tříd jsou načteny v kontextu konkrétní aplikace, a to je důvod, proč automaticky spouštějí ve verzi rozhraní .NET Framework, na které aplikace poběží.

Z důvodu tohoto omezení je pro součásti obzvlášť důležité zajištění kompatibility. Od verze rozhraní .NET Framework 4, můžete zadat míru, do jaké se očekává součást zůstane kompatibilní ve více verzích použitím <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> atributu pro tuto součást. Nástroje pro tento atribut slouží ke zjištění, že případné porušení kompatibilitu zaručit v budoucích verzích komponenty.

## <a name="backward-compatibility-and-the-net-framework"></a>Zpětná kompatibilita a rozhraní .NET Framework

Rozhraní .NET Framework 4.5 a novější verze jsou zpětně kompatibilní s aplikacemi, které byly vytvořeny v dřívějších verzích rozhraní .NET Framework. Jinými slovy aplikace a komponenty sestavené v předchozích verzích budou fungovat bez úprav na rozhraní .NET Framework 4.5 a novější verze. Ale ve výchozím nastavení, aplikace spuštěny ve verzi modulu common language runtime pro kterou byly vyvinuty, tak může být zapotřebí poskytnout konfigurační soubor aplikace spustit na .NET Framework 4.5 nebo novější verze. Další informace najdete v tématu [Kompatibilita verzí pro aplikace](#Apps) dříve v tomto článku.

V praxi však může být tato kompatibilita porušena zdánlivě bezvýznamnými změnami v rozhraní .NET Framework a změnami v programovacích postupech. Vylepšení výkonu v rozhraní .NET Framework 4.5 můžete například odhalit spor, který nedošlo k v dřívějších verzích. Podobně použití pevně zakódované cesty k sestavením .NET Framework, provádění porovnání rovnosti s konkrétní verzí rozhraní .NET Framework a získání hodnoty soukromého pole pomocí reflexe nejsou zpětně kompatibilní postupy. Kromě toho zahrnuje každá verze rozhraní .NET Framework opravy chyb a změny související se zabezpečením, které mohou ovlivnit kompatibilitu některých aplikací a komponent.

Pokud vaše aplikace nebo komponenta nefunguje v rozhraní .NET Framework 4.5 (včetně dílčích verzí rozhraní .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 nebo 4.8) podle očekávání, použijte následující kontrolní seznamy:

- Pokud vaše aplikace byla vyvinuta v jakékoli verzi rozhraní .NET Framework počínaje .NET Framework 4.0 naleznete v tématu [kompatibilita aplikací v rozhraní .NET Framework](application-compatibility.md) pro vygenerování seznamu změn mezi vaší cílovou verzi rozhraní .NET Framework a verze, na kterém je spuštěná aplikace.

- Pokud budete mít aplikaci .NET Framework 3.5, viz také informace [problémy s migrací rozhraní .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md).

- Pokud budete mít aplikaci .NET Framework 2.0, viz také informace [změny v rozhraní .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkId=186989).

- Pokud budete mít aplikaci .NET Framework 1.1, viz také informace [změny v rozhraní .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkID=125263).

- Pokud jste rekompilace existující zdrojový kód pro spuštění v rozhraní .NET Framework 4.5 nebo jeho verze, nebo pokud vyvíjíte novou verzi aplikace nebo komponenty, které cílí na rozhraní .NET Framework 4.5 nebo jeho verze z existujícího základu zdrojového kódu, zkontrolujte [What's Obsolete in knihovny tříd](../whats-new/whats-obsolete.md) pro zastaralých typech a členech a použijte popsané řešení. (Dříve zkompilovaný kód bude nadále spouštět proti typům a členům, které jsou označené jako zastaralé.)

- Pokud zjistíte, že změna v rozhraní .NET Framework 4.5 způsobila poškození vaší aplikace, zkontrolujte [schéma nastavení běhového prostředí](../configure-apps/file-schema/runtime/index.md)a hlavně [ \<AppContextSwitchOverrides > Element](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)do určení, zda můžete použít nastavení modulu runtime v konfiguračním souboru aplikace k obnovení předchozího chování.

- Pokud narazíte na problém, který nebyl zdokumentován, otevřete problém na [web komunity vývojářů pro .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) nebo otevřete problém [úložiště GitHub Microsoft/dotnet](https://github.com/microsoft/dotnet/issues).

## <a name="compatibility-and-side-by-side-execution"></a>Spuštění kompatibility a vedle sebe

Pokud nemůžete najít vhodné řešení problému, nezapomeňte, že pracuje s verzemi 1.1, 2.0 a 3.5 rozhraní .NET Framework 4.5 (nebo některá z jeho vydání bodu) a je místní aktualizace, která nahrazuje verzi 4. U aplikací s cílovou verzí 1.1, 2.0 a 3.5 můžete nainstalovat odpovídající verzi rozhraní .NET Framework na cílovém počítači spusťte aplikaci v tom nejlepším prostředí. Další informace o spuštění vedle sebe, naleznete v tématu [spuštění vedle sebe](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>Viz také:

- [Co je nového](../whats-new/index.md)
- [Zastaralé položky v knihovně tříd](../whats-new/whats-obsolete.md)
- [Kompatibilita aplikací](../migration-guide/application-compatibility.md)
- [Zásady životního cyklu podpory rozhraní Microsoft .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=248212)
- [Potíže s migrací rozhraní .NET framework 4](../migration-guide/net-framework-4-migration-issues.md)
