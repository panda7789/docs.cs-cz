---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614532"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>Trasování zásobníku získané při použití přenosných soubory PDB nyní obsahuje zdrojový soubor a informace o řádku, pokud je požadováno

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.7.2, trasování zásobníku získané při použití přenosných soubory PDB zahrnují zdrojový soubor a informace o řádku, pokud je to požadováno. Ve verzích starších než .NET Framework 4.7.2 nebude při použití přenosného soubory PDB k dispozici informace o zdrojovém souboru a řádku, i když je výslovně požadováno.

#### <a name="suggestion"></a>Návrh

Pro aplikace cílené na .NET Framework 4.7.2 můžete odhlásit zdrojový soubor a informace o řádku při použití přenosných soubory PDB, pokud to není žádoucí, a to tak, že do `<runtime>` části souboru přidáte následující `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

Pro aplikace, které cílí na starší verze .NET Framework, ale běží na .NET Framework 4.7.2 nebo novějším, můžete při používání přenosných soubory PDB použít následující informace ke zdrojovému souboru a řádku, a to přidáním následujícího do `<runtime>` části `app.config` souboru:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
