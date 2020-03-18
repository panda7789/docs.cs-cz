---
title: Jak zachytit výjimku nekompatibilní se specifikací CLS
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 635cf0a9142f56dea4b2722fbf3f3eda505d85ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346280"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="b3165-102">Jak zachytit výjimku nekompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="b3165-102">How to catch a non-CLS exception</span></span>
<span data-ttu-id="b3165-103">Některé jazyky .NET, včetně C++/CLI, umožňují objektům <xref:System.Exception>vyvolat výjimky, které nejsou odvozeny z .</span><span class="sxs-lookup"><span data-stu-id="b3165-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="b3165-104">Tyto výjimky se nazývají *výjimky bez specifikace CLS* nebo *jiné výjimky*.</span><span class="sxs-lookup"><span data-stu-id="b3165-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="b3165-105">V c# nelze vyvolat výjimky bez CLS, ale můžete je zachytit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="b3165-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="b3165-106">V `catch (RuntimeWrappedException e)` bloku.</span><span class="sxs-lookup"><span data-stu-id="b3165-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="b3165-107">Ve výchozím nastavení visual c# sestavení zachytí výjimky bez CLS jako zabalené výjimky.</span><span class="sxs-lookup"><span data-stu-id="b3165-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="b3165-108">Tuto metodu použijte, pokud potřebujete přístup k původní výjimce, ke které lze přistupovat prostřednictvím vlastnosti. <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b3165-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b3165-109">Postup dále v tomto tématu vysvětluje, jak zachytit výjimky tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="b3165-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="b3165-110">V rámci obecné catch bloku (catch blok bez typu výjimky `catch` zadán), který je umístěn za všechny ostatní bloky.</span><span class="sxs-lookup"><span data-stu-id="b3165-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="b3165-111">Tuto metodu použijte, pokud chcete provést nějakou akci (například zápis do souboru protokolu) v reakci na výjimky bez specifikace CLS a nepotřebujete přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="b3165-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="b3165-112">Ve výchozím nastavení zaobění běžného jazyka runtime zabalí všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="b3165-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="b3165-113">Chcete-li toto chování zakázat, přidejte do kódu tento `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`atribut na úrovni sestavení, obvykle v souboru AssemblyInfo.cs: .</span><span class="sxs-lookup"><span data-stu-id="b3165-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="b3165-114">Chcete-li zachytit výjimku bez specifikace CLS</span><span class="sxs-lookup"><span data-stu-id="b3165-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="b3165-115">V `catch(RuntimeWrappedException e)` rámci bloku přístup k <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> původní výjimku prostřednictvím vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b3165-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3165-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3165-116">Example</span></span>  
 <span data-ttu-id="b3165-117">Následující příklad ukazuje, jak zachytit výjimku bez specifikace CLS, která byla vyvolána z knihovny tříd napsané v jazyce C++/CLI.</span><span class="sxs-lookup"><span data-stu-id="b3165-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="b3165-118">Všimněte si, že v tomto příkladu kód klienta C# <xref:System.String?displayProperty=nameWithType>předem ví, že typ výjimky je vyvolána .</span><span class="sxs-lookup"><span data-stu-id="b3165-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b3165-119">Můžete přetypovat <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> vlastnost zpět jeho původní typ tak dlouho, dokud tento typ je přístupný z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="b3165-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3165-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3165-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="b3165-121">Výjimky a zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="b3165-121">Exceptions and Exception Handling</span></span>](./index.md)
