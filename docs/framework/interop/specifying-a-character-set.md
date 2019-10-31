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
# <a name="specifying-a-character-set"></a><span data-ttu-id="4134b-102">Určení sady znaků</span><span class="sxs-lookup"><span data-stu-id="4134b-102">Specifying a Character Set</span></span>
<span data-ttu-id="4134b-103">Pole <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> řídí zařazování řetězců a určuje, jakým způsobem vyvolání platformy nalezne názvy funkcí v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="4134b-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="4134b-104">V tomto tématu jsou popsána obě chování.</span><span class="sxs-lookup"><span data-stu-id="4134b-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="4134b-105">Některá rozhraní API exportují dvě verze funkcí, které přijímají argumenty pro řetězce: úzká (ANSI) a roztažitelné (Unicode).</span><span class="sxs-lookup"><span data-stu-id="4134b-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="4134b-106">Rozhraní Windows API obsahuje například následující názvy vstupních bodů pro funkci **MessageBox** :</span><span class="sxs-lookup"><span data-stu-id="4134b-106">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="4134b-107">**MessageBox**</span><span class="sxs-lookup"><span data-stu-id="4134b-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="4134b-108">Poskytuje 1 bajtové formátování znakové sady ANSI rozlišené znakem "A", který je připojený k názvu vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="4134b-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="4134b-109">Volání **MessageBox** . vždycky zařazování řetězců ve formátu ANSI.</span><span class="sxs-lookup"><span data-stu-id="4134b-109">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="4134b-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="4134b-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="4134b-111">Poskytuje 2 bajtové formátování znaků znakové sady Unicode, které se odlišuje "W" připojením k názvu vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="4134b-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="4134b-112">Volání **MessageBoxW** vždy zařazování řetězců ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="4134b-112">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="4134b-113">Zařazování řetězců a shoda názvů</span><span class="sxs-lookup"><span data-stu-id="4134b-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="4134b-114">Pole `CharSet` přijímá následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="4134b-114">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="4134b-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (výchozí hodnota)</span><span class="sxs-lookup"><span data-stu-id="4134b-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="4134b-116">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="4134b-116">String marshaling</span></span>  
  
     <span data-ttu-id="4134b-117">Volání platformy zařazování řetězců z jejich spravovaného formátu (Unicode) do formátu ANSI.</span><span class="sxs-lookup"><span data-stu-id="4134b-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="4134b-118">Shoda názvů</span><span class="sxs-lookup"><span data-stu-id="4134b-118">Name matching</span></span>  
  
     <span data-ttu-id="4134b-119">Když je pole <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> `true`, protože je ve výchozím nastavení v Visual Basic, vyvolá hledání na platformě pouze název, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="4134b-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="4134b-120">Například pokud zadáte **MessageBox**, vyvolá volání metody **MessageBox** a dojde k chybě, když nemůže najít přesný pravopis.</span><span class="sxs-lookup"><span data-stu-id="4134b-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="4134b-121">Když je pole `ExactSpelling` `false`, protože je ve výchozím nastavení C++ v a C#, vyvolá volání metody jako první (MessageBox) nezměněný alias (**MessageBox**), pak se pozměněný název (**MessageBox**), pokud nebyl nalezen nezměněný alias.</span><span class="sxs-lookup"><span data-stu-id="4134b-121">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="4134b-122">Všimněte si, že chování při shodě názvů ANSI se liší od chování při shodě názvů Unicode.</span><span class="sxs-lookup"><span data-stu-id="4134b-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="4134b-123">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="4134b-123">String marshaling</span></span>  
  
     <span data-ttu-id="4134b-124">Vyvolání platformy kopíruje řetězce z spravovaného formátu (Unicode) do formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="4134b-124">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="4134b-125">Shoda názvů</span><span class="sxs-lookup"><span data-stu-id="4134b-125">Name matching</span></span>  
  
     <span data-ttu-id="4134b-126">Když je pole `ExactSpelling` `true`, protože je ve výchozím nastavení v Visual Basic, vyvolá hledání na platformě pouze název, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="4134b-126">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="4134b-127">Například pokud zadáte **MessageBox**, vyvolá volání metody **MessageBox** a dojde k chybě, pokud nemůže najít přesný pravopis.</span><span class="sxs-lookup"><span data-stu-id="4134b-127">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="4134b-128">Když je pole `ExactSpelling` `false`, protože je ve výchozím nastavení C++ v a, C#vyvolá volání metody jako první (**MessageBoxW**) a pak nezměněný alias (**MessageBox**), pokud nebyl nalezen pozměněný název.</span><span class="sxs-lookup"><span data-stu-id="4134b-128">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="4134b-129">Všimněte si, že chování při shodě názvů Unicode se liší od chování při shodě názvů ANSI.</span><span class="sxs-lookup"><span data-stu-id="4134b-129">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="4134b-130">Volání platformy se v době běhu volí mezi formáty ANSI a Unicode, a to na základě cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="4134b-130">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="4134b-131">Určení znakové sady v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4134b-131">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="4134b-132">Následující příklad deklaruje funkci **MessageBox** třikrát, a to pokaždé, když se liší chování znakových sad.</span><span class="sxs-lookup"><span data-stu-id="4134b-132">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="4134b-133">Můžete určit chování znakových sad v Visual Basic přidáním klíčového slova **ANSI**, **Unicode**nebo **auto** do příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="4134b-133">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="4134b-134">Vynecháte-li klíčové slovo sady znaků, jak je provedeno v prvním příkazu deklarace, je pole <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> ve výchozím nastavení znaková sada ANSI.</span><span class="sxs-lookup"><span data-stu-id="4134b-134">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="4134b-135">Druhý a třetí příkaz v příkladu explicitně specifikují znakovou sadu s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="4134b-135">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="4134b-136">Určení znakové sady v C# aC++</span><span class="sxs-lookup"><span data-stu-id="4134b-136">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="4134b-137">Pole <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> identifikuje základní znakovou sadu jako ANSI nebo Unicode.</span><span class="sxs-lookup"><span data-stu-id="4134b-137">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="4134b-138">Znaková sada určuje, jak by měly být zařazeny řetězcové argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="4134b-138">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="4134b-139">K označení znakové sady použijte jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="4134b-139">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="4134b-140">Následující příklad ukazuje tři spravované definice funkce **MessageBox** s atributem pro určení znakové sady.</span><span class="sxs-lookup"><span data-stu-id="4134b-140">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="4134b-141">V první definici po vynechání pole `CharSet` ve výchozím nastavení znaková sada ANSI.</span><span class="sxs-lookup"><span data-stu-id="4134b-141">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4134b-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4134b-142">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="4134b-143">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="4134b-143">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="4134b-144">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="4134b-144">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="4134b-145">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="4134b-145">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
