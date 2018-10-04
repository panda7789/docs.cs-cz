---
title: Migrace z rozhraní .NET Framework 1.1
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 546bb50531e62abafe8ab016e2c138ffa9d8720d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778364"
---
# <a name="migrating-from-the-net-framework-11"></a>Migrace z rozhraní .NET Framework 1.1

[!INCLUDE[win7](../../../includes/win7-md.md)] a novějších verzích operačního systému Windows nepodporuje [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)]. V důsledku toho se aplikace, jejichž cílem [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] nebudou spuštěny bez úprav na [!INCLUDE[win7](../../../includes/win7-md.md)] nebo novější verze operačního systému. Toto téma popisuje kroky potřebné ke spuštění aplikace, který cílí [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] pod [!INCLUDE[win7](../../../includes/win7-md.md)] a novějšími verzemi operačního systému Windows. Další informace o [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)] a [!INCLUDE[win8](../../../includes/win8-md.md)], naleznete v tématu [spouštění aplikací .NET Framework v systému Windows 8 a novější verze 1.1](../../../docs/framework/install/run-net-framework-1-1-apps.md).

## <a name="retargeting-or-recompiling"></a>Přeorientovat nebo rekompilovat

Existují dva způsoby, jak získat aplikace, která se zkompilovala pomocí [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] ke spuštění na [!INCLUDE[win7](../../../includes/win7-md.md)] nebo novějším operačním systémem Windows:

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

- Rozbíjející změny, ke kterým došlo mezi [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] a novějších verzích rozhraní .NET Framework.

- Typy a členy typů, které jsou označené jako zastaralé nebo zastaralé mezi [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] a novějších verzích rozhraní .NET Framework.

Zda změnit cíl aplikace nebo ji znovu zkompilovat, byste měli zkontrolovat nejnovější změny a zastaralé typy a členy pro každou verzi rozhraní .NET Framework, která byla vydána po [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].

## <a name="breaking-changes"></a>Nejnovější změny

Když dojde ke změně rozdělení, v závislosti na konkrétní změně může být k dispozici alternativní řešení i pro rekompilované aplikace. V některých případech můžete přidat podřízený element pro [ \<runtime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) element konfiguračního souboru aplikace k obnovení předchozího chování. Například následující konfigurační soubor obnovuje řazení a porovnávání chování řetězců používané [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] a může být použit buď s přesměrovanou nebo překompilovanou aplikací.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Nicméně v některých případech budete muset upravit zdrojový kód a zkompilovat aplikaci znovu.

Chcete-li posoudit dopad možných nejnovějších změn na aplikaci, musíte zkontrolovat následující seznamy změn:

- [Rozbíjející změny v rozhraní .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkId=125263) změny dokumentů v [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] , jež mohou ovlivnit aplikaci zaměřenou [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].

- [Změny v rozhraní .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkID=186989) změny dokumentů mezi verzí [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] a [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)].

- [Problémy s migrací rozhraní .NET framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) změny dokumentů mezi verzí [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] a [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].

## <a name="obsolete-types-and-members"></a>Zastaralé typy a členy

Dopad zastaralých typů a členů se poněkud liší od revidovaných aplikací a rekompilovaných aplikací. Použití zastaralých typů a členů neovlivní přesměrovanou aplikaci, pokud zastaralý typ nebo člen nebyl fyzicky odebrán z příslušného sestavení. Opětovnou kompilací aplikace, která používá zastaralé typy nebo členy, obvykle vytváří kompilátor varování spíše než chybu kompilátoru. V některých případech však dojde k chybě kompilátoru a kód, který používá zastaralý typ nebo člen nebude zkompilován úspěšně. V takovém případě je třeba přepsat zdrojový kód, který vyvolá zastaralý typ nebo člen předtím, než aplikaci znovu zkompilujete. Další informace o zastaralých typů a členů, naleznete v tématu [What's Obsolete in knihovny tříd](../../../docs/framework/whats-new/whats-obsolete.md).

Chcete-li posoudit dopad typů a členů, které již nejsou používání od vydání [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], naleznete v tématu [What's Obsolete in knihovny tříd](../../../docs/framework/whats-new/whats-obsolete.md). Zkontrolujte seznam zastaralých typů a členů pro [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]a [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].