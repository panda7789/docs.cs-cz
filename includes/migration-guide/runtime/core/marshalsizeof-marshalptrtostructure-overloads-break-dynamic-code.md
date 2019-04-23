---
ms.openlocfilehash: 6309cead46dff44ff6360bac9b31666f875be210
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981527"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal.SizeOf a přetížení Marshal.PtrToStructure přerušit dynamický kód

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5.1, dynamické vazby na metody <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, nebo <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (přes Windows PowerShell, IronPython, nebo C# dynamické klíčové slovo pro Příklad) může vést k <code>MethodInvocationExceptions</code> vzhledem k tomu, že byly přidány nové přetížení z těchto metod, které můžou být nejednoznačná skriptovacích strojů.|
|Doporučení|Aktualizujte skripty, které jasně označují, které přetížení by mělo být použito. To může, obvykle provádí přetypováním explicitní parametry typu metody jako <xref:System.Type>. Zobrazit [tento odkaz](https://support.microsoft.com/kb/2909958/) další podrobnosti a příklady, jak chcete-li vyřešit tento problém.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Type|Modul runtime|
