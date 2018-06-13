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
ms.openlocfilehash: 31bb28b5bda51fb1579021e47b8d5ec49adb644e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388830"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="4ba66-102">Určení vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="4ba66-102">Specifying an Entry Point</span></span>
<span data-ttu-id="4ba66-103">Vstupní bod určuje umístění funkce v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="4ba66-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="4ba66-104">Původní název nebo řadový vstupní bod cílové funkce identifikuje v rámci spravovaného projektu funkci napříč hranicemi interoperability.</span><span class="sxs-lookup"><span data-stu-id="4ba66-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="4ba66-105">Dále je možné namapovat vstupní bod na jiný název, a tak funkci účinně přejmenovat.</span><span class="sxs-lookup"><span data-stu-id="4ba66-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="4ba66-106">Následuje seznam možných důvodů přejmenování funkce knihovny DLL:</span><span class="sxs-lookup"><span data-stu-id="4ba66-106">Following is a list of possible reasons to rename a DLL function:</span></span>  
  
-   <span data-ttu-id="4ba66-107">Zamezení používání názvů funkcí rozhraní API, která rozlišují velikost písmen</span><span class="sxs-lookup"><span data-stu-id="4ba66-107">To avoid using case-sensitive API function names</span></span>  
  
-   <span data-ttu-id="4ba66-108">Dodržování stávajících standardů pro zadávání názvů</span><span class="sxs-lookup"><span data-stu-id="4ba66-108">To comply with existing naming standards</span></span>  
  
-   <span data-ttu-id="4ba66-109">Přizpůsobení funkcí, které přijímají různé datové typy (deklarací několika verzí stejné funkce knihovny DLL)</span><span class="sxs-lookup"><span data-stu-id="4ba66-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
-   <span data-ttu-id="4ba66-110">Zjednodušení používání rozhraní API, která obsahují verze ANSI a Unicode</span><span class="sxs-lookup"><span data-stu-id="4ba66-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="4ba66-111">Toto téma popisuje, jakým způsobem lze přejmenovat funkci knihovny DLL ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="4ba66-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="4ba66-112">Přejmenování funkce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ba66-112">Renaming a Function in Visual Basic</span></span>  
 <span data-ttu-id="4ba66-113">Visual Basic používá **funkce** – klíčové slovo v **Declare** příkaz nastavit <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pole.</span><span class="sxs-lookup"><span data-stu-id="4ba66-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="4ba66-114">Následující příklad znázorňuje základní deklaraci.</span><span class="sxs-lookup"><span data-stu-id="4ba66-114">The following example shows a basic declaration.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 <span data-ttu-id="4ba66-115">Můžete nahradit **MessageBox** vstupní bod s **MsgBox** zahrnutím **Alias** – klíčové slovo v definici, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4ba66-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="4ba66-116">V obou příkladech **automaticky** – klíčové slovo eliminuje nutnost zadat znakovou sadu verzi vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="4ba66-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="4ba66-117">Další informace o výběru znak nastavení najdete [zadání znaková sada](../../../docs/framework/interop/specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="4ba66-117">For more information about selecting a character set, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="4ba66-118">Přejmenování funkce v jazyce C# a C++</span><span class="sxs-lookup"><span data-stu-id="4ba66-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="4ba66-119">K určení funkce knihovny DLL pomocí názvu nebo řádu můžete použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4ba66-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="4ba66-120">Pokud název funkce v definici vaše metoda je stejný jako vstupní bod v knihovně DLL, není nutné explicitně rozpoznat funkci s **EntryPoint** pole.</span><span class="sxs-lookup"><span data-stu-id="4ba66-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="4ba66-121">Jinak lze pro určení názvu nebo řádu použít jednu z těchto podob atributů:</span><span class="sxs-lookup"><span data-stu-id="4ba66-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 <span data-ttu-id="4ba66-122">Je nutné poznamenat, že pro řád je třeba použít předponu v podobě znaku libry (#).</span><span class="sxs-lookup"><span data-stu-id="4ba66-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="4ba66-123">Následující příklad ukazuje, jak nahradit **MessageBoxA** s **MsgBox** v kódu pomocí **EntryPoint** pole.</span><span class="sxs-lookup"><span data-stu-id="4ba66-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
  
public class Win32 {  
    [DllImport("user32.dll", EntryPoint="MessageBoxA")]  
    public static extern int MsgBox(int hWnd, String text, String caption,  
                                    uint type);  
}  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
  
typedef void* HWND;  
[DllImport("user32", EntryPoint="MessageBoxA")]  
extern "C" int MsgBox(HWND hWnd,  
                      String*  pText,  
                      String*  pCaption,  
                      unsigned int uType);  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ba66-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ba66-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="4ba66-125">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="4ba66-125">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="4ba66-126">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="4ba66-126">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="4ba66-127">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="4ba66-127">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
