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
ms.openlocfilehash: e0f732eb7b6ee77cb6b16130fc41655922127c3b
ms.sourcegitcommit: 56ac30a336668124cb7d95d8ace16bd985875147
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469686"
---
# <a name="specifying-a-character-set"></a>Určení sady znaků
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole řídí zařazování řetězce a určuje, jak vyvolání platformy najde názvy funkcí v knihovně DLL. Toto téma popisuje, jak chování.  
  
 Některá rozhraní API exportovat dvě verze funkcí, které přijímají řetězcové argumenty: úzký (ANSI) a celý (Unicode). Rozhraní Windows API, například zahrnuje následující názvy vstupní bod **MessageBox** funkce:  
  
- **MessageBoxA**  
  
     Poskytuje 1bajtový ANSI formátování, odlišené "A" připojenou k názvu vstupního bodu. Volání **MessageBoxA** vždy zařazovat řetězce ve formátu ANSI.  
  
- **MessageBoxW**  
  
     Obsahuje formátování 2bajtových znaků Unicode, odlišené "W" připojenou k názvu vstupního bodu. Volání **funkce** vždy zařazovat řetězce ve formátu Unicode.  
  
## <a name="string-marshaling-and-name-matching"></a>Zařazování řetězců a shoda názvu  
 `CharSet` Pole přijímá následující hodnoty:  
  
 <xref:System.Runtime.InteropServices.CharSet.Ansi> (výchozí hodnota)  
  
- Zařazování řetězců  
  
     Vyvolání platformy marshals řetězců z jejich spravovaných formátu (Unicode) na ANSI formát.  
  
- Shoda názvu  
  
     Když <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole je `true`, protože je ve výchozím nastavení v jazyce Visual Basic, vyvolání platformy vyhledá pouze zadaný název. Pokud zadáte například **MessageBox**, vyhledá vyvolání platformy **MessageBox** a selže, pokud nemůže najít přesnou kontrolu pravopisu.  
  
     Když `ExactSpelling` pole je `false`, protože je ve výchozím nastavení v jazyce C++ a C#, nejprve hledá unmangled alias vyvolání platformy (**MessageBox**), pak pozměněný název (**MessageBoxA**) Pokud se nenajde unmangled alias. Všimněte si, že ANSI shoda názvu chování se liší od chování porovnávání název kódování Unicode.  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- Zařazování řetězců  
  
     Kopie řetězce z jejich spravovaných formátu (Unicode) do Unicode formátu vyvolání platformy.  
  
- Shoda názvu  
  
     Když `ExactSpelling` pole je `true`, protože je ve výchozím nastavení v jazyce Visual Basic, vyvolání platformy vyhledá pouze zadaný název. Pokud zadáte například **MessageBox**, vyhledá vyvolání platformy **MessageBox** a selže, pokud nemůže najít přesnou kontrolu pravopisu.  
  
     Když `ExactSpelling` pole je `false`, protože je ve výchozím nastavení v jazyce C++ a C#, nejprve vyhledá pozměněný název vyvolání platformy (**funkce**), pak unmangled alias (**MessageBox**) Pokud se nenajde pozměnění názvu. Všimněte si, že Unicode shoda názvu chování se liší od chování porovnávání název ANSI.  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- Vyvolání platformy zvolí mezi formáty ANSI a Unicode v době běhu, založené na cílové platformě.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Určení znakové sady v jazyce Visual Basic  
 Následující příklad deklaruje **MessageBox** funkce tři vícekrát, pokaždé, když s jinou znakovou sadu chování. Znakové sady chování v jazyce Visual Basic můžete zadat tak, že přidáte **Ansi**, **Unicode**, nebo **automaticky** – klíčové slovo do příkazu deklarace.  
  
 Pokud vynecháte – klíčové slovo znakové sady, jak je tomu v prvním příkazu deklarace, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole výchozí znakovou sadu ANSI. Druhý a třetí příkazy v příkladu explicitně zadat znakovou sadu s klíčovým slovem.  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Určení znakové sady v C# a C++  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole identifikuje základní znakovou sadu ANSI nebo Unicode. Znakové sady, které řídí, jak by měly být zařazeny řetězcové argumenty metody. Použijte jednu z následujících forem udávajících znakové sady:  
  
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
  
 Následující příklad ukazuje tři spravované definice **MessageBox** funkce s atributy k určení sady znaků. V první definici podle jeho vynechání `CharSet` pole výchozí znakovou sadu ANSI.  
  
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
- [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Příklady vyvolání platformy](../../../docs/framework/interop/platform-invoke-examples.md)
- [Zařazování dat s voláním platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
