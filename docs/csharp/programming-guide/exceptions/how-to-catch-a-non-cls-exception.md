---
title: Jak zachytit výjimku nekompatibilní se specifikací CLS
description: Naučte se zachytit výjimku, která není CLS. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 255de4cab9a72491eb3b9624d968539d432e0442
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302006"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="b6786-104">Jak zachytit výjimku nekompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="b6786-104">How to catch a non-CLS exception</span></span>
<span data-ttu-id="b6786-105">Některé jazyky .NET, včetně C++/CLI, umožňují, aby objekty vyvolaly výjimky, které nejsou odvozeny od <xref:System.Exception> .</span><span class="sxs-lookup"><span data-stu-id="b6786-105">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="b6786-106">Takové výjimky se nazývají *výjimky, které nejsou kompatibilní se specifikací CLS* , nebo *nevýjimkou*.</span><span class="sxs-lookup"><span data-stu-id="b6786-106">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="b6786-107">V jazyce C# nelze vyvolat výjimky, které nejsou kompatibilní se specifikací CLS, ale můžete je zachytit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="b6786-107">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="b6786-108">V rámci `catch (RuntimeWrappedException e)` bloku.</span><span class="sxs-lookup"><span data-stu-id="b6786-108">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="b6786-109">Ve výchozím nastavení sestavení Visual C# zachycuje výjimky nepatřící do CLS jako zabalené výjimky.</span><span class="sxs-lookup"><span data-stu-id="b6786-109">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="b6786-110">Tuto metodu použijte, pokud potřebujete přístup k původní výjimce, ke které lze přistupovat prostřednictvím <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b6786-110">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b6786-111">Postup dále v tomto tématu vysvětluje, jak zachytit výjimky tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="b6786-111">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="b6786-112">V rámci obecného bloku catch (je určen blok catch bez typu výjimky), který je umístěn po všech ostatních `catch` blocích.</span><span class="sxs-lookup"><span data-stu-id="b6786-112">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="b6786-113">Tuto metodu použijte, pokud chcete provést určitou akci (například zápis do souboru protokolu) v reakci na výjimky jiné než CLS a nepotřebujete přístup k informacím o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="b6786-113">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="b6786-114">Ve výchozím nastavení jsou všechny výjimky zabaleny modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b6786-114">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="b6786-115">Chcete-li toto chování zakázat, přidejte do kódu tento atribut na úrovni sestavení, obvykle v souboru AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]` .</span><span class="sxs-lookup"><span data-stu-id="b6786-115">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="b6786-116">Zachycení výjimky nesouvisející se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="b6786-116">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="b6786-117">V rámci `catch(RuntimeWrappedException e)` bloku přístup k původní výjimce prostřednictvím <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b6786-117">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6786-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6786-118">Example</span></span>  
 <span data-ttu-id="b6786-119">Následující příklad ukazuje, jak zachytit výjimku nekompatibilní se specifikací CLS vyvolanou z knihovny tříd napsanou v jazyce C++/CLI.</span><span class="sxs-lookup"><span data-stu-id="b6786-119">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="b6786-120">Všimněte si, že v tomto příkladu kód klienta jazyka C# ví předem, že vyvolaný typ výjimky je <xref:System.String?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b6786-120">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b6786-121">Vlastnost můžete přetypovat <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> zpět na původní typ, pokud je tento typ přístupný z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="b6786-121">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="b6786-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6786-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="b6786-123">Výjimky a zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="b6786-123">Exceptions and Exception Handling</span></span>](./index.md)
