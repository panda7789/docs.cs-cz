---
title: Určení vstupního bodu
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: a55e460f565c33731c5b0b29ab42b8263d3690e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125155"
---
# <a name="specifying-an-entry-point"></a>Určení vstupního bodu

Vstupní bod určuje umístění funkce v knihovně DLL. Původní název nebo řadový vstupní bod cílové funkce identifikuje v rámci spravovaného projektu funkci napříč hranicemi interoperability. Dále je možné namapovat vstupní bod na jiný název, a tak funkci účinně přejmenovat.  
  
 Následuje seznam možných důvodů přejmenování funkce knihovny DLL:  
  
- Zamezení používání názvů funkcí rozhraní API, která rozlišují velikost písmen  
  
- Dodržování stávajících standardů pro zadávání názvů  
  
- Přizpůsobení funkcí, které přijímají různé datové typy (deklarací několika verzí stejné funkce knihovny DLL)  
  
- Zjednodušení používání rozhraní API, která obsahují verze ANSI a Unicode  
  
 Toto téma popisuje, jakým způsobem lze přejmenovat funkci knihovny DLL ve spravovaném kódu.  
  
## <a name="renaming-a-function-in-visual-basic"></a>Přejmenování funkce v jazyce Visual Basic  
 
Visual Basic používá klíčové slovo **Function** v příkazu **Declare** pro nastavení pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>. Následující příklad znázorňuje základní deklaraci.  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
Vstupní bod **MessageBox** můžete nahradit pomocí **OknoSeZprávou** vložením klíčového slova **alias** do definice, jak je znázorněno v následujícím příkladu. V obou příkladech klíčové slovo **auto** eliminuje nutnost zadat verzi znakového sady vstupního bodu. Další informace o výběru znakové sady naleznete v tématu [Určení znakové sady](specifying-a-character-set.md).  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a>Přejmenování funkce v jazyce C# a C++  
 K určení funkce knihovny DLL pomocí názvu nebo řádu můžete použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> . Pokud je název funkce v definici metody stejný jako vstupní bod v knihovně DLL, není nutné explicitně identifikovat funkci s polem **EntryPoint** . Jinak lze pro určení názvu nebo řádu použít jednu z těchto podob atributů:  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 Je nutné poznamenat, že pro řád je třeba použít předponu v podobě znaku libry (#).  
  
 Následující příklad ukazuje, jak nahradit **MessageBox** ' pomocí **OknoSeZprávou** v kódu pomocí pole **EntryPoint** .  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
- [Příklady vyvolání platformy](platform-invoke-examples.md)
- [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)
