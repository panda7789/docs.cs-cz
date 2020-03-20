---
ms.openlocfilehash: 38c774417fc94fa080bf2b82c04d575e9068cdcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858488"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Reflexní objekty již nelze předat ze spravovaného kódu klientům DCOM mimo proces.

|   |   |
|---|---|
|Podrobnosti|Reflexní objekty již nelze předat ze spravovaného kódu klientům DCOM mimo proces. Ovlivněny jsou následující typy:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name>(a jeho odvozené <xref:System.Reflection.FieldInfo?displayProperty=name>typy, <xref:System.Type?displayProperty=name>včetně <xref:System.Reflection.TypeInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, a )</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Volání <code>IMarshal</code> pro návrat <code>E_NOINTERFACE</code>objektu .|
|Návrh|Aktualizace zařazovacího kódu pro práci s objekty bez odrazu|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|
