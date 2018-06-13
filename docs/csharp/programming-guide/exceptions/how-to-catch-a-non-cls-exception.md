---
title: 'Postupy: Zachycení výjimky nekompatibilní se specifikací CLS'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 6169f4b6de2efdfed0dbf43272d708c47b46dbca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340018"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="e29c5-102">Postupy: Zachycení výjimky nekompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="e29c5-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="e29c5-103">Některé jazyky rozhraní .NET, včetně C + +/ CLI, povolit objekty k vyvolání výjimky, které není odvozena od <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="e29c5-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="e29c5-104">Takové výjimky, se nazývají *-specifikací CLS výjimky* nebo *bez výjimky*.</span><span class="sxs-lookup"><span data-stu-id="e29c5-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="e29c5-105">V jazyce Visual C# můžete nelze vyvolat-specifikací CLS výjimky, ale můžete je zachytit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="e29c5-105">In Visual C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
-   <span data-ttu-id="e29c5-106">V rámci `catch (Exception e)` blokovat jako <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="e29c5-106">Within a `catch (Exception e)` block as a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
     <span data-ttu-id="e29c5-107">Ve výchozím nastavení sestavení Visual C# zachytí výjimky specifikací CLS jako zabalené výjimky.</span><span class="sxs-lookup"><span data-stu-id="e29c5-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="e29c5-108">Tuto metodu použijte, pokud budete potřebovat přístup k původní výjimka, která je přístupná prostřednictvím <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e29c5-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span> <span data-ttu-id="e29c5-109">Postupem uvedeným v tomto tématu vysvětluje, jak zachytit výjimky tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="e29c5-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
-   <span data-ttu-id="e29c5-110">V rámci bloku catch obecné (bloku catch bez zadán typ výjimky), který je put po `catch (Exception)` nebo `catch (Exception e)` bloku.</span><span class="sxs-lookup"><span data-stu-id="e29c5-110">Within a general catch block (a catch block without an exception type specified) that is put after a `catch (Exception)` or `catch (Exception e)` block.</span></span>  
  
     <span data-ttu-id="e29c5-111">Tuto metodu použijte, pokud chcete provést některé akce (například zápis do souboru protokolu) v reakci na-specifikací CLS výjimky a nepotřebujete přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="e29c5-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="e29c5-112">Ve výchozím nastavení modul common language runtime zabalí všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="e29c5-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="e29c5-113">Chcete-li toto chování zakázat, přidejte tento atribut úrovně sestavení do kódu, obvykle v souboru AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="e29c5-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="e29c5-114">K zachycení výjimky specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="e29c5-114">To catch a non-CLS exception</span></span>  
  
1.  <span data-ttu-id="e29c5-115">V rámci `catch(Exception e) block`, použijte `as` – klíčové slovo k testování zda `e` lze převést na <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="e29c5-115">Within a `catch(Exception e) block`, use the `as` keyword to test whether `e` can be cast to a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
2.  <span data-ttu-id="e29c5-116">Přístup k původní výjimka pomocí <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e29c5-116">Access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e29c5-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e29c5-117">Example</span></span>  
 <span data-ttu-id="e29c5-118">Následující příklad ukazuje, jak zachytit-specifikací CLS výjimka, která byla vydána z knihovny tříd napsané v jazyce C + +/ CLR.</span><span class="sxs-lookup"><span data-stu-id="e29c5-118">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLR.</span></span> <span data-ttu-id="e29c5-119">Všimněte si, že v tomto příkladu kód klienta Visual C# vědět předem, že je typ výjimky, které jsou hlášeny <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e29c5-119">Note that in this example, the Visual C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e29c5-120">Můžete převést <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> vlastnost zpět jeho původní typ tak dlouho, dokud tento typ je přístupný z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="e29c5-120">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property back its original type as long as that type is accessible from your code.</span></span>  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## <a name="see-also"></a><span data-ttu-id="e29c5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="e29c5-121">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [<span data-ttu-id="e29c5-122">Výjimky a jejich zpracování</span><span class="sxs-lookup"><span data-stu-id="e29c5-122">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
