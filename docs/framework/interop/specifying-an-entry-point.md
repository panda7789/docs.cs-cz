---
title: Určení vstupního bodu
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: c5f8f735dd3e8c359f88044a532c29303237acc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181313"
---
# <a name="specifying-an-entry-point"></a>Určení vstupního bodu

Vstupní bod určuje umístění funkce v knihovně DLL. Původní název nebo řadový vstupní bod cílové funkce identifikuje v rámci spravovaného projektu funkci napříč hranicemi interoperability. Dále je možné namapovat vstupní bod na jiný název, a tak funkci účinně přejmenovat.  
  
 Následuje seznam možných důvodů pro přejmenování funkce DLL:  
  
- Zamezení používání názvů funkcí rozhraní API, která rozlišují velikost písmen  
  
- Dodržování stávajících standardů pro zadávání názvů  
  
- Přizpůsobení funkcí, které přijímají různé datové typy (deklarací několika verzí stejné funkce knihovny DLL)  
  
- Zjednodušení používání rozhraní API, která obsahují verze ANSI a Unicode  
  
 Toto téma popisuje, jakým způsobem lze přejmenovat funkci knihovny DLL ve spravovaném kódu.  
  
## <a name="renaming-a-function-in-visual-basic"></a>Přejmenování funkce v jazyce Visual Basic  

Visual Basic používá **funkci klíčovéslovo** v <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> **Declare** prohlášení nastavit pole. Následující příklad znázorňuje základní deklaraci.  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
Vstupní bod **messageboxu** můžete nahradit **msgbox** zahrnutím klíčového slova **Alias** do definice, jak je znázorněno v následujícím příkladu. V obou příkladech klíčové slovo **Auto** eliminuje potřebu určit verzi znakové sady vstupního bodu. Další informace o výběru znakové sady naleznete v [tématu Určení znakové sady](specifying-a-character-set.md).  
  
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
 K určení funkce knihovny DLL pomocí názvu nebo řádu můžete použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> . Pokud je název funkce v definici metody stejný jako vstupní bod v dll, není třeba explicitně identifikovat funkci s **entrypoint** pole. Jinak lze pro určení názvu nebo řádu použít jednu z těchto podob atributů:  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 Je nutné poznamenat, že pro řád je třeba použít předponu v podobě znaku libry (#).  
  
 Následující příklad ukazuje, jak nahradit **MessageBoxA** **msgBox** v kódu pomocí **entrypoint** pole.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
- [Příklady vyvolání platformy](platform-invoke-examples.md)
- [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)
