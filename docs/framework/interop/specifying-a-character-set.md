---
title: Určení sady znaků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ee68d0da3b7f23d4de0192da076ef6f71d6d222
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051637"
---
# <a name="specifying-a-character-set"></a>Určení sady znaků
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole řídí zařazování řetězců a určuje, jakým způsobem vyvolání platformy nalezne názvy funkcí v knihovně DLL. V tomto tématu jsou popsána obě chování.  
  
 Některá rozhraní API exportují dvě verze funkcí, které přijímají argumenty pro řetězce: úzká (ANSI) a roztažitelné (Unicode). Rozhraní Windows API obsahuje například následující názvy vstupních bodů pro funkci **MessageBox** :  
  
- **MessageBoxA**  
  
     Poskytuje 1 bajtové formátování znakové sady ANSI rozlišené znakem "A", který je připojený k názvu vstupního bodu. Volání **MessageBox** . vždycky zařazování řetězců ve formátu ANSI.  
  
- **MessageBoxW**  
  
     Poskytuje 2 bajtové formátování znaků znakové sady Unicode, které se odlišuje "W" připojením k názvu vstupního bodu. Volání **MessageBoxW** vždy zařazování řetězců ve formátu Unicode.  
  
## <a name="string-marshaling-and-name-matching"></a>Zařazování řetězců a shoda názvů  
 `CharSet` Pole přijímá následující hodnoty:  
  
 <xref:System.Runtime.InteropServices.CharSet.Ansi>(výchozí hodnota)  
  
- Zařazování řetězců  
  
     Volání platformy zařazování řetězců z jejich spravovaného formátu (Unicode) do formátu ANSI.  
  
- Shoda názvů  
  
     Když je <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> `true`pole ve výchozím nastavení v Visual Basic, vyvolá vyhledá platforma pouze zadaný název. Například pokud zadáte **MessageBox**, vyvolá volání metody **MessageBox** a dojde k chybě, když nemůže najít přesný pravopis.  
  
     C++ C#Když je `ExactSpelling` `false`pole ve výchozím nastavení v a, vyvolá volání metody jako první (MessageBox) nezměněný alias (MessageBox) a pak pozměněný název (MessageBox), pokud nebyl nalezen nezměněný alias. Všimněte si, že chování při shodě názvů ANSI se liší od chování při shodě názvů Unicode.  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- Zařazování řetězců  
  
     Vyvolání platformy kopíruje řetězce z spravovaného formátu (Unicode) do formátu Unicode.  
  
- Shoda názvů  
  
     Když je `ExactSpelling` `true`pole ve výchozím nastavení v Visual Basic, vyvolá vyhledá platforma pouze zadaný název. Například pokud zadáte **MessageBox**, vyvolá volání metody **MessageBox** a dojde k chybě, pokud nemůže najít přesný pravopis.  
  
     C++ C#Když je `ExactSpelling` `false`pole ve výchozím nastavení v a, vyvolá volání metody jako první (MessageBoxW) a pak nezměněný alias (MessageBox), pokud nebyl nalezen pozměněný název. Všimněte si, že chování při shodě názvů Unicode se liší od chování při shodě názvů ANSI.  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- Volání platformy se v době běhu volí mezi formáty ANSI a Unicode, a to na základě cílové platformy.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Určení znakové sady v Visual Basic  
 Následující příklad deklaruje funkci **MessageBox** třikrát, a to pokaždé, když se liší chování znakových sad. Můžete určit chování znakových sad v Visual Basic přidáním klíčového slova **ANSI**, **Unicode**nebo **auto** do příkazu deklarace.  
  
 Vynecháte-li klíčové slovo sady znaků, jak je provedeno v prvním příkazu deklarace, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> je pole standardně znakovou sadou ANSI. Druhý a třetí příkaz v příkladu explicitně specifikují znakovou sadu s klíčovým slovem.  
  
```vb
Friend Class NativeMethods
    Friend Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Určení znakové sady v C# aC++  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole určuje základní znakovou sadu jako ANSI nebo Unicode. Znaková sada určuje, jak by měly být zařazeny řetězcové argumenty metody. K označení znakové sady použijte jednu z následujících forem:  
  
```csharp
[DllImport("DllName", CharSet = CharSet.Ansi)]
[DllImport("DllName", CharSet = CharSet.Unicode)]
[DllImport("DllName", CharSet = CharSet.Auto)]
```
  
```cpp
[DllImport("DllName", CharSet = CharSet::Ansi)]
[DllImport("DllName", CharSet = CharSet::Unicode)]
[DllImport("DllName", CharSet = CharSet::Auto)]
```
  
 Následující příklad ukazuje tři spravované definice funkce **MessageBox** s atributem pro určení znakové sady. V první definici po vynechání `CharSet` pole je ve výchozím nastavení znaková sada ANSI.  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBoxA(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Unicode)]
    internal static extern int MessageBoxW(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```  
  
```cpp
typedef void* HWND;

// Can use MessageBox or MessageBoxA.
[DllImport("user32")]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Can use MessageBox or MessageBoxW.
[DllImport("user32", CharSet = CharSet::Unicode)]
extern "C" int MessageBoxW(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Must use MessageBox.
[DllImport("user32", CharSet = CharSet::Auto)]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
- [Příklady vyvolání platformy](platform-invoke-examples.md)
- [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)
