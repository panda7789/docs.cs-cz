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
ms.openlocfilehash: 0db1cd8d75b45f6d718168793c873e5867028269
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125176"
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="fd332-102">Určení sady znaků</span><span class="sxs-lookup"><span data-stu-id="fd332-102">Specifying a Character Set</span></span>
<span data-ttu-id="fd332-103"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole řídí zařazování řetězců a určuje, jakým způsobem vyvolání platformy nalezne názvy funkcí v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="fd332-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="fd332-104">V tomto tématu jsou popsána obě chování.</span><span class="sxs-lookup"><span data-stu-id="fd332-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="fd332-105">Některá rozhraní API exportují dvě verze funkcí, které přijímají argumenty pro řetězce: úzká (ANSI) a roztažitelné (Unicode).</span><span class="sxs-lookup"><span data-stu-id="fd332-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="fd332-106">Rozhraní Windows API obsahuje například následující názvy vstupních bodů pro funkci **MessageBox** :</span><span class="sxs-lookup"><span data-stu-id="fd332-106">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="fd332-107">**MessageBox**</span><span class="sxs-lookup"><span data-stu-id="fd332-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="fd332-108">Poskytuje 1 bajtové formátování znakové sady ANSI rozlišené znakem "A", který je připojený k názvu vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="fd332-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="fd332-109">Volání **MessageBox** . vždycky zařazování řetězců ve formátu ANSI.</span><span class="sxs-lookup"><span data-stu-id="fd332-109">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="fd332-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="fd332-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="fd332-111">Poskytuje 2 bajtové formátování znaků znakové sady Unicode, které se odlišuje "W" připojením k názvu vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="fd332-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="fd332-112">Volání **MessageBoxW** vždy zařazování řetězců ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="fd332-112">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="fd332-113">Zařazování řetězců a shoda názvů</span><span class="sxs-lookup"><span data-stu-id="fd332-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="fd332-114">`CharSet` Pole přijímá následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="fd332-114">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="fd332-115"><xref:System.Runtime.InteropServices.CharSet.Ansi>(výchozí hodnota)</span><span class="sxs-lookup"><span data-stu-id="fd332-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="fd332-116">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="fd332-116">String marshaling</span></span>  
  
     <span data-ttu-id="fd332-117">Volání platformy zařazování řetězců z jejich spravovaného formátu (Unicode) do formátu ANSI.</span><span class="sxs-lookup"><span data-stu-id="fd332-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="fd332-118">Shoda názvů</span><span class="sxs-lookup"><span data-stu-id="fd332-118">Name matching</span></span>  
  
     <span data-ttu-id="fd332-119">Když je <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> `true`pole ve výchozím nastavení v Visual Basic, vyvolá vyhledá platforma pouze zadaný název.</span><span class="sxs-lookup"><span data-stu-id="fd332-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="fd332-120">Například pokud zadáte **MessageBox**, vyvolá volání metody **MessageBox** a dojde k chybě, když nemůže najít přesný pravopis.</span><span class="sxs-lookup"><span data-stu-id="fd332-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="fd332-121">Když je `ExactSpelling` `false`pole ve výchozím nastavení v jazyce C++ a C#, vyvolá volání metody jako první (MessageBox) nezměněný alias (**MessageBox**) a pak pozměněný název (**MessageBox**), pokud nebyl nalezen nezměněný alias.</span><span class="sxs-lookup"><span data-stu-id="fd332-121">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="fd332-122">Všimněte si, že chování při shodě názvů ANSI se liší od chování při shodě názvů Unicode.</span><span class="sxs-lookup"><span data-stu-id="fd332-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="fd332-123">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="fd332-123">String marshaling</span></span>  
  
     <span data-ttu-id="fd332-124">Vyvolání platformy kopíruje řetězce z spravovaného formátu (Unicode) do formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="fd332-124">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="fd332-125">Shoda názvů</span><span class="sxs-lookup"><span data-stu-id="fd332-125">Name matching</span></span>  
  
     <span data-ttu-id="fd332-126">Když je `ExactSpelling` `true`pole ve výchozím nastavení v Visual Basic, vyvolá vyhledá platforma pouze zadaný název.</span><span class="sxs-lookup"><span data-stu-id="fd332-126">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="fd332-127">Například pokud zadáte **MessageBox**, vyvolá volání metody **MessageBox** a dojde k chybě, pokud nemůže najít přesný pravopis.</span><span class="sxs-lookup"><span data-stu-id="fd332-127">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="fd332-128">Když je `ExactSpelling` `false`pole ve výchozím nastavení v jazyce C++ a C#, vyvolá volání metody jako první pozměněný název (**MessageBoxW**) a pak nezměněný alias (**MessageBox**), pokud nebyl nalezen pozměněný název.</span><span class="sxs-lookup"><span data-stu-id="fd332-128">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="fd332-129">Všimněte si, že chování při shodě názvů Unicode se liší od chování při shodě názvů ANSI.</span><span class="sxs-lookup"><span data-stu-id="fd332-129">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="fd332-130">Volání platformy se v době běhu volí mezi formáty ANSI a Unicode, a to na základě cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="fd332-130">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="fd332-131">Určení znakové sady v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd332-131">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="fd332-132">Následující příklad deklaruje funkci **MessageBox** třikrát, a to pokaždé, když se liší chování znakových sad.</span><span class="sxs-lookup"><span data-stu-id="fd332-132">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="fd332-133">Můžete určit chování znakových sad v Visual Basic přidáním klíčového slova **ANSI**, **Unicode**nebo **auto** do příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="fd332-133">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="fd332-134">Vynecháte-li klíčové slovo sady znaků, jak je provedeno v prvním příkazu deklarace, je <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole standardně znakovou sadou ANSI.</span><span class="sxs-lookup"><span data-stu-id="fd332-134">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="fd332-135">Druhý a třetí příkaz v příkladu explicitně specifikují znakovou sadu s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="fd332-135">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="fd332-136">Určení znakové sady v jazycích C# a C++</span><span class="sxs-lookup"><span data-stu-id="fd332-136">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="fd332-137"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole určuje základní znakovou sadu jako ANSI nebo Unicode.</span><span class="sxs-lookup"><span data-stu-id="fd332-137">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="fd332-138">Znaková sada určuje, jak by měly být zařazeny řetězcové argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="fd332-138">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="fd332-139">K označení znakové sady použijte jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="fd332-139">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="fd332-140">Následující příklad ukazuje tři spravované definice funkce **MessageBox** s atributem pro určení znakové sady.</span><span class="sxs-lookup"><span data-stu-id="fd332-140">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="fd332-141">V první definici po vynechání `CharSet` pole je ve výchozím nastavení znaková sada ANSI.</span><span class="sxs-lookup"><span data-stu-id="fd332-141">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd332-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd332-142">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="fd332-143">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="fd332-143">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="fd332-144">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="fd332-144">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="fd332-145">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="fd332-145">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
