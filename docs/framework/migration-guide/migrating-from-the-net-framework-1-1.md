---
title: Migrace z rozhraní .NET Framework 1.1
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
ms.openlocfilehash: 11fe9ba36d32a4c9fe363b48f76a8bb2b24f073b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73974972"
---
# <a name="migrate-from-the-net-framework-11"></a>Migrace z rozhraní .NET Framework 1.1

Windows 7 a novější verze operačního systému Windows nepodporují rozhraní .NET Framework 1.1. V důsledku toho aplikace, které se zaměřují na rozhraní .NET Framework 1.1 nebude fungovat bez úprav v systému Windows 7 nebo novější verze operačního systému. Toto téma popisuje kroky potřebné ke spuštění aplikace, která se zaměřuje na rozhraní .NET Framework 1.1 v systému Windows 7 a novějších verzích operačního systému Windows. Další informace o rozhraních .NET Framework 1.1 a Windows 8 naleznete v [tématu Spuštění aplikací rozhraní .NET Framework 1.1 ve Windows 8 a novějších verzích](../install/run-net-framework-1-1-apps.md).

## <a name="retarget-or-recompile"></a>Přesměrovávat nebo znovu zkompilovat

Existují dva způsoby, jak získat aplikaci, která byla zkompilována pomocí rozhraní .NET Framework 1.1 pro spuštění v systému Windows 7 nebo novějším operačním systému Windows:

- Přesměrujte aplikaci tak, aby byla spuštěna v rozhraní .NET Framework 4 a novějších verzích. Opětovné cílení vyžaduje přidání [ \<prvku supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) do konfiguračního souboru aplikace, který umožňuje jeho spuštění v rámci rozhraní .NET Framework 4 a novějších verzí. Takový konfigurační soubor má následující podobu:

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- Překompilujte aplikaci pomocí kompilátoru, který cílí na rozhraní .NET Framework 4 nebo novější verzi. Pokud jste původně použili Visual Studio 2003 k vývoji a kompilaci řešení, můžete otevřít řešení v sadě Visual Studio 2010 (a případně i novější verze) a použít dialogové okno **Kompatibilita projektu** k převodu řešení a souborů projektu z formátů používaných visual studio 2003 do formátu Microsoft Build Engine (MSBuild).

Bez ohledu na to, zda dáváte přednost překompilování nebo přecílení aplikace, je nutné určit, zda je vaše aplikace ovlivněna změnami zavedenými v novějších verzích rozhraní .NET Framework. Tyto změny jsou dvojího druhu:

- Narušující změny, ke kterým došlo mezi rozhraním .NET Framework 1.1 a novějšími verzemi rozhraní .NET Framework.

- Typy a členy typu, které byly označeny jako zastaralé nebo zastaralé mezi rozhraním .NET Framework 1.1 a novějšími verzemi rozhraní .NET Framework.

Bez ohledu na to, zda aplikaci znovu zacílíte nebo ji znovu zkompilujete, měli byste zkontrolovat narušující změny i zastaralé typy a členy pro každou verzi rozhraní .NET Framework, která byla vydána po rozhraní .NET Framework 1.1.

## <a name="breaking-changes"></a>Změny způsobující chyby

Dojde-li k narušující změně, v závislosti na konkrétní změně může být k dispozici řešení pro retargeted a překompilované aplikace. V některých případech můžete přidat podřízený prvek do [ \<runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) prvek konfiguračního souboru aplikace k obnovení předchozího chování. Například následující konfigurační soubor obnoví chování řazení a porovnávání řetězců použité v rozhraní .NET Framework 1.1 a lze jej použít buď s retargeted nebo překompilované aplikace.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

V některých případech však bude pravděpodobně nutné upravit zdrojový kód a znovu zkompilovat aplikaci.

Chcete-li posoudit dopad možných změn na aplikaci, je nutné zkontrolovat následující seznamy změn:

- [Narušující změny v rozhraní .NET Framework 2.0](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10)) dokumentují změny v rozhraní .NET Framework 2.0 SP1, které mohou ovlivnit aplikaci, která cílí na rozhraní .NET Framework 1.1.

- [Změny v dokumentech rozhraní .NET Framework 3.5 SP1](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10)) se mění mezi rozhraními .NET Framework 3.5 a .NET Framework 3.5 SP1.

- [Rozhraní .NET Framework 4 Migrace Problémy](net-framework-4-migration-issues.md) dokumenty dokumenty změny mezi .NET Framework 3.5 SP1 a .NET Framework 4.

## <a name="obsolete-types-and-members"></a>Zastaralé typy a členy

Dopad zastaralé typy a členy je poněkud odlišná pro retargeted aplikace a překompilované aplikace. Použití zastaralých typů a členů nebude mít vliv na retargeted aplikace, pokud zastaralý typ nebo člen byl fyzicky odebrán z jeho sestavení. Rekompilace aplikace, která používá zastaralé typy nebo členy obvykle vytváří upozornění kompilátoru spíše než chyba kompilátoru. V některých případech však vytvoří chybu kompilátoru a kód, který používá zastaralý typ nebo člen nezkompiluje úspěšně. V takovém případě je nutné přepsat zdrojový kód, který volá zastaralý typ nebo člen před překompilováním aplikace. Další informace o zastaralých typech a členech naleznete [v tématu Co je zastaralé v knihovně tříd](../whats-new/whats-obsolete.md).

Chcete-li posoudit dopad typů a členů, které byly zastaralé od vydání rozhraní .NET Framework 2.0 SP1, naleznete [v tématu Co je zastaralé v knihovně tříd](../whats-new/whats-obsolete.md). Prohlédněte si seznamy zastaralých typů a členů pro rozhraní .NET Framework 2.0 SP1, Rozhraní .NET Framework 3.5 a .NET Framework 4.
