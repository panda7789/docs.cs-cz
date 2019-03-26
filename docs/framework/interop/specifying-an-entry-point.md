---
title: Určení vstupního bodu
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 787406b1fa7e5beb59ff3f8715c1215a734ed895
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411301"
---
# <a name="specifying-an-entry-point"></a>Určení vstupního bodu
Vstupní bod určuje umístění funkce v knihovně DLL. Původní název nebo řadový vstupní bod cílové funkce identifikuje v rámci spravovaného projektu funkci napříč hranicemi interoperability. Dále je možné namapovat vstupní bod na jiný název, a tak funkci účinně přejmenovat.  
  
 Následuje seznam možných důvodů přejmenování funkce knihovny DLL:  
  
-   Zamezení používání názvů funkcí rozhraní API, která rozlišují velikost písmen  
  
-   Dodržování stávajících standardů pro zadávání názvů  
  
-   Přizpůsobení funkcí, které přijímají různé datové typy (deklarací několika verzí stejné funkce knihovny DLL)  
  
-   Zjednodušení používání rozhraní API, která obsahují verze ANSI a Unicode  
  
 Toto téma popisuje, jakým způsobem lze přejmenovat funkci knihovny DLL ve spravovaném kódu.  
  
## <a name="renaming-a-function-in-visual-basic"></a>Přejmenování funkce v jazyce Visual Basic  
 Jazyk Visual Basic používá **funkce** – klíčové slovo v **Declare** příkaz nastavit <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pole. Následující příklad znázorňuje základní deklaraci.  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 Můžete nahradit **MessageBox** vstupní bod s **MsgBox** zahrnutím **Alias** – klíčové slovo v definici, jak je znázorněno v následujícím příkladu. V obou příkladech **automaticky** – klíčové slovo eliminuje nutnost určit verzi znakové sady vstupního bodu. Další informace o výběru znakové sady naleznete v tématu [určení znakové sady](../../../docs/framework/interop/specifying-a-character-set.md).  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a>Přejmenování funkce v jazyce C# a C++  
 K určení funkce knihovny DLL pomocí názvu nebo řádu můžete použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> . Pokud je název funkce v definici metody stejný jako vstupní bod v knihovně DLL, není nutné explicitně identifikovat funkci pomocí **EntryPoint** pole. Jinak lze pro určení názvu nebo řádu použít jednu z těchto podob atributů:  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 Je nutné poznamenat, že pro řád je třeba použít předponu v podobě znaku libry (#).  
  
 Následující příklad ukazuje, jak nahradit **MessageBoxA** s **MsgBox** ve vašem kódu pomocí **EntryPoint** pole.  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
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
- [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Příklady vyvolání platformy](../../../docs/framework/interop/platform-invoke-examples.md)
- [Zařazování dat s voláním platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
