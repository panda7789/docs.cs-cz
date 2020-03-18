---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643954"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>Serializovatelný atribut odebraný z některých typů formulářů systému Windows

Byl <xref:System.SerializableAttribute> odebrán z některých tříd windows forms, které nemají žádné známé scénáře binární serializace.

#### <a name="change-description"></a>Popis změny

Následující typy jsou označeny rozhraním <xref:System.SerializableAttribute> in .NET Framework, ale atribut byl odebrán v rozhraní .NET Core:

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

Historicky měl tento serializační mechanismus vážné obavy o údržbu a zabezpečení. Udržování `SerializableAttribute` na typy znamená, že tyto typy musí být testovány pro změny serializace verze k verzi a potenciálně změny serializace architektury na architekturu. To ztěžuje vývoj těchto typů a může být nákladné udržovat. Tyto typy nemají žádné známé scénáře binární serializace, což minimalizuje dopad odebrání atributu.

Další informace naleznete [v tématu Binary serializace](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 9

#### <a name="recommended-action"></a>Doporučená akce

Aktualizujte libovolný kód, který může záviset na těchto typech, které jsou označeny jako serializovatelné.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádný

<!--

### Affected APIs

- Not detectable via API analysis

-->
