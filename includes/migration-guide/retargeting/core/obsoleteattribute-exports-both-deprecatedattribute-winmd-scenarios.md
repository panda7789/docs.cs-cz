---
ms.openlocfilehash: e8c48c4b1031813ce62f576e5bf1f94c082dfe4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088469"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute exportuje jako ObsoleteAttribute a DeprecatedAttribute ve scénářích WinMD

|   |   |
|---|---|
|Podrobnosti|Při vytváření knihovny metadat Windows (soubor winmd), <xref:System.ObsoleteAttribute?displayProperty=name> atribut se exportují jako <xref:System.ObsoleteAttribute?displayProperty=name> a [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).|
|Doporučení|Rekompilace existující zdrojový kód, který používá <xref:System.ObsoleteAttribute?displayProperty=name> atribut může generovat upozornění při využívání, že kód z C++/CX nebo JavaScript.We nedoporučujeme použití obou <xref:System.ObsoleteAttribute?displayProperty=name> a [ Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) kód ve spravovaných sestavení; může dojít v upozorněních sestavení.|
|Rozsah|Edge|
|Version|4.5.1|
|Type|Změna cílení|
