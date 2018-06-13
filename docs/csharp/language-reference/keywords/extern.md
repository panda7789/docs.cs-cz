---
title: extern (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 996888a585f8355bdda14e09b6bb9544257ae824
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172290"
---
# <a name="extern-c-reference"></a><span data-ttu-id="19a2e-102">extern (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="19a2e-102">extern (C# Reference)</span></span>
<span data-ttu-id="19a2e-103">`extern` Modifikátor se používá k deklaraci metodu, která je implementována externě.</span><span class="sxs-lookup"><span data-stu-id="19a2e-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="19a2e-104">Běžně se používají `extern` se modifikátor s `DllImport` atributu při použití zprostředkovatele komunikace s objekty služby volat nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="19a2e-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="19a2e-105">V takovém případě metoda musí být deklarován také jako `static`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="19a2e-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>  
  
```csharp  
[DllImport("avifil32.dll")]  
private static extern void AVIFileInit();  
```  
  
 <span data-ttu-id="19a2e-106">`extern` – Klíčové slovo můžete také definovat alias externí sestavení, která vám umožní tak, aby odkazovaly různé verze stejné komponenty z v rámci jednoho sestavení.</span><span class="sxs-lookup"><span data-stu-id="19a2e-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="19a2e-107">Další informace najdete v tématu [extern alias](../../../csharp/language-reference/keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="19a2e-107">For more information, see [extern alias](../../../csharp/language-reference/keywords/extern-alias.md).</span></span>  
  
 <span data-ttu-id="19a2e-108">Jedná se o chybu používat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) a `extern` modifikátory společně k úpravě stejného člena.</span><span class="sxs-lookup"><span data-stu-id="19a2e-108">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="19a2e-109">Pomocí `extern` modifikátor znamená, že je metoda implementována mimo kód C# zatímco pomocí `abstract` modifikátor znamená, že není zadaný implementace metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="19a2e-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>  
  
 <span data-ttu-id="19a2e-110">Externí klíčové slovo má v jazyce C# omezenější použití než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="19a2e-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="19a2e-111">Chcete-li porovnat klíčové slovo C# s klíčovým slovem C++, přečtěte si informace v kapitole Určení zapojení v referenci jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="19a2e-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19a2e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="19a2e-112">Example</span></span>  
 <span data-ttu-id="19a2e-113">**Příklad 1.**</span><span class="sxs-lookup"><span data-stu-id="19a2e-113">**Example 1.**</span></span> <span data-ttu-id="19a2e-114">V tomto příkladu program od uživatele přijímá řetězec a zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="19a2e-114">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="19a2e-115">Program používá `MessageBox` metoda naimportované z knihovny User32.dll.</span><span class="sxs-lookup"><span data-stu-id="19a2e-115">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="19a2e-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="19a2e-116">Example</span></span>  
 <span data-ttu-id="19a2e-117">**Příklad 2.**</span><span class="sxs-lookup"><span data-stu-id="19a2e-117">**Example 2.**</span></span> <span data-ttu-id="19a2e-118">Tento příklad ukazuje programu C#, který volá do knihovny jazyka C (nativní knihovny DLL).</span><span class="sxs-lookup"><span data-stu-id="19a2e-118">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>  
  
 1. <span data-ttu-id="19a2e-119">Vytvoření následujícího souboru C a pojmenujte ji `cmdll.c`:</span><span class="sxs-lookup"><span data-stu-id="19a2e-119">Create the following C file and name it `cmdll.c`:</span></span>  
  
```  
// cmdll.c  
// Compile with: /LD  
int __declspec(dllexport) SampleMethod(int i)  
{  
   return i*10;  
}  
```  
  
## <a name="example"></a><span data-ttu-id="19a2e-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="19a2e-120">Example</span></span>  
 2. <span data-ttu-id="19a2e-121">Otevřete okno sady Visual Studio x64 (nebo x32) nativní nástroje pro příkazový řádek z instalačního adresáře nástroje Visual Studio a kompilaci `cmdll.c` souboru zadáním **cl /LD cmdll.c** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="19a2e-121">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl /LD cmdll.c** at the command prompt.</span></span>  
  
 3. <span data-ttu-id="19a2e-122">Ve stejném adresáři, vytvořte následující soubor C# a pojmenujte ji `cm.cs`:</span><span class="sxs-lookup"><span data-stu-id="19a2e-122">In the same directory, create the following C# file and name it `cm.cs`:</span></span>  
  
```csharp  
// cm.cs  
using System;  
using System.Runtime.InteropServices;  
public class MainClass   
{  
   [DllImport("Cmdll.dll")]  
   public static extern int SampleMethod(int x);  
  
   static void Main()   
   {  
      Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="19a2e-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="19a2e-123">Example</span></span>  
 3. <span data-ttu-id="19a2e-124">Otevřete okno sady Visual Studio x64 (nebo x32) nativní nástroje pro příkazový řádek z instalačního adresáře nástroje Visual Studio a kompilaci `cm.cs` souboru zadáním:</span><span class="sxs-lookup"><span data-stu-id="19a2e-124">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>  
  
> <span data-ttu-id="19a2e-125">**CSC cm.cs** (pro x64 příkazového řádku)</span><span class="sxs-lookup"><span data-stu-id="19a2e-125">**csc cm.cs** (for the x64 command prompt)</span></span>   
>  <span data-ttu-id="19a2e-126">—nebo—</span><span class="sxs-lookup"><span data-stu-id="19a2e-126">—or—</span></span>  
> <span data-ttu-id="19a2e-127">**CSC /platform:x 86 cm.cs** (pro x32 příkazového řádku)</span><span class="sxs-lookup"><span data-stu-id="19a2e-127">**csc /platform:x86 cm.cs** (for the x32 command prompt)</span></span>  
  
 <span data-ttu-id="19a2e-128">Tím se vytvoří spustitelný soubor `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="19a2e-128">This will create the executable file `cm.exe`.</span></span>  
  
 4. <span data-ttu-id="19a2e-129">Run `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="19a2e-129">Run `cm.exe`.</span></span> <span data-ttu-id="19a2e-130">`SampleMethod` Metoda předá hodnotu 5 soubor knihovny DLL, která vrátí hodnotu násobí hodnotou 10.</span><span class="sxs-lookup"><span data-stu-id="19a2e-130">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="19a2e-131">Program vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="19a2e-131">The program produces the following output:</span></span>  
  
```  
SampleMethod() returns 50.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="19a2e-132">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="19a2e-132">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="19a2e-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="19a2e-133">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
 [<span data-ttu-id="19a2e-134">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="19a2e-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="19a2e-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="19a2e-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="19a2e-136">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="19a2e-136">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="19a2e-137">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="19a2e-137">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
