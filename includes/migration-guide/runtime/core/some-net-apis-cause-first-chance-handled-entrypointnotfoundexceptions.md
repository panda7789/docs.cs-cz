---
ms.openlocfilehash: b23f06ec5b27fbd7976a4b62ba6105c607eaee39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236686"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>První možnost některá rozhraní API pro .NET příčina EntryPointNotFoundExceptions (zpracování)

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, začal malý počet metod rozhraní .NET, vyvolání první příležitosti <xref:System.EntryPointNotFoundException?displayProperty=name>s. Tyto výjimky se zpracovávají v rámci rozhraní .NET Framework, ale může poškodit automatizace testů, který nebyl očekáván první příležitosti výjimky. Tato stejná rozhraní API přerušením, dokud některé scénáře ApiVerifier HighVersionLie je povolená.|
|Doporučení|Upgradem na rozhraní .NET Framework 4.5.1 se lze vyvarovat této chyby. Můžete také aktualizovat automatizace testů tak, že nedojde k narušení na první odpovídající <xref:System.EntryPointNotFoundException?displayProperty=name>s.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|
