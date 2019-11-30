---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643954"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute byl odebrán z některých typů model Windows Forms.

<xref:System.SerializableAttribute> byla odebrána z některých model Windows Forms tříd, které nemají žádné známé scénáře binární serializace.

#### <a name="change-description"></a>Změnit popis

Následující typy jsou upraveny pomocí <xref:System.SerializableAttribute> v .NET Framework, ale atribut byl odstraněn v rozhraní .NET Core:

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

V minulosti měl tento mechanismus serializace závažné problémy s údržbou a zabezpečením. Udržování `SerializableAttribute` na typech znamená, že tyto typy musí být testovány na změny serializace verze na verzi a potenciálně změny serializace architektury rozhraní. Díky tomu je to obtížnější je rozvíjet tyto typy a může být náročné na údržbu. Tyto typy nemají žádné známé scénáře binární serializace, což minimalizuje dopad odebrání atributu.

Další informace naleznete v tématu [binární serializace](~/docs/standard/serialization/binary-serialization.md).

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
