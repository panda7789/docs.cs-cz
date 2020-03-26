---
title: 'Postup: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novějších verzí'
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework
- .NET Framework, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
ms.openlocfilehash: 30fb1da8d758b0e8996b4fcdebbb7fbf545a46c1
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228749"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-later-versions"></a>Postup: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novějších verzí

Všechny aplikace, které jsou hostiteli cltime společného jazyka (CLR) je třeba spustit nebo *aktivovat*, CLR za účelem spuštění spravovaného kódu. Obvykle aplikace .NET Framework funguje ve verzi modulu CLR, pro kterou byla sestavena, ale toto chování stolních aplikací můžete změnit pomocí konfiguračního souboru aplikace (někdy označovaného jako soubor app.config). Nelze však změnit výchozí chování aktivace aplikací pro Windows Store nebo Windows Phone pomocí konfiguračního souboru aplikace. Tento článek vysvětluje, jak povolit spuštění aplikace pro stolní počítače v jiné verzi rozhraní .NET Framework, a poskytuje příklad, jak cílit na verzi 4 nebo novější verze.

 Verze rozhraní .NET Framework, na které aplikace poběží, je určena následovně:

- Konfigurační soubor.

     Pokud konfigurační soubor aplikace obsahuje [ \<podporovanéModul uběh>](../configure-apps/file-schema/startup/supportedruntime-element.md) položky, které určují jednu nebo více verzí rozhraní .NET Framework a jedna z těchto verzí je k dispozici v počítači uživatele, aplikace běží na této verzi. Konfigurační soubor čte [ \<podporovanéModul běhu>](../configure-apps/file-schema/startup/supportedruntime-element.md) položky v pořadí, v jakém jsou uvedeny, a používá první uvedenou verzi rozhraní .NET Framework, která je k dispozici v počítači uživatele. (Použijte [ \<požadovaný prvek> runtime](../configure-apps/file-schema/startup/requiredruntime-element.md) pro verzi 1.0.)

- Kompilovaná verze.

     Pokud neexistuje konfigurační soubor, ale verze rozhraní .NET Framework, pro kterou byla aplikace vytvořena, je přítomna v počítači uživatele, aplikace bude spuštěna v této verzi.

- Nainstalována je nejnovější verze.

     Pokud verze rozhraní .NET Framework, na které byla aplikace postavena, není k dispozici a konfigurační soubor neurčuje verzi v [ \<podporovaném prvku Runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md), aplikace se pokusí spustit na nejnovější verzi rozhraní .NET Framework, která je přítomna v počítači uživatele.

     Aplikace rozhraní .NET Framework 1.0, 1.1, 2.0, 3.0 a 3.5 se však nemusí automaticky spustit v rozhraní .NET Framework 4 nebo vyšším a v některých případech může uživatel obdržet chybovou zprávu s výzvou k instalaci rozhraní .NET Framework 3.5. Chování aktivace závisí rovněž na operačním systému uživatele, protože různé verze systému Windows obsahují různé verze rozhraní .NET Framework. Pokud vaše aplikace podporuje rozhraní .NET Framework 3.5 a 4 nebo vyšší, doporučujeme označit to více záznamy v konfiguračním souboru, aby nedocházelo k chybám inicializace rozhraní .NET Framework. Další informace naleznete v [tématu Verze a závislosti](versions-and-dependencies.md).

 Můžete také nakonfigurovat aplikace rozhraní .NET Framework 3.5 tak, aby se spouštěla v rozhraní .NET Framework 4 nebo novějších verzích, a to i v počítačích s nainstalovanou rozhraním .NET Framework 3.5, abyste mohli využít výhod vylepšení výkonu ve verzích 4 a novějších verzích.

> [!IMPORTANT]
> Doporučujeme vždy testovat aplikaci v každé verzi rozhraní .NET Framework, kterou podporujete. Informace o upgradu aplikace pro pozdější verze rozhraní .NET Framework najdete v [tématu Kompatibilita verzí.](version-compatibility.md)

 Informace o úpravách aplikací rozhraní .NET Framework 1.0 a 1.1 pro podporu Windows 7 a Windows 8 naleznete [v tématu Migrace z rozhraní .NET Framework 1.1](migrating-from-the-net-framework-1-1.md).

