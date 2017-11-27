---
title: "Určení vstupního bodu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7406e256acaea0c535c222386c529c4087bbdc6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="fec91-102">Určení vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="fec91-102">Specifying an Entry Point</span></span>
<span data-ttu-id="fec91-103">Vstupní bod určuje umístění funkce v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="fec91-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="fec91-104">Původní název nebo řadový vstupní bod cílové funkce identifikuje v rámci spravovaného projektu funkci napříč hranicemi interoperability.</span><span class="sxs-lookup"><span data-stu-id="fec91-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="fec91-105">Dále je možné namapovat vstupní bod na jiný název, a tak funkci účinně přejmenovat.</span><span class="sxs-lookup"><span data-stu-id="fec91-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="fec91-106">Následuje seznam možných důvodů přejmenování funkce knihovny DLL:</span><span class="sxs-lookup"><span data-stu-id="fec91-106">Following is a list of possible reasons to rename a DLL function:</span></span>  
  
-   <span data-ttu-id="fec91-107">Zamezení používání názvů funkcí rozhraní API, která rozlišují velikost písmen</span><span class="sxs-lookup"><span data-stu-id="fec91-107">To avoid using case-sensitive API function names</span></span>  
  
-   <span data-ttu-id="fec91-108">Dodržování stávajících standardů pro zadávání názvů</span><span class="sxs-lookup"><span data-stu-id="fec91-108">To comply with existing naming standards</span></span>  
  
-   <span data-ttu-id="fec91-109">Přizpůsobení funkcí, které přijímají různé datové typy (deklarací několika verzí stejné funkce knihovny DLL)</span><span class="sxs-lookup"><span data-stu-id="fec91-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
-   <span data-ttu-id="fec91-110">Zjednodušení používání rozhraní API, která obsahují verze ANSI a Unicode</span><span class="sxs-lookup"><span data-stu-id="fec91-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="fec91-111">Toto téma popisuje, jakým způsobem lze přejmenovat funkci knihovny DLL ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="fec91-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="fec91-112">Přejmenování funkce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fec91-112">Renaming a Function in Visual Basic</span></span>  
 <span data-ttu-id="fec91-113">Visual Basic používá **funkce** – klíčové slovo v **Declare** příkaz nastavit <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pole.</span><span class="sxs-lookup"><span data-stu-id="fec91-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="fec91-114">Následující příklad znázorňuje základní deklaraci.</span><span class="sxs-lookup"><span data-stu-id="fec91-114">The following example shows a basic declaration.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 <span data-ttu-id="fec91-115">Můžete nahradit **MessageBox** vstupní bod s **MsgBox** zahrnutím **Alias** – klíčové slovo v definici, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fec91-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="fec91-116">V obou příkladech **automaticky** – klíčové slovo eliminuje nutnost zadat znakovou sadu verzi vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="fec91-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="fec91-117">Další informace o výběru znak nastavení najdete [zadání znaková sada](../../../docs/framework/interop/specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="fec91-117">For more information about selecting a character set, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="fec91-118">Přejmenování funkce v jazyce C# a C++</span><span class="sxs-lookup"><span data-stu-id="fec91-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="fec91-119">K určení funkce knihovny DLL pomocí názvu nebo řádu můžete použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fec91-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="fec91-120">Pokud název funkce v definici vaše metoda je stejný jako vstupní bod v knihovně DLL, není nutné explicitně rozpoznat funkci s **EntryPoint** pole.</span><span class="sxs-lookup"><span data-stu-id="fec91-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="fec91-121">Jinak lze pro určení názvu nebo řádu použít jednu z těchto podob atributů:</span><span class="sxs-lookup"><span data-stu-id="fec91-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 <span data-ttu-id="fec91-122">Je nutné poznamenat, že pro řád je třeba použít předponu v podobě znaku libry (#).</span><span class="sxs-lookup"><span data-stu-id="fec91-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="fec91-123">Následující příklad ukazuje, jak nahradit **MessageBoxA** s **MsgBox** v kódu pomocí **EntryPoint** pole.</span><span class="sxs-lookup"><span data-stu-id="fec91-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fec91-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="fec91-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="fec91-125">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="fec91-125">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="fec91-126">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="fec91-126">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="fec91-127">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="fec91-127">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
