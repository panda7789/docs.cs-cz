---
title: Určení vstupního bodu
description: Naučte se zadat vstupní bod, který identifikuje umístění funkce v knihovně DLL. Funkci lze přejmenovat tak, že namapujete vstupní bod na jiný název.
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: 5628c54103410d127c2f9c4f56e1c6f897ada754
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282018"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="30a82-104">Určení vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="30a82-104">Specifying an Entry Point</span></span>

<span data-ttu-id="30a82-105">Vstupní bod určuje umístění funkce v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="30a82-105">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="30a82-106">Původní název nebo řadový vstupní bod cílové funkce identifikuje v rámci spravovaného projektu funkci napříč hranicemi interoperability.</span><span class="sxs-lookup"><span data-stu-id="30a82-106">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="30a82-107">Dále je možné namapovat vstupní bod na jiný název, a tak funkci účinně přejmenovat.</span><span class="sxs-lookup"><span data-stu-id="30a82-107">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="30a82-108">Následuje seznam možných důvodů přejmenování funkce knihovny DLL:</span><span class="sxs-lookup"><span data-stu-id="30a82-108">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="30a82-109">Zamezení používání názvů funkcí rozhraní API, která rozlišují velikost písmen</span><span class="sxs-lookup"><span data-stu-id="30a82-109">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="30a82-110">Dodržování stávajících standardů pro zadávání názvů</span><span class="sxs-lookup"><span data-stu-id="30a82-110">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="30a82-111">Přizpůsobení funkcí, které přijímají různé datové typy (deklarací několika verzí stejné funkce knihovny DLL)</span><span class="sxs-lookup"><span data-stu-id="30a82-111">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="30a82-112">Zjednodušení používání rozhraní API, která obsahují verze ANSI a Unicode</span><span class="sxs-lookup"><span data-stu-id="30a82-112">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="30a82-113">Toto téma popisuje, jakým způsobem lze přejmenovat funkci knihovny DLL ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="30a82-113">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="30a82-114">Přejmenování funkce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30a82-114">Renaming a Function in Visual Basic</span></span>  

<span data-ttu-id="30a82-115">Visual Basic používá klíčové slovo **Function** v příkazu **Declare** pro nastavení <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pole.</span><span class="sxs-lookup"><span data-stu-id="30a82-115">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="30a82-116">Následující příklad znázorňuje základní deklaraci.</span><span class="sxs-lookup"><span data-stu-id="30a82-116">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="30a82-117">Vstupní bod **MessageBox** můžete nahradit pomocí **OknoSeZprávou** vložením klíčového slova **alias** do definice, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="30a82-117">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="30a82-118">V obou příkladech klíčové slovo **auto** eliminuje nutnost zadat verzi znakového sady vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="30a82-118">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="30a82-119">Další informace o výběru znakové sady naleznete v tématu [Určení znakové sady](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="30a82-119">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
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
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="30a82-120">Přejmenování funkce v jazyce C# a C++</span><span class="sxs-lookup"><span data-stu-id="30a82-120">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="30a82-121">K určení funkce knihovny DLL pomocí názvu nebo řádu můžete použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="30a82-121">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="30a82-122">Pokud je název funkce v definici metody stejný jako vstupní bod v knihovně DLL, není nutné explicitně identifikovat funkci s polem **EntryPoint** .</span><span class="sxs-lookup"><span data-stu-id="30a82-122">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="30a82-123">Jinak lze pro určení názvu nebo řádu použít jednu z těchto podob atributů:</span><span class="sxs-lookup"><span data-stu-id="30a82-123">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="30a82-124">Je nutné poznamenat, že pro řád je třeba použít předponu v podobě znaku libry (#).</span><span class="sxs-lookup"><span data-stu-id="30a82-124">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="30a82-125">Následující příklad ukazuje, jak nahradit **MessageBox** ' pomocí **OknoSeZprávou** v kódu pomocí pole **EntryPoint** .</span><span class="sxs-lookup"><span data-stu-id="30a82-125">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30a82-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="30a82-126">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="30a82-127">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="30a82-127">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="30a82-128">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="30a82-128">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="30a82-129">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="30a82-129">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
