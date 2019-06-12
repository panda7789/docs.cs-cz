---
title: Migrace z rozhraní .NET Framework 1.1
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9671dd87e3185e9d4b997e2ea75770f756605efb
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833510"
---
# <a name="migrating-from-the-net-framework-11"></a>Migrace z rozhraní .NET Framework 1.1

[!INCLUDE[win7](../../../includes/win7-md.md)] a novějších verzích operačního systému Windows nepodporuje rozhraní .NET Framework 1.1. V důsledku toho nebudou aplikace, které jsou cíleny rozhraní .NET Framework 1.1 spuštěny bez úprav na [!INCLUDE[win7](../../../includes/win7-md.md)] nebo novější verze operačního systému. Toto téma popisuje kroky potřebné ke spuštění aplikace, která cílí na rozhraní .NET Framework 1.1 v rámci [!INCLUDE[win7](../../../includes/win7-md.md)] a novějšími verzemi operačního systému Windows. Další informace o rozhraní .NET Framework 1.1 a [!INCLUDE[win8](../../../includes/win8-md.md)], naleznete v tématu [spouštění aplikací .NET Framework v systému Windows 8 a novější verze 1.1](../../../docs/framework/install/run-net-framework-1-1-apps.md).

## <a name="retargeting-or-recompiling"></a>Přeorientovat nebo rekompilovat

Existují dva způsoby, jak získat aplikace, která byla sestavena pomocí rozhraní .NET Framework 1.1 pro spuštění na [!INCLUDE[win7](../../../includes/win7-md.md)] nebo novějším operačním systémem Windows:

- Můžete změnit cíl aplikace pro spuštění v rozhraní .NET Framework 4 a novější verze. Mění se cílení vyžaduje, abyste přidali [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) prvku do konfiguračního souboru aplikace, který povolí jeho spuštění v rozhraní .NET Framework 4 a novější verze. Konfigurační soubor získá následující tvar:

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- Můžete znovu zkompilovat aplikaci s kompilátorem, který cílí na .NET Framework 4 nebo novější. Pokud jste původně použili Visual Studio 2003 k vývoji a kompilaci vašeho řešení, můžete řešení otevřít v sadě Visual Studio 2010 (a případně novější verze příliš) a použít **kompatibilita projektu** dialogové okno Převést řešení a soubory projektu z formátů používaných sadou Visual Studio 2003 do formátu Microsoft Build Engine (MSBuild)

Bez ohledu na to, zda upřednostňujete rekompilaci nebo změnu cílové aplikace musíte určit, jestli bude vaše aplikace ovlivněna změnami zavedenými v novějších verzích rozhraní .NET Framework. Tyto změny jsou dvou typů:

- Rozbíjející změny, ke kterým došlo mezi .NET Framework 1.1 a novějších verzích rozhraní .NET Framework.

- Typy a členy typů, které jsou označené jako zastaralé nebo zastaralé mezi .NET Framework 1.1 a novějších verzích rozhraní .NET Framework.

Zda změnit cíl aplikace nebo ji znovu zkompilovat, měli byste zkontrolovat nejnovější změny a zastaralé typy a členy pro každou verzi rozhraní .NET Framework, která byla vydána po rozhraní .NET Framework 1.1.

## <a name="breaking-changes"></a>Nejnovější změny

Když dojde ke změně rozdělení, v závislosti na konkrétní změně může být k dispozici alternativní řešení i pro rekompilované aplikace. V některých případech můžete přidat podřízený element pro [ \<runtime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) element konfiguračního souboru aplikace k obnovení předchozího chování. Například následující konfigurační soubor obnovuje řetězec řazení a porovnání chování použité v rozhraní .NET Framework 1.1 a může být použit buď s přesměrovanou nebo překompilovanou aplikací.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Nicméně v některých případech budete muset upravit zdrojový kód a zkompilovat aplikaci znovu.

Chcete-li posoudit dopad možných nejnovějších změn na aplikaci, musíte zkontrolovat následující seznamy změn:

- [Rozbíjející změny v rozhraní .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkId=125263) změny v rozhraní .NET Framework 2.0 SP1 může mít vliv na aplikaci, která cílí na .NET Framework 1.1 dokumentů.

- [Změny v rozhraní .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkID=186989) změny dokumentů mezi verzí rozhraní .NET Framework 3.5 a rozhraní .NET Framework 3.5 SP1.

- [Problémy s migrací rozhraní .NET framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) změny dokumentů mezi verzí rozhraní .NET Framework 3.5 SP1 a rozhraní .NET Framework 4.

## <a name="obsolete-types-and-members"></a>Zastaralé typy a členy

Dopad zastaralých typů a členů se poněkud liší od revidovaných aplikací a rekompilovaných aplikací. Použití zastaralých typů a členů neovlivní přesměrovanou aplikaci, pokud zastaralý typ nebo člen nebyl fyzicky odebrán z příslušného sestavení. Opětovnou kompilací aplikace, která používá zastaralé typy nebo členy, obvykle vytváří kompilátor varování spíše než chybu kompilátoru. V některých případech však dojde k chybě kompilátoru a kód, který používá zastaralý typ nebo člen nebude zkompilován úspěšně. V takovém případě je třeba přepsat zdrojový kód, který vyvolá zastaralý typ nebo člen předtím, než aplikaci znovu zkompilujete. Další informace o zastaralých typů a členů, naleznete v tématu [What's Obsolete in knihovny tříd](../../../docs/framework/whats-new/whats-obsolete.md).

Chcete-li posoudit dopad typů a členů, které jsou zastaralé od verze rozhraní .NET Framework 2.0 SP1, přečtěte si téma [What's Obsolete in knihovny tříd](../../../docs/framework/whats-new/whats-obsolete.md). Zkontrolujte seznam zastaralých typů a členů pro rozhraní .NET Framework 2.0 SP1, .NET Framework 3.5 a rozhraní .NET Framework 4.
