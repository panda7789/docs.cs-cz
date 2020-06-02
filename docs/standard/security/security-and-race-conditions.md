---
title: Zabezpečení a konflikty časování
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 715bf240a5f7f44ba3f914ad6788631074aa41b2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291016"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="515a0-102">Zabezpečení a konflikty časování</span><span class="sxs-lookup"><span data-stu-id="515a0-102">Security and Race Conditions</span></span>
<span data-ttu-id="515a0-103">Další oblastí obav je potenciál bezpečnostních děr vycházejících ze sporných podmínek.</span><span class="sxs-lookup"><span data-stu-id="515a0-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="515a0-104">Existuje několik způsobů, jak se k tomu může dojít.</span><span class="sxs-lookup"><span data-stu-id="515a0-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="515a0-105">Dílčí témata, která následují, popisují některé hlavní nástrah, se kterými se vývojář musí vyhnout.</span><span class="sxs-lookup"><span data-stu-id="515a0-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="515a0-106">Konflikty časování v metodě Dispose</span><span class="sxs-lookup"><span data-stu-id="515a0-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="515a0-107">Pokud metoda **Dispose** třídy (pro další informace, viz [uvolňování paměti](../garbage-collection/index.md)) není synchronizována, je možné, že čistící kód uvnitř **Dispose** lze spustit více než jednou, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="515a0-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()
{  
    if (myObj != null)
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="515a0-108">Vzhledem k tomu, že tato implementace **Dispose** není synchronizována, je možné ji `Cleanup` volat prvním jedním vláknem a poté druhým vláknem, `_myObj` aby byla nastavena na **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="515a0-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="515a0-109">Bez ohledu na to, zda se jedná o zabezpečení, závisí na tom, co se stane při `Cleanup` spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="515a0-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="515a0-110">Hlavní problém s nesynchronizovanými implementacemi **Dispose** zahrnuje použití popisovačů prostředků, jako jsou soubory.</span><span class="sxs-lookup"><span data-stu-id="515a0-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="515a0-111">Nesprávné vyřazení může způsobit použití chybného popisovače, což často vede k ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="515a0-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="515a0-112">Konflikty časování v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="515a0-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="515a0-113">V některých aplikacích může být možné, aby další vlákna mohla přistupovat ke členům třídy před tím, než se jejich konstruktory tříd úplně spustí.</span><span class="sxs-lookup"><span data-stu-id="515a0-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="515a0-114">Měli byste zkontrolovat všechny konstruktory třídy, aby se zajistilo, že nedochází k žádným problémům se zabezpečením, pokud by k tomu došlo, nebo v případě potřeby synchronizaci vláken.</span><span class="sxs-lookup"><span data-stu-id="515a0-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="515a0-115">Konflikty časování s objekty uloženými v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="515a0-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="515a0-116">Kód, který ukládá do mezipaměti informace o zabezpečení nebo používá operaci [vyhodnocení](../../framework/misc/using-the-assert-method.md) zabezpečení přístupu kódu, může být také ohrožen konflikty časování, pokud jiné části třídy nejsou vhodně synchronizovány, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="515a0-116">Code that caches security information or uses the code access security [Assert](../../framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()
{  
    if (SomeDemandPasses())
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()
{  
    if (fCallersOK)
    {  
        DoSomethingTrusted();  
    }  
    else
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 <span data-ttu-id="515a0-117">Pokud existují další cesty `DoOtherWork` , které mohou být volány z jiného vlákna se stejným objektem, nedůvěryhodný volající může nakládat za poptávku.</span><span class="sxs-lookup"><span data-stu-id="515a0-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="515a0-118">Pokud váš kód ukládá do mezipaměti informace o zabezpečení, ujistěte se, že je pro tuto chybu zabezpečení revidován.</span><span class="sxs-lookup"><span data-stu-id="515a0-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="515a0-119">Konflikty časování v finalizačních podmínkách</span><span class="sxs-lookup"><span data-stu-id="515a0-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="515a0-120">Ke konfliktům časování může dojít také v objektu, který odkazuje na statický nebo nespravovaný prostředek, který je poté uvolněn v jeho finalizační metodě.</span><span class="sxs-lookup"><span data-stu-id="515a0-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="515a0-121">Pokud více objektů sdílí prostředek, který je manipulován v finalizační metodě třídy, musí objekty synchronizovat veškerý přístup k tomuto prostředku.</span><span class="sxs-lookup"><span data-stu-id="515a0-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="515a0-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="515a0-122">See also</span></span>

- [<span data-ttu-id="515a0-123">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="515a0-123">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
