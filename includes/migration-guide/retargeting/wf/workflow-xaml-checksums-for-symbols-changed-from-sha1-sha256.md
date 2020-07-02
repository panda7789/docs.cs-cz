---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616238"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>Kontrolní součty v jazyce XAML pro symboly změněné ze SHA1 na SHA256

#### <a name="details"></a>Podrobnosti

Pro podporu ladění pomocí sady Visual Studio modul runtime pracovního postupu generuje kontrolní součet pro soubor XAML pracovního postupu pomocí algoritmu hash. V .NET Framework 4.6.2 a dřívějších verzích využívala hodnota hash kontrolního součtu workflowu algoritmus MD5, který způsobil problémy se systémy s podporou standardu FIPS. Počínaje .NET Framework 4,7 se výchozí algoritmus změnil na SHA1. Počínaje .NET Framework 4,8 byl výchozí algoritmus změněn na SHA256.

#### <a name="suggestion"></a>Návrh

Pokud váš kód nemůže načíst instance pracovního postupu nebo najít odpovídající symboly z důvodu chyby kontrolního součtu, zkuste nastavit `AppContext` přepínač "Switch.System". Activities. UseSHA1HashForDebuggerSymbols `true` . V kódu:

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

Nebo v konfiguraci:

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4,8         |
| Typ    | Změna cílení |
