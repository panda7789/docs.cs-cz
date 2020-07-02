---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619987"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshaling. SizeOf a Marshal. PtrToStructure přetížení dynamického kódu

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.5.1, dynamicky navázání na metody,,,, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601> <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> , nebo <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (například prostřednictvím prostředí Windows PowerShell, ironpythonu nebo dynamické klíčové slovo C#) může mít za následek <code>MethodInvocationExceptions</code> to, že se přidala nová přetížení těchto metod, která můžou být nejednoznačná pro skriptovací stroje.

#### <a name="suggestion"></a>Návrh

Aktualizujte skripty, aby jasně označovaly, které přetížení by mělo být použito. To se obvykle může provést explicitním přetypováním parametrů typu metody jako <xref:System.Type> . Další podrobnosti a příklady, jak tento problém vyřešit, najdete v [tomto odkazu](https://support.microsoft.com/kb/2909958/) .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5.1|
|Typ|Modul runtime|
