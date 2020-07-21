---
title: 'Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí'
description: Pomocí zahrnutého příkladu se dozvíte, jak nakonfigurovat desktopovou aplikaci, aby podporovala .NET Framework 4 nebo novější.
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework
- .NET Framework, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
ms.openlocfilehash: 58d71cb7fac7a3c2bef975c99cfab1ca730fb6eb
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475460"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-later-versions"></a>Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí

Všechny aplikace, které jsou hostiteli společného jazykového modulu runtime (CLR), musí spustit nebo *aktivovat*CLR, aby bylo možné spustit spravovaný kód. Obvykle se .NET Framework aplikace spouští ve verzi modulu CLR, na které byla vytvořena, ale toto chování desktopových aplikací můžete změnit pomocí konfiguračního souboru aplikace (někdy označovaného jako app.config soubor). Nelze však změnit výchozí chování aktivace aplikací pro Windows Store nebo Windows Phone pomocí konfiguračního souboru aplikace. Tento článek vysvětluje, jak povolit spuštění desktopové aplikace na jiné verzi .NET Framework a poskytuje příklad, jak cílit na verzi 4 nebo novější verze.

 Verze rozhraní .NET Framework, na které aplikace poběží, je určena následovně:

- Konfigurační soubor.

     Pokud konfigurační soubor aplikace obsahuje [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) položky, které určují jednu nebo více .NET Framework verzí a jedna z těchto verzí je k dispozici v počítači uživatele, aplikace bude spuštěna na této verzi. Konfigurační soubor načte [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) položky v pořadí, v jakém jsou uvedeny, a používá první .NET Framework verzi uvedenou v počítači uživatele. (Použijte [ \<requiredRuntime> element](../configure-apps/file-schema/startup/requiredruntime-element.md) pro verzi 1,0.)

- Kompilovaná verze.

     Pokud neexistuje konfigurační soubor, ale verze rozhraní .NET Framework, pro kterou byla aplikace vytvořena, je přítomna v počítači uživatele, aplikace bude spuštěna v této verzi.

- Nainstalována je nejnovější verze.

     Pokud není k dispozici verze .NET Framework, na které byla aplikace vytvořena, a konfigurační soubor neurčuje verzi v [ \<supportedRuntime> elementu](../configure-apps/file-schema/startup/supportedruntime-element.md), aplikace se pokusí spustit na nejnovější verzi .NET Framework, která se nachází v počítači uživatele.

     Aplikace rozhraní .NET Framework 1.0, 1.1, 2.0, 3.0 a 3.5 se však nemusí automaticky spustit v rozhraní .NET Framework 4 nebo vyšším a v některých případech může uživatel obdržet chybovou zprávu s výzvou k instalaci rozhraní .NET Framework 3.5. Chování aktivace závisí rovněž na operačním systému uživatele, protože různé verze systému Windows obsahují různé verze rozhraní .NET Framework. Pokud vaše aplikace podporuje rozhraní .NET Framework 3.5 a 4 nebo vyšší, doporučujeme označit to více záznamy v konfiguračním souboru, aby nedocházelo k chybám inicializace rozhraní .NET Framework. Další informace najdete v tématu [verze a závislosti](versions-and-dependencies.md).

 Můžete také nakonfigurovat, aby aplikace .NET Framework 3,5 běžely v .NET Framework 4 nebo novějších verzích, a to i v počítačích s nainstalovanou .NET Framework 3,5, aby bylo možné využívat vylepšení výkonu ve verzích 4 a novějších verzích.

> [!IMPORTANT]
> Doporučujeme vždy testovat aplikaci v každé verzi rozhraní .NET Framework, kterou podporujete. Informace o upgradu vaší aplikace na podporu pozdějších verzí .NET Framework najdete v tématu [Kompatibilita verzí](version-compatibility.md) .

 Informace o úpravách aplikací .NET Framework 1,0 a 1,1 pro podporu systémů Windows 7 a Windows 8 najdete v tématu [migrace z .NET Framework 1,1](migrating-from-the-net-framework-1-1.md).

## <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-later-versions"></a>Konfigurace aplikace tak, aby běžela na .NET Framework 4 nebo novějších verzích

1. Přidejte nebo vyhledejte konfigurační soubor pro projekt s rozhraním .NET Framework. Konfigurační soubor pro aplikaci je ve stejném adresáři jako aplikace a má stejný název jako aplikace, avšak má příponu .config. Například pro aplikaci s názvem MyExecutable.exe musí mít konfigurační soubor aplikace název MyExecutable.exe.config.

     Chcete-li přidat konfigurační soubor, v panelu nabídek aplikace Visual Studio vyberte možnost **projekt**, **Přidat novou položku**. V levém podokně zvolte **Obecné** a pak zvolte **konfigurační soubor**. Pojmenujte konfigurační soubor *appName*.exe.config. Tyto možnosti nabídky nejsou k dispozici pro projekty aplikací pro Windows Store ani aplikací pro Windows Phone, protože na těchto platformách nelze změnit zásady aktivace.

2. Přidejte [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) prvek následujícím způsobem do konfiguračního souboru aplikace:

    ```xml
    <configuration>
      <startup>
        <supportedRuntime version="version"/>
      </startup>
    </configuration>
    ```

     kde *\<version>* Určuje verzi modulu CLR, která je v souladu s verzí .NET Framework, kterou vaše aplikace podporuje. Použijte následující řetězce:

    - Rozhraní .NET Framework 1.0: „v1.0.3705“

    - Rozhraní .NET Framework 1.1: „v1.1.4322“

    - Rozhraní .NET Framework 2.0, 3.0 a 3.5: „v2.0.50727“

    - .NET Framework 4 a novější verze: "v 4.0"

     Můžete přidat více [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) prvků, které jsou uvedeny v pořadí podle priority, a určit tak podporu více verzí .NET Framework.

 Následující tabulka ukazuje, jak nastavení konfiguračního souboru a nainstalované verze rozhraní .NET Framework na počítači určují, na které verzi se aplikace pro rozhraní .NET Framework 3.5 spustí. Příklady jsou specifické pro aplikaci rozhraní .NET Framework 3.5, ale můžete použít podobnou logiku pro cílovou aplikaci vytvořenou pomocí předchozích verzí rozhraní .NET Framework. Číslo verze rozhraní .NET Framework 2.0 (v2.0.50727) se používá k určení rozhraní .NET Framework 3.5 v konfiguračním souboru aplikace.

|Nastavení souboru app.config|V počítači s nainstalovanou verzí 3.5|V počítači s nainstalovanými verzemi 3,5 a 4 nebo novějšími verzemi|V počítači s nainstalovanou verzí 4 nebo novější verzí|
|-|-|-|-|
|Žádný|Spustí se na 3.5|Spustí se na 3.5|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|
|`<supportedRuntime version="v2.0.50727"/>`|Spustí se na 3.5|Spustí se na 3.5|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|Spustí se na 3.5|Spustí se na 3.5|Spouští se ve 4 nebo novějších verzích.|
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|Spustí se na 3.5|Spouští se ve 4 nebo novějších verzích.|Spouští se ve 4 nebo novějších verzích.|
|`<supportedRuntime version="v4.0"/>`|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|Spouští se ve 4 nebo novějších verzích.|Spouští se ve 4 nebo novějších verzích.|

 \*Další informace o této chybové zprávě a způsobech, jak jí předcházet, naleznete v tématu [.NET Framework chyby inicializace: Správa prostředí uživatele](../deployment/initialization-errors-managing-the-user-experience.md).

## <a name="see-also"></a>Viz také

- [Migrace z rozhraní .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Průvodce migrací](index.md)
