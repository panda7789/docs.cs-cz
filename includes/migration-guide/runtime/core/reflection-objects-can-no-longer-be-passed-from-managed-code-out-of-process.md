---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621145"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Objekty reflexe již nelze předávat ze spravovaného kódu do mimoprocesových klientů modelu DCOM.

#### <a name="details"></a>Podrobnosti

Objekty reflexe již nelze předávat ze spravovaného kódu pro klienty DCOM mimo procesy. Ovlivněny jsou následující typy:<ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><xref:System.Reflection.MemberInfo?displayProperty=fullName>(a jeho odvozené typy, včetně <xref:System.Reflection.FieldInfo?displayProperty=fullName> , <xref:System.Reflection.MethodInfo?displayProperty=fullName> , <xref:System.Type?displayProperty=fullName> a <xref:System.Reflection.TypeInfo?displayProperty=fullName> )</li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</li></ul>Volání <code>IMarshal</code> pro objekt vrátí <code>E_NOINTERFACE</code> .

#### <a name="suggestion"></a>Návrh

Aktualizace zařazovacího kódu pro práci s objekty bez reflexe

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6|
|Typ|Modul runtime|