## <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-later-versions"></a>Konfigurace aplikace pro spuštění v rozhraní .NET Framework 4 nebo novějších verzích

1. Přidejte nebo vyhledejte konfigurační soubor pro projekt s rozhraním .NET Framework. Konfigurační soubor pro aplikaci je ve stejném adresáři jako aplikace a má stejný název jako aplikace, avšak má příponu .config. Například pro aplikaci s názvem MyExecutable.exe musí mít konfigurační soubor aplikace název MyExecutable.exe.config.

     Chcete-li přidat konfigurační soubor, zvolte na panelu nabídek Sady Visual Studio **možnost Projekt**, Přidat **novou položku**. V levém podokně zvolte **Obecné** a pak zvolte **Konfigurační soubor**. Pojmenujte konfigurační soubor *appName*.exe.config. Tyto možnosti nabídky nejsou k dispozici pro projekty aplikací pro Windows Store nebo Windows Phone, protože zásady aktivace na těchto platformách nelze změnit.

2. Přidejte prvek [ \<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) do konfiguračního souboru aplikace takto:

    ```xml
    <configuration>
      <startup>
        <supportedRuntime version="version"/>
      </startup>
    </configuration>
    ```

     kde * \<verze>* určuje verzi CLR, která je v souladu s verzí rozhraní .NET Framework, kterou vaše aplikace podporuje. Použijte následující řetězce:

    - Rozhraní .NET Framework 1.0: „v1.0.3705“

    - Rozhraní .NET Framework 1.1: „v1.1.4322“

    - Rozhraní .NET Framework 2.0, 3.0 a 3.5: „v2.0.50727“

    - Rozhraní .NET Framework 4 a novější verze: "v4.0"

     Můžete přidat [ \<více podporovanýchModul běhu>](../configure-apps/file-schema/startup/supportedruntime-element.md) prvky, uvedené v pořadí podle priority, chcete-li určit podporu pro více verzí rozhraní .NET Framework.

 Následující tabulka ukazuje, jak nastavení konfiguračního souboru a nainstalované verze rozhraní .NET Framework na počítači určují, na které verzi se aplikace pro rozhraní .NET Framework 3.5 spustí. Příklady jsou specifické pro aplikaci rozhraní .NET Framework 3.5, ale můžete použít podobnou logiku pro cílovou aplikaci vytvořenou pomocí předchozích verzí rozhraní .NET Framework. Číslo verze rozhraní .NET Framework 2.0 (v2.0.50727) se používá k určení rozhraní .NET Framework 3.5 v konfiguračním souboru aplikace.

|Nastavení souboru app.config|V počítači s nainstalovanou verzí 3.5|V počítači s nainstalovanými verzemi 3.5 a 4 nebo novějšími verzemi|V počítači s nainstalovanou verzí 4 nebo novějšími verzemi|
|-|-|-|-|
|Žádný|Spustí se na 3.5|Spustí se na 3.5|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|
|`<supportedRuntime version="v2.0.50727"/>`|Spustí se na 3.5|Spustí se na 3.5|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|Spustí se na 3.5|Spustí se na 3.5|Běží na 4 nebo novější verze|
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|Spustí se na 3.5|Běží na 4 nebo novější verze|Běží na 4 nebo novější verze|
|`<supportedRuntime version="v4.0"/>`|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|Běží na 4 nebo novější verze|Běží na 4 nebo novější verze|

 \*Další informace o této chybové zprávě a způsobech, jak se jí vyhnout, naleznete v [tématu chyby inicializace rozhraní .NET Framework: Správa uživatelského prostředí](../deployment/initialization-errors-managing-the-user-experience.md).

## <a name="see-also"></a>Viz také

- [Migrace z rozhraní .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Průvodce migrací](index.md)
