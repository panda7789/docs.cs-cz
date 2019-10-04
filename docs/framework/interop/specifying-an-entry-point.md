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
ms.openlocfilehash: 2a5449b4fa77ba99a18595077081089e80bd32df
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833610"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="872fc-102">Určení vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="872fc-102">Specifying an Entry Point</span></span>

<span data-ttu-id="872fc-103">Vstupní bod určuje umístění funkce v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="872fc-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="872fc-104">Původní název nebo řadový vstupní bod cílové funkce identifikuje v rámci spravovaného projektu funkci napříč hranicemi interoperability.</span><span class="sxs-lookup"><span data-stu-id="872fc-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="872fc-105">Dále je možné namapovat vstupní bod na jiný název, a tak funkci účinně přejmenovat.</span><span class="sxs-lookup"><span data-stu-id="872fc-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="872fc-106">Následuje seznam možných důvodů přejmenování funkce knihovny DLL:</span><span class="sxs-lookup"><span data-stu-id="872fc-106">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="872fc-107">Zamezení používání názvů funkcí rozhraní API, která rozlišují velikost písmen</span><span class="sxs-lookup"><span data-stu-id="872fc-107">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="872fc-108">Dodržování stávajících standardů pro zadávání názvů</span><span class="sxs-lookup"><span data-stu-id="872fc-108">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="872fc-109">Přizpůsobení funkcí, které přijímají různé datové typy (deklarací několika verzí stejné funkce knihovny DLL)</span><span class="sxs-lookup"><span data-stu-id="872fc-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="872fc-110">Zjednodušení používání rozhraní API, která obsahují verze ANSI a Unicode</span><span class="sxs-lookup"><span data-stu-id="872fc-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="872fc-111">Toto téma popisuje, jakým způsobem lze přejmenovat funkci knihovny DLL ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="872fc-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="872fc-112">Přejmenování funkce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="872fc-112">Renaming a Function in Visual Basic</span></span>  
 
<span data-ttu-id="872fc-113">Visual Basic používá klíčové slovo **Function** v příkazu **Declare** pro nastavení pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="872fc-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="872fc-114">Následující příklad znázorňuje základní deklaraci.</span><span class="sxs-lookup"><span data-stu-id="872fc-114">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="872fc-115">Vstupní bod **MessageBox** můžete nahradit pomocí **OknoSeZprávou** vložením klíčového slova **alias** do definice, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="872fc-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="872fc-116">V obou příkladech klíčové slovo **auto** eliminuje nutnost zadat verzi znakového sady vstupního bodu.</span><span class="sxs-lookup"><span data-stu-id="872fc-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="872fc-117">Další informace o výběru znakové sady naleznete v tématu [Určení znakové sady](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="872fc-117">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
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
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="872fc-118">Přejmenování funkce v jazyce C# a C++</span><span class="sxs-lookup"><span data-stu-id="872fc-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="872fc-119">K určení funkce knihovny DLL pomocí názvu nebo řádu můžete použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="872fc-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="872fc-120">Pokud je název funkce v definici metody stejný jako vstupní bod v knihovně DLL, není nutné explicitně identifikovat funkci s polem **EntryPoint** .</span><span class="sxs-lookup"><span data-stu-id="872fc-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="872fc-121">Jinak lze pro určení názvu nebo řádu použít jednu z těchto podob atributů:</span><span class="sxs-lookup"><span data-stu-id="872fc-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="872fc-122">Je nutné poznamenat, že pro řád je třeba použít předponu v podobě znaku libry (#).</span><span class="sxs-lookup"><span data-stu-id="872fc-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="872fc-123">Následující příklad ukazuje, jak nahradit **MessageBox** ' pomocí **OknoSeZprávou** v kódu pomocí pole **EntryPoint** .</span><span class="sxs-lookup"><span data-stu-id="872fc-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="872fc-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="872fc-124">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="872fc-125">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="872fc-125">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="872fc-126">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="872fc-126">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="872fc-127">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="872fc-127">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
