---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616047"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute exportuje jako ObsoleteAttribute i DeprecatedAttribute ve scénářích WinMD

#### <a name="details"></a>Podrobnosti

Když vytváříte knihovnu metadat systému Windows (soubor. winmd), <xref:System.ObsoleteAttribute?displayProperty=fullName> atribut je exportován jako i <xref:System.ObsoleteAttribute?displayProperty=fullName> [Windows. Foundation. DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).

#### <a name="suggestion"></a>Návrh

Opětovná kompilace stávajícího zdrojového kódu, který používá <xref:System.ObsoleteAttribute?displayProperty=fullName> atribut, může generovat upozornění při využívání kódu z C++/CX nebo JavaScript. nedoporučujeme <xref:System.ObsoleteAttribute?displayProperty=fullName> pro kód ve spravovaných sestaveních použít jak oba, tak [Windows. Foundation. DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) , což může vést k upozorněním sestavení.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.5.1       |
| Typ    | Změna cílení |
