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
ms.openlocfilehash: 798fcacab5bd74dbd6569a68a3b598c0bb63a0a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087739"
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="f0df5-102">Určení sady znaků</span><span class="sxs-lookup"><span data-stu-id="f0df5-102">Specifying a Character Set</span></span>
<span data-ttu-id="f0df5-103"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole řídí zařazování řetězce a určuje, jak vyvolání platformy najde názvy funkcí v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="f0df5-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="f0df5-104">Toto téma popisuje, jak chování.</span><span class="sxs-lookup"><span data-stu-id="f0df5-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="f0df5-105">Některá rozhraní API exportovat dvě verze funkcí, které přijímají řetězcové argumenty: úzký (ANSI) a celý (Unicode).</span><span class="sxs-lookup"><span data-stu-id="f0df5-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="f0df5-106">Rozhraní Windows API, například zahrnuje následující názvy vstupní bod **MessageBox** funkce:</span><span class="sxs-lookup"><span data-stu-id="f0df5-106">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
-   <span data-ttu-id="f0df5-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="f0df5-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="f0df5-108">Poskytuje 1bajtový ANSI formátování, odlišené "A" připojenou k názvu vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="f0df5-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="f0df5-109">Volání **MessageBoxA** vždy zařazovat řetězce ve formátu ANSI.</span><span class="sxs-lookup"><span data-stu-id="f0df5-109">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
-   <span data-ttu-id="f0df5-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="f0df5-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="f0df5-111">Obsahuje formátování 2bajtových znaků Unicode, odlišené "W" připojenou k názvu vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="f0df5-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="f0df5-112">Volání **funkce** vždy zařazovat řetězce ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="f0df5-112">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="f0df5-113">Zařazování řetězců a shoda názvu</span><span class="sxs-lookup"><span data-stu-id="f0df5-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="f0df5-114">`CharSet` Pole přijímá následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="f0df5-114">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="f0df5-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (výchozí hodnota)</span><span class="sxs-lookup"><span data-stu-id="f0df5-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
-   <span data-ttu-id="f0df5-116">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="f0df5-116">String marshaling</span></span>  
  
     <span data-ttu-id="f0df5-117">Vyvolání platformy marshals řetězců z jejich spravovaných formátu (Unicode) na ANSI formát.</span><span class="sxs-lookup"><span data-stu-id="f0df5-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
-   <span data-ttu-id="f0df5-118">Shoda názvu</span><span class="sxs-lookup"><span data-stu-id="f0df5-118">Name matching</span></span>  
  
     <span data-ttu-id="f0df5-119">Když <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole je `true`, protože je ve výchozím nastavení v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], vyhledá pouze zadaný název vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="f0df5-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="f0df5-120">Pokud zadáte například **MessageBox**, vyhledá vyvolání platformy **MessageBox** a selže, pokud nemůže najít přesnou kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="f0df5-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="f0df5-121">Když `ExactSpelling` pole je `false`, protože je ve výchozím nastavení v jazyce C++ a C#, nejprve hledá unmangled alias vyvolání platformy (**MessageBox**), pak pozměněný název (**MessageBoxA**) Pokud se nenajde unmangled alias.</span><span class="sxs-lookup"><span data-stu-id="f0df5-121">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="f0df5-122">Všimněte si, že ANSI shoda názvu chování se liší od chování porovnávání název kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="f0df5-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
-   <span data-ttu-id="f0df5-123">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="f0df5-123">String marshaling</span></span>  
  
     <span data-ttu-id="f0df5-124">Kopie řetězce z jejich spravovaných formátu (Unicode) do Unicode formátu vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="f0df5-124">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
-   <span data-ttu-id="f0df5-125">Shoda názvu</span><span class="sxs-lookup"><span data-stu-id="f0df5-125">Name matching</span></span>  
  
     <span data-ttu-id="f0df5-126">Když `ExactSpelling` pole je `true`, protože je ve výchozím nastavení v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], vyhledá pouze zadaný název vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="f0df5-126">When the `ExactSpelling` field is `true`, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="f0df5-127">Pokud zadáte například **MessageBox**, vyhledá vyvolání platformy **MessageBox** a selže, pokud nemůže najít přesnou kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="f0df5-127">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="f0df5-128">Když `ExactSpelling` pole je `false`, protože je ve výchozím nastavení v jazyce C++ a C#, nejprve vyhledá pozměněný název vyvolání platformy (**funkce**), pak unmangled alias (**MessageBox**) Pokud se nenajde pozměnění názvu.</span><span class="sxs-lookup"><span data-stu-id="f0df5-128">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="f0df5-129">Všimněte si, že Unicode shoda názvu chování se liší od chování porovnávání název ANSI.</span><span class="sxs-lookup"><span data-stu-id="f0df5-129">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
-   <span data-ttu-id="f0df5-130">Vyvolání platformy zvolí mezi formáty ANSI a Unicode v době běhu, založené na cílové platformě.</span><span class="sxs-lookup"><span data-stu-id="f0df5-130">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="f0df5-131">Určení znakové sady v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0df5-131">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="f0df5-132">Následující příklad deklaruje **MessageBox** funkce tři vícekrát, pokaždé, když s jinou znakovou sadu chování.</span><span class="sxs-lookup"><span data-stu-id="f0df5-132">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="f0df5-133">Znakové sady chování v jazyce Visual Basic můžete zadat tak, že přidáte **Ansi**, **Unicode**, nebo **automaticky** – klíčové slovo do příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="f0df5-133">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="f0df5-134">Pokud vynecháte – klíčové slovo znakové sady, jak je tomu v prvním příkazu deklarace, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole výchozí znakovou sadu ANSI.</span><span class="sxs-lookup"><span data-stu-id="f0df5-134">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="f0df5-135">Druhý a třetí příkazy v příkladu explicitně zadat znakovou sadu s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="f0df5-135">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="f0df5-136">Určení znakové sady v C# a C++</span><span class="sxs-lookup"><span data-stu-id="f0df5-136">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="f0df5-137"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole identifikuje základní znakovou sadu ANSI nebo Unicode.</span><span class="sxs-lookup"><span data-stu-id="f0df5-137">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="f0df5-138">Znakové sady, které řídí, jak by měly být zařazeny řetězcové argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="f0df5-138">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="f0df5-139">Použijte jednu z následujících forem udávajících znakové sady:</span><span class="sxs-lookup"><span data-stu-id="f0df5-139">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="f0df5-140">Následující příklad ukazuje tři spravované definice **MessageBox** funkce s atributy k určení sady znaků.</span><span class="sxs-lookup"><span data-stu-id="f0df5-140">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="f0df5-141">V první definici podle jeho vynechání `CharSet` pole výchozí znakovou sadu ANSI.</span><span class="sxs-lookup"><span data-stu-id="f0df5-141">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
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
  
## <a name="see-also"></a><span data-ttu-id="f0df5-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0df5-142">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="f0df5-143">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="f0df5-143">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="f0df5-144">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="f0df5-144">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="f0df5-145">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="f0df5-145">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
