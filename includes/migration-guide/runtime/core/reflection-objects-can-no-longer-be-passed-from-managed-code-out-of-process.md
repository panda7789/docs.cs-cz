---
ms.openlocfilehash: d00f86c492a7d32344b1067a48c8e53aa2a43426
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761278"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Objekty reflexe lze předat už ze spravovaného kódu DCOM klientům mimo proces

|   |   |
|---|---|
|Podrobnosti|Objekty reflexe je už předat ze spravovaného kódu DCOM klientům mimo proces. Jsou ovlivněny následující typy:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (a jeho odvozeným typům, včetně <xref:System.Reflection.FieldInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, <xref:System.Type?displayProperty=name>, a <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Volání <code>IMarshal</code> pro vrácení objektu <code>E_NOINTERFACE</code>.|
|Doporučení|Aktualizace kódu zařazování pro práci s objekty bez reflexe|
|Rozsah|Vedlejší|
|Version|4.6|
|Type|Modul runtime|

