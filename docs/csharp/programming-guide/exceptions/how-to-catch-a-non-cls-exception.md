---
title: Jak zachytit výjimku, která není CLS
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 635cf0a9142f56dea4b2722fbf3f3eda505d85ee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346280"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="59aee-102">Jak zachytit výjimku, která není CLS</span><span class="sxs-lookup"><span data-stu-id="59aee-102">How to catch a non-CLS exception</span></span>
<span data-ttu-id="59aee-103">Některé jazyky .NET, včetně C++/CLI, umožňují, aby objekty vyvolaly výjimky, které nejsou odvozeny od <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="59aee-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="59aee-104">Takové výjimky se nazývají *výjimky, které nejsou kompatibilní se specifikací CLS* , nebo *nevýjimkou*.</span><span class="sxs-lookup"><span data-stu-id="59aee-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="59aee-105">V C# nemůžete vyvolat výjimky, které nejsou kompatibilní se specifikací CLS, ale můžete je zachytit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="59aee-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="59aee-106">V rámci `catch (RuntimeWrappedException e)`ho bloku.</span><span class="sxs-lookup"><span data-stu-id="59aee-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="59aee-107">Ve výchozím nastavení je sestavení C# sady Visual zachytí výjimky NEODPOVÍDAJÍCÍ specifikaci CLS jako zabalené výjimky.</span><span class="sxs-lookup"><span data-stu-id="59aee-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="59aee-108">Tuto metodu použijte, pokud potřebujete přístup k původní výjimce, ke které lze přistupovat prostřednictvím vlastnosti <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59aee-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="59aee-109">Postup dále v tomto tématu vysvětluje, jak zachytit výjimky tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="59aee-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="59aee-110">V rámci obecného bloku catch (je určen blok catch bez typu výjimky), který je umístěn po všech ostatních `catch` blocích.</span><span class="sxs-lookup"><span data-stu-id="59aee-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="59aee-111">Tuto metodu použijte, pokud chcete provést určitou akci (například zápis do souboru protokolu) v reakci na výjimky jiné než CLS a nepotřebujete přístup k informacím o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="59aee-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="59aee-112">Ve výchozím nastavení jsou všechny výjimky zabaleny modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="59aee-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="59aee-113">Chcete-li toto chování zakázat, přidejte do kódu tento atribut na úrovni sestavení, obvykle v souboru AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="59aee-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="59aee-114">Zachycení výjimky nesouvisející se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="59aee-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="59aee-115">V rámci `catch(RuntimeWrappedException e)` bloku přístup k původní výjimce prostřednictvím vlastnosti <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59aee-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59aee-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="59aee-116">Example</span></span>  
 <span data-ttu-id="59aee-117">Následující příklad ukazuje, jak zachytit výjimku, která není CLS, která byla vyvolána z knihovny tříd napsané v C++/CLI.</span><span class="sxs-lookup"><span data-stu-id="59aee-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="59aee-118">Všimněte si, že v tomto příkladu C# kód klienta ví, že typ výjimky, která je vyvolána, je <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59aee-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="59aee-119">Vlastnost <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> můžete přetypovat zpět na původní typ, pokud je tento typ přístupný z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="59aee-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59aee-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59aee-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="59aee-121">Výjimky a jejich zpracování</span><span class="sxs-lookup"><span data-stu-id="59aee-121">Exceptions and Exception Handling</span></span>](./index.md)
