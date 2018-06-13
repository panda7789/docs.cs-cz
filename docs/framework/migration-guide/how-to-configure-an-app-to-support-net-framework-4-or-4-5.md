---
title: 'Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.5'
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework 4
- .NET Framework 4, configuring apps
- .NET Framework 4.5, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45044e286fa48149c117e97c2e22aa8a0b7d5ce3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393699"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-45"></a>Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.5
Všechny aplikace, které jsou hostiteli common language runtime (CLR) nutné spustit, nebo *aktivovat*, aby bylo možné spustit spravovaného kódu modulu CLR. Obvykle aplikace .NET Framework funguje ve verzi modulu CLR, pro kterou byla sestavena, ale toto chování stolních aplikací můžete změnit pomocí konfiguračního souboru aplikace (někdy označovaného jako soubor app.config). Nelze však změnit výchozí chování aktivace aplikací pro Windows Store nebo Windows Phone pomocí konfiguračního souboru aplikace. Tento článek vysvětluje, jak povolit stolní aplikaci spuštění v jiné verzi rozhraní .NET Framework, a poskytuje příklad, jak se zaměřit na verzi 4 nebo 4.5.  
  
 Verze rozhraní .NET Framework, na které aplikace poběží, je určena následovně:  
  
-   Konfigurační soubor.  
  
     Pokud konfigurační soubor aplikace obsahuje [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) položky, které zadejte jeden nebo více verzí rozhraní .NET Framework a jednu z těchto verzí je k dispozici v počítači uživatele, spuštění aplikace na tuto verzi . Čte konfigurační soubor [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) položky v pořadí, které jsou uvedeny a použije zobrazí první verze rozhraní .NET Framework, které se nachází v počítači uživatele. (Použití [ \<requiredRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) pro verzi 1.0.)  
  
-   Kompilovaná verze.  
  
     Pokud neexistuje konfigurační soubor, ale verze rozhraní .NET Framework, pro kterou byla aplikace vytvořena, je přítomna v počítači uživatele, aplikace bude spuštěna v této verzi.  
  
-   Nainstalována je nejnovější verze.  
  
     Pokud není k dispozici verzi rozhraní .NET Framework, který aplikaci byl postavený na a konfigurační soubor není uveden ve na verzi [ \<supportedRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md), aplikace se pokusí spustit na nejnovější verzi rozhraní .NET Rozhraní, které se nachází v počítači uživatele.  
  
     Aplikace rozhraní .NET Framework 1.0, 1.1, 2.0, 3.0 a 3.5 se však nemusí automaticky spustit v rozhraní .NET Framework 4 nebo vyšším a v některých případech může uživatel obdržet chybovou zprávu s výzvou k instalaci rozhraní .NET Framework 3.5. Chování aktivace závisí rovněž na operačním systému uživatele, protože různé verze systému Windows obsahují různé verze rozhraní .NET Framework. Pokud vaše aplikace podporuje rozhraní .NET Framework 3.5 a 4 nebo vyšší, doporučujeme označit to více záznamy v konfiguračním souboru, aby nedocházelo k chybám inicializace rozhraní .NET Framework. Další informace najdete v tématu [verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md).  
  
 Můžete také nastavit aplikace rozhraní .NET Framework 3.5 k běhu v rozhraní .NET Framework 4 nebo 4.5 i v počítačích s nainstalovaným rozhraním .NET Framework 3.5 a získat tak lepší výkon rozhraní .NET Framework 4 a 4.5.  
  
