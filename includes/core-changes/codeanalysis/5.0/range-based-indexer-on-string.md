---
ms.openlocfilehash: 87f9cc03f334233ef286abd11e6f5ff82d7988c2
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811341"
---
### <a name="ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer"></a>CA1831 místo indexeru založeného na rozsahu použijte AsSpan nebo AsMemory.

Ve výchozím nastavení je ve výchozím nastavení povolený [CA1831](/visualstudio/code-quality/ca1831) pravidla analyzátoru kódu .NET Počínaje rozhraním .NET 5,0. Vytvoří upozornění sestavení pro jakýkoliv kód <xref:System.Range> , kde je indexer založený na řetězci použit, ale nebyla určena žádná kopie.

#### <a name="change-description"></a>Popis změny

Počínaje platformou .NET 5,0 obsahuje sada .NET SDK [analyzátory zdrojového kódu .NET](../../../../docs/fundamentals/productivity/code-analysis.md). Některé z těchto pravidel je ve výchozím nastavení povolené, včetně [CA1831](/visualstudio/code-quality/ca1831). Pokud váš projekt obsahuje kód, který porušuje toto pravidlo a je nakonfigurován tak, aby pocházel s upozorněními jako s chybami, může tato změna poškodit vaše sestavení.

CA1831 pravidla vyhledá instance, ve kterých <xref:System.Range> je indexer založený na řetězci použit, ale nebyla určena žádná kopie. Pokud <xref:System.Range> je indexer založený na řetězci použit přímo na řetězec pro vytvoření implicitního přetypování, pak je vytvořena nepotřebná kopie požadované části řetězce. Příklad:

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

CA1831 navrhuje použití <xref:System.Range> indexeru založeného na *rozsahu* řetězce místo toho. Příklad:

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 8

#### <a name="recommended-action"></a>Doporučená akce

- Chcete-li opravit kód a vyhnout se zbytečnému přidělení, zavolejte <xref:System.MemoryExtensions.AsSpan(System.String)> nebo <xref:System.MemoryExtensions.AsMemory(System.String)> před použitím <xref:System.Range> indexeru založeného na. Příklad:

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- Pokud nechcete změnit kód, můžete pravidlo zakázat nastavením jeho závažnosti na `suggestion` nebo `none` . Další informace naleznete v tématu [Configure Code Analysis Rules](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).

- Pro úplné vypnutí analýzy kódu nastavte `EnableNETAnalyzers` na hodnotu `false` v souboru projektu. Další informace najdete v tématu [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).

#### <a name="category"></a>Kategorie

Analýza kódu

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Range?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Range`

-->
