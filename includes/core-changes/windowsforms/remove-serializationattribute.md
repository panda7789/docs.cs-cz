---
ms.openlocfilehash: e9d76d5907e7d700fc57117ccb43f8c430c615b0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181798"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute byl odebrán z některých typů model Windows Forms.

<xref:System.SerializableAttribute> Byl odebrán z některých tříd model Windows Forms, které nemají žádné známé scénáře binární serializace.

#### <a name="change-description"></a>Změnit popis

Následující typy jsou upraveny pomocí <xref:System.SerializableAttribute> .NET Framework, ale atribut byl odebrán v rozhraní .NET Core:

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

V minulosti měl tento mechanismus serializace závažné problémy s údržbou a zabezpečením. Údržba `SerializableAttribute` na typech znamená, že tyto typy musí být testovány pro změny serializace verze na verzi a potenciálně změny serializace architektury rozhraní. Díky tomu je to obtížnější je rozvíjet tyto typy a může být náročné na údržbu. Tyto typy nemají žádné známé scénáře binární serializace, což minimalizuje dopad odebrání atributu.

Další informace naleznete v tématu <https://docs.microsoft.com/en-us/dotnet/standard/serialization/binary-serialization>.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Aktualizujte jakýkoli kód, který může záviset na těchto typech označených jako serializovatelný.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádné

<!-- 

### Affected APIs

- Not detectable via API analysis

-->