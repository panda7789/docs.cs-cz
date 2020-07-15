---
title: Určení sady znaků
description: Naučte se, jak zadat znakovou sadu, která používá kódování s úzkým kódováním (ANSI) nebo roztažitelné (Unicode). Můžete také zadat automatický výběr za běhu.
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
ms.openlocfilehash: 789753742d8714e481f038e323407cbab0499f6c
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309791"
---
# <a name="specify-a-character-set"></a><span data-ttu-id="a8a0f-104">Zadat znakovou sadu</span><span class="sxs-lookup"><span data-stu-id="a8a0f-104">Specify a character set</span></span>

<span data-ttu-id="a8a0f-105"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType>Pole řídí zařazování řetězců a určuje, jakým způsobem vyvolání platformy nalezne názvy funkcí v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-105">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="a8a0f-106">V tomto tématu jsou popsána obě chování.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-106">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="a8a0f-107">Některá rozhraní API exportují dvě verze funkcí, které přijímají argumenty pro řetězce: úzká (ANSI) a roztažitelné (Unicode).</span><span class="sxs-lookup"><span data-stu-id="a8a0f-107">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="a8a0f-108">Rozhraní Windows API obsahuje například následující názvy vstupních bodů pro funkci **MessageBox** :</span><span class="sxs-lookup"><span data-stu-id="a8a0f-108">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="a8a0f-109">**MessageBox**</span><span class="sxs-lookup"><span data-stu-id="a8a0f-109">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="a8a0f-110">Poskytuje 1 bajtové formátování znakové sady ANSI rozlišené znakem "A", který je připojený k názvu vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-110">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="a8a0f-111">Volání **MessageBox** . vždycky zařazování řetězců ve formátu ANSI.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-111">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="a8a0f-112">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="a8a0f-112">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="a8a0f-113">Poskytuje 2 bajtové formátování znaků znakové sady Unicode, které se odlišuje "W" připojením k názvu vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-113">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="a8a0f-114">Volání **MessageBoxW** vždy zařazování řetězců ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-114">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="a8a0f-115">Zařazování řetězců a shoda názvů</span><span class="sxs-lookup"><span data-stu-id="a8a0f-115">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="a8a0f-116">`CharSet`Pole přijímá následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="a8a0f-116">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="a8a0f-117"><xref:System.Runtime.InteropServices.CharSet.Ansi>(výchozí hodnota)</span><span class="sxs-lookup"><span data-stu-id="a8a0f-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="a8a0f-118">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="a8a0f-118">String marshaling</span></span>  
  
     <span data-ttu-id="a8a0f-119">Volání platformy zařazování řetězců z jejich spravovaného formátu (Unicode) do formátu ANSI.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-119">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="a8a0f-120">Shoda názvů</span><span class="sxs-lookup"><span data-stu-id="a8a0f-120">Name matching</span></span>  
  
     <span data-ttu-id="a8a0f-121">Když <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> je pole ve `true` výchozím nastavení v Visual Basic, vyvolá vyhledá platforma pouze zadaný název.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-121">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="a8a0f-122">Například pokud zadáte **MessageBox**, vyvolá volání metody **MessageBox** a dojde k chybě, když nemůže najít přesný pravopis.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-122">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="a8a0f-123">Když `ExactSpelling` je pole `false` ve výchozím nastavení v jazyce C++ a C#, vyvolá volání metody jako první (MessageBox) nezměněný alias (**MessageBox**) a pak pozměněný název (**MessageBox**), pokud nebyl nalezen nezměněný alias.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-123">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="a8a0f-124">Všimněte si, že chování při shodě názvů ANSI se liší od chování při shodě názvů Unicode.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-124">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="a8a0f-125">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="a8a0f-125">String marshaling</span></span>  
  
     <span data-ttu-id="a8a0f-126">Vyvolání platformy kopíruje řetězce z spravovaného formátu (Unicode) do formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-126">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="a8a0f-127">Shoda názvů</span><span class="sxs-lookup"><span data-stu-id="a8a0f-127">Name matching</span></span>  
  
     <span data-ttu-id="a8a0f-128">Když `ExactSpelling` je pole ve `true` výchozím nastavení v Visual Basic, vyvolá vyhledá platforma pouze zadaný název.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-128">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="a8a0f-129">Například pokud zadáte **MessageBox**, vyvolá volání metody **MessageBox** a dojde k chybě, pokud nemůže najít přesný pravopis.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-129">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="a8a0f-130">Když `ExactSpelling` je pole `false` ve výchozím nastavení v jazyce C++ a C#, vyvolá volání metody jako první pozměněný název (**MessageBoxW**) a pak nezměněný alias (**MessageBox**), pokud nebyl nalezen pozměněný název.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-130">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="a8a0f-131">Všimněte si, že chování při shodě názvů Unicode se liší od chování při shodě názvů ANSI.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-131">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="a8a0f-132">Volání platformy se v době běhu volí mezi formáty ANSI a Unicode, a to na základě cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specify-a-character-set-in-visual-basic"></a><span data-ttu-id="a8a0f-133">Zadejte znakovou sadu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a8a0f-133">Specify a character set in Visual Basic</span></span>

<span data-ttu-id="a8a0f-134">Můžete určit chování znakových sad v Visual Basic přidáním `Ansi` `Unicode` `Auto` klíčového slova, nebo do příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-134">You can specify character-set behavior in Visual Basic by adding the `Ansi`, `Unicode`, or `Auto` keyword to the declaration statement.</span></span> <span data-ttu-id="a8a0f-135">Vynecháte-li klíčové slovo sady znaků, bude <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole standardně nastaveno na znakovou sadu ANSI.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-135">If you omit the character-set keyword, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span>

<span data-ttu-id="a8a0f-136">Následující příklad deklaruje funkci **MessageBox** třikrát, a to pokaždé, když se liší chování znakových sad.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-136">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="a8a0f-137">První příkaz vynechává klíčové slovo sady znaků, takže znaková sada je standardně ANSI.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-137">The first statement omits the character-set keyword, so the character set defaults to ANSI.</span></span> <span data-ttu-id="a8a0f-138">Druhý a třetí příkaz explicitně specifikují znakovou sadu s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-138">The second and third statements explicitly specify a character set with a keyword.</span></span>

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
  
## <a name="specify-a-character-set-in-c-and-c"></a><span data-ttu-id="a8a0f-139">Určení znakové sady v jazycích C# a C++</span><span class="sxs-lookup"><span data-stu-id="a8a0f-139">Specify a character set in C# and C++</span></span>

<span data-ttu-id="a8a0f-140"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType>Pole určuje základní znakovou sadu jako ANSI nebo Unicode.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-140">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="a8a0f-141">Znaková sada určuje, jak by měly být zařazeny řetězcové argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-141">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="a8a0f-142">K označení znakové sady použijte jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="a8a0f-142">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="a8a0f-143">Následující příklad ukazuje tři spravované definice funkce **MessageBox** s atributem pro určení znakové sady.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-143">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="a8a0f-144">V první definici po vynechání pole je ve `CharSet` výchozím nastavení znaková sada ANSI.</span><span class="sxs-lookup"><span data-stu-id="a8a0f-144">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8a0f-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8a0f-145">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="a8a0f-146">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="a8a0f-146">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="a8a0f-147">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="a8a0f-147">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="a8a0f-148">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="a8a0f-148">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
