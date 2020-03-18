---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116347"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft.VisualBasic.Constants.vbNewLine je zastaralý

Konstanta <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> je [ \[označena jako zastaralá\] ](xref:System.ObsoleteAttribute) počínaje rozhraním .NET Core 3.0 Preview 8.

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 8

#### <a name="change-description"></a>Popis změny

Počínaje rozhraním .NET Core 3.0 Preview 8 byl <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> atribut [Obsolete](xref:System.ObsoleteAttribute) použit na konstantu. Použití konstanty vytváří upozornění kompilátoru. V rozhraní .NET Framework a předchozích verzích rozhraní .NET Core nebyla označena jako zastaralá.

Tato změna byla provedena pro podporu jazyka Visual Basic jako jazyk pro vývoj více platforem. Konstanta <xref:Microsoft.VisualBasic.Constants.vbNewLine> je `\r\n`ekvivalentní , pořadí znaků nového řádku v systému Windows. V systémech založených na Unixu `\n`je znak nového řádku .

#### <a name="recommended-action"></a>Doporučená akce

[Zpráva o atributu Zastaralé](xref:System.ObsoleteAttribute) pro <xref:Microsoft.VisualBasic.Constants.vbNewLine> obsahuje následující doporučení:

Pro vrácení vozíku a <xref:Microsoft.VisualBasic.Constants.vbCrLf>posuv řádku použijte . Pro novou linku aktuální platformy <xref:System.Environment.NewLine?displayProperty=nameWithType>použijte .

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