> [!IMPORTANT]
>  Doporučujeme vždy testovat aplikaci v každé verzi rozhraní .NET Framework, kterou podporujete. V tématu [kompatibilitu verzí](../../../docs/framework/migration-guide/version-compatibility.md) informace o upgradu vaší aplikace pro podporu novější verze rozhraní .NET Framework.  
  
 Informace o úpravách aplikace rozhraní .NET Framework 1.0 a 1.1 pro podporu Windows 7 a Windows 8 najdete v tématu [migrace z verze rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
### <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-45"></a>Konfigurace aplikace pro spuštění v rozhraní .NET Framework 4 nebo 4.5  
  
1.  Přidejte nebo vyhledejte konfigurační soubor pro projekt s rozhraním .NET Framework. Konfigurační soubor pro aplikaci je ve stejném adresáři jako aplikace a má stejný název jako aplikace, avšak má příponu .config. Například pro aplikaci s názvem MyExecutable.exe musí mít konfigurační soubor aplikace název MyExecutable.exe.config.  
  
     Chcete-li přidat konfigurační soubor, na panelu nabídek Visual Studio zvolte **projektu**, **přidat novou položku**. Zvolte **Obecné** v levém podokně a potom zvolte **konfigurační soubor**.  Název konfiguračního souboru *appName*. exe.config. Tyto možnosti nabídek nejsou k dispozici pro projekty aplikací pro Windows Store ani aplikací pro Windows Phone, protože na těchto platformách nelze změnit zásady aktivace.  
  
2.  Přidat [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) element následujícím způsobem, aby konfigurační soubor aplikace:  
  
    ```xml  
    <configuration>  
      <startup>  
        <supportedRuntime version="<version>"/>  
      </startup>  
    </configuration>  
    ```  
  
     kde  *\<verze >* Určuje verzi modulu CLR, zarovnaná s verzi rozhraní .NET Framework, který podporuje aplikace. Použijte následující řetězce:  
  
    -   Rozhraní .NET Framework 1.0: „v1.0.3705“  
  
    -   Rozhraní .NET Framework 1.1: „v1.1.4322“  
  
    -   Rozhraní .NET Framework 2.0, 3.0 a 3.5: „v2.0.50727“  
  
    -   Rozhraní .NET Framework 4 a 4.5 (včetně dílčích verzí, například 4.5.1): "v4.0"  
  
     Můžete přidat více [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) prvky, které jsou uvedeny v pořadí podle preference, určit podporu pro více verzí rozhraní .NET Framework.  
  
 Následující tabulka ukazuje, jak nastavení konfiguračního souboru a nainstalované verze rozhraní .NET Framework na počítači určují, na které verzi se aplikace pro rozhraní .NET Framework 3.5 spustí. Příklady jsou specifické pro aplikaci rozhraní .NET Framework 3.5, ale můžete použít podobnou logiku pro cílovou aplikaci vytvořenou pomocí předchozích verzí rozhraní .NET Framework. Číslo verze rozhraní .NET Framework 2.0 (v2.0.50727) se používá k určení rozhraní .NET Framework 3.5 v konfiguračním souboru aplikace.  
  
|Nastavení souboru app.config|V počítači s nainstalovanou verzí 3.5|V počítači s nainstalovanou verzí 3.5, 4 nebo 4.5|V počítači s nainstalovanou verzí 4 nebo 4.5|  
|-|-|-|-|  
|Žádné|Spustí se na 3.5|Spustí se na 3.5|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|  
|`<supportedRuntime version="v2.0.50727"/>`|Spustí se na 3.5|Spustí se na 3.5|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|  
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|Spustí se na 3.5|Spustí se na 3.5|Spustí se na 4 nebo 4.5|  
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|Spustí se na 3.5|Spustí se na 4 nebo 4.5|Spustí se na 4 nebo 4.5|  
|`<supportedRuntime version="v4.0"/>`|Zobrazí se chybová zpráva, která vyzve uživatele k instalaci správné verze*|Spustí se na 4 nebo 4.5|Spustí se na 4 nebo 4.5|  
  
 \* Další informace o této chybové zprávě a způsoby, jak tomu zamezit najdete v tématu [rozhraní .NET Framework – chyby inicializace: Správa zkušeností uživatele](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md).  
  
## <a name="see-also"></a>Viz také  
 [Migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [Průvodce migrací](../../../docs/framework/migration-guide/index.md)
