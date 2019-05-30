---
ms.openlocfilehash: 335647f899c79eff22e313fa40b2e2a73e7cfff0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379646"
---
### <a name="wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serializuje Expressions.Literal\<T > DateTimes odlišně, teď (přeruší vlastní analyzátory XAML)

|   |   |
|---|---|
|Podrobnosti|Přidružené <xref:System.Windows.Markup.ValueSerializer> převede objekt <xref:System.DateTime?displayProperty=name> nebo <xref:System.DateTimeOffset?displayProperty=name> jehož druhý objekt a <xref:System.DateTime.Millisecond?displayProperty=name> komponenty jsou nenulové a (pro <xref:System.DateTime?displayProperty=name> hodnotu) jehož <xref:System.DateTime.Kind> vlastnost není property – element Syntaxe namísto řetězce. Tato změna umožňuje <xref:System.DateTime?displayProperty=name> a <xref:System.DateTimeOffset?displayProperty=name> hodnoty round-trip. Vlastní analyzátory XAML, které předpokládají, že vstup XAML je v syntaxi atributu, nebudou pracovat správně.|
|Doporučení|Tato změna umožňuje <xref:System.DateTime?displayProperty=name> a <xref:System.DateTimeOffset?displayProperty=name> hodnoty round-trip. Vlastní analyzátory XAML, které předpokládají, že vstup XAML je v syntaxi atributu, nebudou pracovat správně.|
|Scope|Edge|
|Version|4.5|
|Type|Modul runtime|
