---
ms.openlocfilehash: e128bdb5735b3e4844356ad4807cc092f6f2b105
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062419"
---
### <a name="no-aw-suffix-probing-on-non-windows-platforms"></a>Žádná přípona A/W na platformách jiných než Windows

Rozhraní .NET Runtime již nepřidává `A` `W` příponu ani pro export názvů funkcí během zjišťování pro volání nespravovaných platforem na jiných platformách než Windows.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 4

#### <a name="change-description"></a>Popis změny

[Systém Windows má konvenci](/windows/win32/intl/conventions-for-function-prototypes) pro přidání `A` `W` přípony nebo pro Windows SDK názvů funkcí, které odpovídají znakové stránce systému Windows a verzím Unicode v uvedeném pořadí.

V předchozích verzích rozhraní .NET `A` `W` během zjišťování exportu pro volání nespravovaného objektu *na všech platformách*přidá do názvu exportu příponu nebo (CoreCLR).

V rozhraní .NET 5,0 a novějších verzích `A` `W` je přípona nebo přidána do názvu exportu během zjišťování exportu *pouze v systému Windows*. Na platformách UNIX není přípona přidána. Sémantika obou běhových prostředí v platformě Windows zůstane beze změny.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna byla provedena za účelem zjednodušení zjišťování pro různé platformy. Má se za to, že by nedocházelo k tomu, že platformy jiné než Windows neobsahují tuto sémantickou sémantiku.

#### <a name="recommended-action"></a>Doporučená akce

Chcete-li tuto změnu zmírnit, můžete ručně přidat požadovanou příponu na platformy jiných výrobců než Windows. Příklad:

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

#### <a name="category"></a>Kategorie

Zprostředkovatel komunikace

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

-->
