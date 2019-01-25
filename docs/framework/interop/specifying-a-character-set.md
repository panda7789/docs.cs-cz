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
ms.openlocfilehash: 45810390ced8584ea7b37908a9e4af8d3da73f34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549847"
---
# <a name="specifying-a-character-set"></a>Určení sady znaků
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole řídí zařazování řetězce a určuje, jak vyvolání platformy najde názvy funkcí v knihovně DLL. Toto téma popisuje, jak chování.  
  
 Některá rozhraní API exportovat dvě verze funkcí, které přijímají řetězcové argumenty: úzký (ANSI) a celý (Unicode). Rozhraní API systému Win32, zahrnuje následující názvy vstupní bod **MessageBox** funkce:  
  
-   **MessageBoxA**  
  
     Poskytuje 1bajtový ANSI formátování, odlišené "A" připojenou k názvu vstupního bodu. Volání **MessageBoxA** vždy zařazování řetězců v ANSI formátování, což je běžné na platformách Windows 95 a Windows 98.  
  
-   **MessageBoxW**  
  
     Obsahuje formátování 2bajtových znaků Unicode, odlišené "W" připojenou k názvu vstupního bodu. Volání **funkce** vždy zařazovat řetězce ve formátu Unicode, což je běžné na platformách Windows NT, Windows 2000 a Windows XP.  
  
## <a name="string-marshaling-and-name-matching"></a>Zařazování řetězců a shoda názvu  
 **CharSet** pole přijímá následující hodnoty:  
  
 **CharSet.Ansi** (výchozí hodnota)  
  
-   Zařazování řetězců  
  
     Vyvolání platformy marshals řetězců z jejich spravovaných formátu (Unicode) na ANSI formát.  
  
-   Shoda názvu  
  
     Když <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole je **true**, protože je ve výchozím nastavení v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], vyhledá pouze zadaný název vyvolání platformy. Pokud zadáte například **MessageBox**, vyhledá vyvolání platformy **MessageBox** a selže, pokud nemůže najít přesnou kontrolu pravopisu.  
  
     Když **ExactSpelling** pole je **false**, protože je ve výchozím nastavení v jazyce C++ a C#, nejprve vyhledá unmangled alias vyvolání platformy (**MessageBox**), pak bude rozdělený název (**MessageBoxA**) Pokud se nenajde unmangled alias. Všimněte si, že ANSI shoda názvu chování se liší od chování porovnávání název kódování Unicode.  
  
 **CharSet.Unicode**  
  
-   Zařazování řetězců  
  
     Kopie řetězce z jejich spravovaných formátu (Unicode) do Unicode formátu vyvolání platformy.  
  
-   Shoda názvu  
  
     Když **ExactSpelling** pole je **true**, protože je ve výchozím nastavení v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], vyhledá pouze zadaný název vyvolání platformy. Pokud zadáte například **MessageBox**, vyhledá vyvolání platformy **MessageBox** a selže, pokud nemůže najít přesnou kontrolu pravopisu.  
  
     Když **ExactSpelling** pole je **false**, protože je ve výchozím nastavení v jazyce C++ a C#, nejprve vyhledá pozměněný název vyvolání platformy (**funkce**), pak bude unmangled alias (**MessageBox**) Pokud se nenajde pozměnění názvu. Všimněte si, že Unicode shoda názvu chování se liší od chování porovnávání název ANSI.  
  
 **CharSet.Auto**  
  
-   Vyvolání platformy zvolí mezi formáty ANSI a Unicode v době běhu, založené na cílové platformě.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Určení znakové sady v jazyce Visual Basic  
 Následující příklad deklaruje **MessageBox** funkce tři vícekrát, pokaždé, když s jinou znakovou sadu chování. Znakové sady chování v jazyce Visual Basic můžete zadat tak, že přidáte **Ansi**, **Unicode**, nebo **automaticky** – klíčové slovo do příkazu deklarace.  
  
 Pokud vynecháte – klíčové slovo znakové sady, jak je tomu v prvním příkazu deklarace, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole výchozí znakovou sadu ANSI. Druhý a třetí příkazy v příkladu explicitně zadat znakovou sadu s klíčovým slovem.  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
   Declare Function MessageBoxA Lib "user32.dll"(ByVal hWnd As Integer, _  
       ByVal txt As String, ByVal caption As String, _  
       ByVal Typ As Integer) As Integer  
  
   Declare Unicode Function MessageBoxW Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
  
   Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Určení znakové sady v C# a C++  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole identifikuje základní znakovou sadu ANSI nebo Unicode. Znakové sady, které řídí, jak by měly být zařazeny řetězcové argumenty metody. Použijte jednu z následujících forem udávajících znakové sady:  
  
```csharp  
[DllImport("dllname", CharSet=CharSet.Ansi)]  
[DllImport("dllname", CharSet=CharSet.Unicode)]  
[DllImport("dllname", CharSet=CharSet.Auto)]  
```  
  
```cpp  
[DllImport("dllname", CharSet=CharSet::Ansi)]  
[DllImport("dllname", CharSet=CharSet::Unicode)]  
[DllImport("dllname", CharSet=CharSet::Auto)]  
```  
  
 Následující příklad ukazuje tři spravované definice **MessageBox** funkce s atributy k určení sady znaků. V první definici podle jeho vynechání **CharSet** pole výchozí znakovou sadu ANSI.  
  
```csharp  
[DllImport("user32.dll")]  
    public static extern int MessageBoxA(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Unicode)]  
    public static extern int MessageBoxW(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Auto)]  
    public static extern int MessageBox(int hWnd, String text,   
        String caption, uint type);  
```  
  
```cpp  
typedef void* HWND;  
  
//Can use MessageBox or MessageBoxA.  
[DllImport("user32")]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Can use MessageBox or MessageBoxW.  
[DllImport("user32", CharSet=CharSet::Unicode)]  
extern "C" int MessageBoxW(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Must use MessageBox.  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Příklady vyvolání platformy](../../../docs/framework/interop/platform-invoke-examples.md)
- [Zařazování dat s voláním platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
