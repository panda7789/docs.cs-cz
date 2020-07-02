---
ms.openlocfilehash: 72d48d1daa85b6891c122f2fcc5279642253b926
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614550"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Kontrolní součty pracovního postupu se změnily z MD5 na SHA1.

#### <a name="details"></a>Podrobnosti

Pro podporu ladění pomocí sady Visual Studio modul runtime pracovního postupu generuje kontrolní součet pro instanci pracovního postupu pomocí algoritmu hash. V .NET Framework 4.6.2 a dřívějších verzích využívala hodnota hash kontrolního součtu workflowu algoritmus MD5, který způsobil problémy se systémy s podporou standardu FIPS. Počínaje .NET Framework 4,7 je algoritmus SHA1. Pokud váš kód trval tyto kontrolní součty, budou nekompatibilní.

#### <a name="suggestion"></a>Návrh

Pokud váš kód nemůže načíst instance pracovního postupu z důvodu chyby kontrolního součtu, zkuste nastavit `AppContext` přepínač &quot;Switch.System. Activities. UseMD5ForWFDebugger &quot; na hodnotu true. V kódu:

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseMD5ForWFDebugger", true);
```

Nebo v konfiguraci:

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseMD5ForWFDebugger=true" />
  </runtime>
</configuration>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4,7         |
| Typ    | Změna cílení |
