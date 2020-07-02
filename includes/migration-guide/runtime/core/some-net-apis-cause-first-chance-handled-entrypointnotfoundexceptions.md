---
ms.openlocfilehash: ed526095459a48aa37b585dfed79cc12b9fb9e56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622041"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>Některá rozhraní API .NET způsobují první šanci (zpracovává) EntryPointNotFoundExceptions

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,5, malý počet metod .NET začal s prvními možnostmi aktivována <xref:System.EntryPointNotFoundException?displayProperty=fullName> . Tyto výjimky byly zpracovány v rámci .NET Framework, ale mohly by poškodit automatizaci testu, která neočekávala první pravděpodobnost výjimek. Tato stejná rozhraní API přeruší některé scénáře ApiVerifier, pokud je povolená HighVersionLie.

#### <a name="suggestion"></a>Návrh

Tato chyba se může vyhnout upgradem na .NET Framework 4.5.1. Alternativně lze automatizaci testů aktualizovat na nepřerušení při první popravděpodobném <xref:System.EntryPointNotFoundException?displayProperty=fullName> .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)></li></ul>|
