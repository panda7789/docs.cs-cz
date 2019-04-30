---
title: 'Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novějších verzí'
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework
- .NET Framework, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40c19dc21bb2262ca1f23573cb89f764e4cd2627
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872687"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-later-versions"></a>Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze

Všechny aplikace, které jsou hostiteli společného jazykového modulu runtime (CLR), musí spustit nebo *aktivovat*, CLR, aby se spustil spravovaný kód. Obvykle aplikace .NET Framework funguje ve verzi modulu CLR, pro kterou byla sestavena, ale toto chování stolních aplikací můžete změnit pomocí konfiguračního souboru aplikace (někdy označovaného jako soubor app.config). Nelze však změnit výchozí chování aktivace aplikací pro Windows Store nebo Windows Phone pomocí konfiguračního souboru aplikace. Tento článek vysvětluje, jak povolit stolní aplikaci spuštění v jiné verzi rozhraní .NET Framework a poskytuje příklad toho, jak do cílové verze 4 nebo novější verze.

 Verze rozhraní .NET Framework, na které aplikace poběží, je určena následovně:

- Konfigurační soubor.

     Pokud konfigurační soubor aplikace obsahuje [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) položek, které určují jednu nebo více verzí rozhraní .NET Framework a jednu z těchto verzí je k dispozici v počítači uživatele, bude aplikace spuštěna na této verzi . Konfigurační soubor čte [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) položky v pořadí, v jakém jsou uvedeny a použije první verze rozhraní .NET Framework, které je k dispozici v počítači uživatele. (Použijte [ \<requiredRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) pro verzi 1.0.)

- Kompilovaná verze.

     Pokud neexistuje konfigurační soubor, ale verze rozhraní .NET Framework, pro kterou byla aplikace vytvořena, je přítomna v počítači uživatele, aplikace bude spuštěna v této verzi.

- Nainstalována je nejnovější verze.

     Pokud není k dispozici verze rozhraní .NET Framework, která byla aplikace vytvořena, a konfigurační soubor nemá verzi v [ \<supportedRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md), aplikace bude spuštěna na nejnovější verzi rozhraní .NET Architektura, která je k dispozici v počítači uživatele.

     Aplikace rozhraní .NET Framework 1.0, 1.1, 2.0, 3.0 a 3.5 se však nemusí automaticky spustit v rozhraní .NET Framework 4 nebo vyšším a v některých případech může uživatel obdržet chybovou zprávu s výzvou k instalaci rozhraní .NET Framework 3.5. Chování aktivace závisí rovněž na operačním systému uživatele, protože různé verze systému Windows obsahují různé verze rozhraní .NET Framework. Pokud vaše aplikace podporuje rozhraní .NET Framework 3.5 a 4 nebo vyšší, doporučujeme označit to více záznamy v konfiguračním souboru, aby nedocházelo k chybám inicializace rozhraní .NET Framework. Další informace najdete v tématu [verze a závislosti](versions-and-dependencies.md).

 Můžete také konfigurovat aplikace rozhraní .NET Framework 3.5 v rozhraní .NET Framework 4 nebo novější verze, a to i v počítačích, které mají nainstalovaný, abyste mohli využívat vylepšení výkonu v verze 4 a novější verze rozhraní .NET Framework 3.5.

> [!IMPORTANT]
> Doporučujeme vždy testovat aplikaci v každé verzi rozhraní .NET Framework, kterou podporujete. Zobrazit [Kompatibilita verzí](version-compatibility.md) informace o inovaci aplikace pro potřeby podpory novějších verzí rozhraní .NET Framework.

 Informace o úpravách aplikací rozhraní .NET Framework 1.0 a 1.1 pro podporu Windows 7 a Windows 8 naleznete v tématu [migrace z rozhraní .NET Framework 1.1](migrating-from-the-net-framework-1-1.md).

## <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-later-versions"></a>Chcete-li nakonfigurovat svoji aplikaci spouštět na rozhraní .NET Framework 4 nebo novější verze

1. Přidejte nebo vyhledejte konfigurační soubor pro projekt s rozhraním .NET Framework. Konfigurační soubor pro aplikaci je ve stejném adresáři jako aplikace a má stejný název jako aplikace, avšak má příponu .config. Například pro aplikaci s názvem MyExecutable.exe musí mít konfigurační soubor aplikace název MyExecutable.exe.config.

     Chcete-li přidat konfigurační soubor, na řádku nabídek sady Visual Studio, zvolte **projektu**, **přidat novou položku**. Zvolte **Obecné** v levém podokně a pak zvolte **konfigurační soubor**. Název konfiguračního souboru *appName*. exe.config. Tyto možnosti nabídek nejsou k dispozici pro projekty aplikací pro Windows Store ani aplikací pro Windows Phone, protože na těchto platformách nelze změnit zásady aktivace.

2. Přidat [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) prvku do konfiguračního souboru aplikace následujícím způsobem:

    ```xml
    <configuration>
      <startup>
        <supportedRuntime version="<version>"/>
      </startup>
    </configuration>
    ```

     kde  *\<verze >* Určuje verzi modulu CLR, která odpovídá verzi rozhraní .NET Framework, která vaše aplikace podporuje. Použijte následující řetězce:

    - Rozhraní .NET Framework 1.0: „v1.0.3705“

    - Rozhraní .NET Framework 1.1: „v1.1.4322“

    - Rozhraní .NET Framework 2.0, 3.0 a 3.5: „v2.0.50727“

    - Rozhraní .NET framework 4 a novější verze: "v4.0"

     Můžete přidat více [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) prvky uvedené v pořadí podle priority, chcete-li určit podporu více verzí rozhraní .NET Framework.

 Následující tabulka ukazuje, jak nastavení konfiguračního souboru a nainstalované verze rozhraní .NET Framework na počítači určují, na které verzi se aplikace pro rozhraní .NET Framework 3.5 spustí. Příklady jsou specifické pro aplikaci rozhraní .NET Framework 3.5, ale můžete použít podobnou logiku pro cílovou aplikaci vytvořenou pomocí předchozích verzí rozhraní .NET Framework. Číslo verze rozhraní .NET Framework 2.0 (v2.0.50727) se používá k určení rozhraní .NET Framework 3.5 v konfiguračním souboru aplikace.

|Nastavení souboru app.config|V počítači s nainstalovanou verzí 3.5|Na počítači s verzí 3.5 a 4 nebo novější|Na počítači s verzí 4 nebo novější|
|-|-|-|-|
|Žádné|Spustí se na 3.5|Spustí se na 3.5|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|
|`<supportedRuntime version="v2.0.50727"/>`|Spustí se na 3.5|Spustí se na 3.5|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|Spustí se na 3.5|Spustí se na 3.5|Běží ve verzi 4 nebo novější|
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|Spustí se na 3.5|Běží ve verzi 4 nebo novější|Běží ve verzi 4 nebo novější|
|`<supportedRuntime version="v4.0"/>`|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|Běží ve verzi 4 nebo novější|Běží ve verzi 4 nebo novější|

 \* Další informace o této chybové zprávě a způsobu, jak jí předcházet, naleznete v tématu [rozhraní .NET Framework – chyby inicializace: Správa zkušeností uživatele](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md).

## <a name="see-also"></a>Viz také:

- [Migrace z rozhraní .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Průvodce migrací](index.md)