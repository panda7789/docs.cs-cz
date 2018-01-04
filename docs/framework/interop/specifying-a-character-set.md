---
title: "Určení sady znaků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afb2ae519b4a3d52c590f050ba728286898373ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-a-character-set"></a>Určení sady znaků
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole řídí řetězec zařazování a určuje, jak vyvolání platformy najde názvy funkcí v knihovně DLL. Toto téma popisuje, jak chování.  
  
 Některé rozhraní API exportovat dvě verze funkcí, které přijímají argumenty řetězce: úzké (ANSI) a celou (Unicode). Rozhraní API Win32 pro instanci zahrnuje následující názvy vstupní bod **MessageBox** funkce:  
  
-   **MessageBoxA**  
  
     Poskytuje 1bajtový znak ANSI formátování, rozlišené "A" připojeným k názvu vstupního bodu. Volání **MessageBoxA** vždy zařazování řetězců v ANSI formátu, jako je běžné na platformách systému Windows 95 a Windows 98.  
  
-   **Funkce**  
  
     Poskytuje formátování 2bajtová znaků Unicode, rozlišené "W" připojeným k názvu vstupního bodu. Volání **funkce** vždy zařazování řetězce ve formátu Unicode, jako je běžné na platformách systému Windows NT, Windows 2000 a Windows XP.  
  
## <a name="string-marshaling-and-name-matching"></a>Zařazování řetězců a odpovídající název  
 **CharSet** pole přijímá následující hodnoty:  
  
 **CharSet.Ansi** (výchozí hodnota)  
  
-   Řetězec zařazování  
  
     Vyvolání platformy marshals řetězců z jejich spravovaných formátu (Unicode) do formátu ANSI.  
  
-   S odpovídajícím názvem  
  
     Když <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole je **true**, protože je ve výchozím nastavení v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], hledání pouze pro zadaný název vyvolání platformy. Pokud zadáte například **MessageBox**, hledá vyvolání platformy **MessageBox** a selže, když nemůže najít přesnou pravopis.  
  
     Když **ExactSpelling** pole je **false**, protože je ve výchozím nastavení v jazyce C++ a C#, vyvolání platformy alias nejprve hledá unmangled (**MessageBox**), pak (pozměnění název **MessageBoxA**) Pokud není nalezena unmangled alias. Všimněte si, že ANSI odpovídajícím názvem chování se liší od chování odpovídajícím názvem kódování Unicode.  
  
 **CharSet.Unicode**  
  
-   Řetězec zařazování  
  
     Vyvolání platformy kopie řetězců z jejich spravovaných formátu (Unicode) do formátu Unicode.  
  
-   S odpovídajícím názvem  
  
     Když **ExactSpelling** pole je **true**, protože je ve výchozím nastavení v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], hledání pouze pro zadaný název vyvolání platformy. Pokud zadáte například **MessageBox**, hledá vyvolání platformy **MessageBox** a selže, pokud nemůže najít přesnou pravopis.  
  
     Když **ExactSpelling** pole je **false**, protože je ve výchozím nastavení v jazyce C++ a C#, vyvolání platformy nejdřív hledá název pozměnění (**funkce**), pak unmangled alias (**MessageBox**) Pokud pozměnění název nebyl nalezen. Všimněte si, že Unicode s odpovídajícím názvem chování se liší od chování odpovídajícím názvem ANSI.  
  
 **CharSet.Auto**  
  
-   Vyvolání platformy zvolí formátech ANSI a Unicode v době běhu podle cílové platformy.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Určení sady znaků v jazyce Visual Basic  
 Následující příklad deklaruje **MessageBox** funkce tři vždy pokaždé, když s jiným chováním znakovou sadu. Můžete určit chování znakové sady v jazyce Visual Basic přidáním **Ansi**, **Unicode**, nebo **automaticky** – klíčové slovo k příkazu deklarace.  
  
 Pokud vynecháte – klíčové slovo znaková sada, jak se provádí v první příkaz deklarace <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole výchozí znakovou sadu ANSI. Druhý a třetí příkazy v příkladu explicitně zadat znakovou sadu s klíčovým slovem.  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Určení sady znaků v jazyce C# a C++  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole identifikuje základní znakovou sadu ANSI nebo Unicode. Ovládací prvky, jak by měl být řetězcové argumenty pro metodu zařazen sada znaků. K označení znaková sada, použijte jednu z následujících podob:  
  
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
  
 Následující příklad ukazuje tři spravované definice **MessageBox** funkce s atributy zadat znakovou sadu. V definici první podle jeho vynechání **CharSet** pole výchozí znakovou sadu ANSI.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Příklady vyvolání platformy](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Zařazování dat s voláním platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
