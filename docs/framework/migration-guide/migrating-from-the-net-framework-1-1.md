---
title: Migrace z rozhraní .NET Framework 1.1
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
ms.openlocfilehash: 11fe9ba36d32a4c9fe363b48f76a8bb2b24f073b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974972"
---
# <a name="migrate-from-the-net-framework-11"></a>Migrace z .NET Framework 1,1

Windows 7 a novější verze operačního systému Windows nepodporují .NET Framework 1,1. V důsledku toho nebudou aplikace cílené na .NET Framework 1,1 běžet beze změny ve verzích operačního systému Windows 7 nebo novějších. Toto téma popisuje kroky potřebné ke spuštění aplikace, která cílí na .NET Framework 1,1 v systému Windows 7 a novějších verzích operačního systému Windows. Další informace o .NET Framework 1,1 a Windows 8 najdete v tématu [spuštění aplikací .NET Framework 1,1 ve Windows 8 a novějších verzích](../install/run-net-framework-1-1-apps.md).

## <a name="retarget-or-recompile"></a>Změnit cílení nebo překompilovat

Existují dva způsoby, jak získat aplikaci, která byla zkompilována pomocí .NET Framework 1,1 pro spuštění v systému Windows 7 nebo novějším operačním systému Windows:

- Změnit cíl aplikace tak, aby běžela v .NET Framework 4 a novějších verzích. Změna cíle vyžaduje, abyste do konfiguračního souboru aplikace přidali [\<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) elementu, který umožňuje jeho spuštění v rámci .NET Framework 4 a novějších verzí. Takový konfigurační soubor má následující formát:

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- Zkompilujte aplikaci znovu s kompilátorem, který cílí na .NET Framework 4 nebo novější verzi. Pokud jste původně použili sadu Visual Studio 2003 k vývoji a kompilování řešení, můžete otevřít řešení v aplikaci Visual Studio 2010 (a případně i novějších verzích) a použít dialogové okno **Kompatibilita projektu** k převedení řešení a souborů projektu z formáty používané v rámci sady Visual Studio 2003 ve formátu Microsoft Build Engine (MSBuild).

Bez ohledu na to, zda upřednostňujete překompilování nebo změnu cílení aplikace, je nutné určit, zda je aplikace ovlivněna jakýmikoli změnami zavedenými v pozdějších verzích .NET Framework. Tyto změny jsou dvou typů:

- Průlomové změny, ke kterým došlo mezi .NET Framework 1,1 a novějšími verzemi .NET Framework.

- Typy a členy typu, které byly označeny jako zastaralé nebo zastaralé mezi .NET Framework 1,1 a novějšími verzemi .NET Framework.

Bez ohledu na to, zda přecílíte na aplikaci nebo je znovu zkompilujete, byste měli zkontrolovat zásadní změny i zastaralé typy a členy pro každou verzi .NET Framework, která byla vydaná po .NET Framework 1,1.

## <a name="breaking-changes"></a>Změny způsobující chyby

V případě, že dojde k zásadní změně v závislosti na konkrétní změně, může být alternativní řešení k dispozici pro přecílené a znovu kompilované aplikace. V některých případech můžete přidat podřízený element do modulu [runtime\<](../configure-apps/file-schema/startup/supportedruntime-element.md) elementu konfiguračního souboru vaší aplikace k obnovení předchozího chování. Například následující konfigurační soubor obnoví řazení řetězců a chování porovnávání používané v .NET Framework 1,1 a lze je použít buď s cílovou nebo znovu zkompilovanou aplikací.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

V některých případech však může být nutné upravit zdrojový kód a znovu zkompilovat aplikaci.

Chcete-li posoudit dopad možných nejnovějších změn v aplikaci, je nutné zkontrolovat následující seznamy změn:

- Zásadní [změny v .NET Framework 2,0](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10)) mění dokumenty v .NET Framework 2,0 SP1, které mohou ovlivnit aplikaci, která cílí na .NET Framework 1,1.

- [Změny v .NET Framework 3,5 SP1 mění v](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10)) dokumentu .NET Framework 3,5 a .NET Framework 3,5 SP1.

- [.NET Framework 4 problémy s migrací](net-framework-4-migration-issues.md) mění dokumenty mezi .NET Framework 3,5 SP1 a .NET Framework 4.

## <a name="obsolete-types-and-members"></a>Zastaralé typy a členové

Dopad zastaralých typů a členů se trochu liší pro změny cílených aplikací a znovu kompilovaných aplikací. Použití zastaralých typů a členů nebude mít vliv na přecílenou aplikaci, pokud zastaralý typ nebo člen nebyl fyzicky odebrán ze svého sestavení. Opětovná kompilace aplikace, která používá zastaralé typy nebo členy, obvykle generuje upozornění kompilátoru, nikoli chybu kompilátoru. V některých případech však vyvolá chybu kompilátoru a kód, který používá zastaralý typ nebo člen, není zkompilován úspěšně. V takovém případě musíte před opětovnou kompilací aplikace přepsat zdrojový kód, který volá zastaralý typ nebo člen. Další informace o zastaralých typech a členech naleznete [v tématu Co je zastaralé v knihovně tříd](../whats-new/whats-obsolete.md).

Chcete-li posoudit dopad typů a členů, které byly zastaralé od vydání .NET Framework 2,0 SP1, přečtěte si téma [co je zastaralé v knihovně tříd](../whats-new/whats-obsolete.md). Zkontrolujte seznam zastaralých typů a členů pro .NET Framework 2,0 SP1, .NET Framework 3,5 a .NET Framework 4.
