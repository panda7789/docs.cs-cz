---
title: Zabezpečení a konflikty časování
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
ms.openlocfilehash: bc0d9f481fd212ede55bffde6cc20c3e080629e4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159413"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="6460e-102">Zabezpečení a konflikty časování</span><span class="sxs-lookup"><span data-stu-id="6460e-102">Security and Race Conditions</span></span>
<span data-ttu-id="6460e-103">Další oblastí obav je potenciál bezpečnostních děr vycházejících ze sporných podmínek.</span><span class="sxs-lookup"><span data-stu-id="6460e-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="6460e-104">Existuje několik způsobů, jak se k tomu může dojít.</span><span class="sxs-lookup"><span data-stu-id="6460e-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="6460e-105">Dílčí témata, která následují, popisují některé hlavní nástrah, se kterými se vývojář musí vyhnout.</span><span class="sxs-lookup"><span data-stu-id="6460e-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="6460e-106">Konflikty časování v metodě Dispose</span><span class="sxs-lookup"><span data-stu-id="6460e-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="6460e-107">Pokud metoda **Dispose** třídy (pro další informace, viz [uvolňování paměti](../../../docs/standard/garbage-collection/index.md)) není synchronizována, je možné, že čistící kód uvnitř **Dispose** lze spustit více než jednou, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6460e-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6460e-108">Vzhledem k tomu, že tato implementace **Dispose** není synchronizována, je možné, že `Cleanup` být volána prvním jedním vláknem a druhým vláknem, před `_myObj` je nastavena na **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="6460e-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="6460e-109">Bez ohledu na to, zda se jedná o zabezpečení, závisí na tom, co se stane, když `Cleanup` kód spouští.</span><span class="sxs-lookup"><span data-stu-id="6460e-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="6460e-110">Hlavní problém s nesynchronizovanými implementacemi **Dispose** zahrnuje použití popisovačů prostředků, jako jsou soubory.</span><span class="sxs-lookup"><span data-stu-id="6460e-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="6460e-111">Nesprávné vyřazení může způsobit použití chybného popisovače, což často vede k ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6460e-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="6460e-112">Konflikty časování v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="6460e-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="6460e-113">V některých aplikacích může být možné, aby další vlákna mohla přistupovat ke členům třídy před tím, než se jejich konstruktory tříd úplně spustí.</span><span class="sxs-lookup"><span data-stu-id="6460e-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="6460e-114">Měli byste zkontrolovat všechny konstruktory třídy, aby se zajistilo, že nedochází k žádným problémům se zabezpečením, pokud by k tomu došlo, nebo v případě potřeby synchronizaci vláken.</span><span class="sxs-lookup"><span data-stu-id="6460e-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="6460e-115">Konflikty časování s objekty uloženými v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="6460e-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="6460e-116">Kód, který ukládá do mezipaměti informace o zabezpečení nebo používá operaci [vyhodnocení](../../../docs/framework/misc/using-the-assert-method.md) zabezpečení přístupu kódu, může být také ohrožen konflikty časování, pokud jiné části třídy nejsou vhodně synchronizovány, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6460e-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6460e-117">Pokud existují další cesty `DoOtherWork`, které je možné volat z jiného vlákna se stejným objektem, může nedůvěryhodný volající nakládat za poptávkou.</span><span class="sxs-lookup"><span data-stu-id="6460e-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="6460e-118">Pokud váš kód ukládá do mezipaměti informace o zabezpečení, ujistěte se, že je pro tuto chybu zabezpečení revidován.</span><span class="sxs-lookup"><span data-stu-id="6460e-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="6460e-119">Konflikty časování v finalizačních podmínkách</span><span class="sxs-lookup"><span data-stu-id="6460e-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="6460e-120">Ke konfliktům časování může dojít také v objektu, který odkazuje na statický nebo nespravovaný prostředek, který je poté uvolněn v jeho finalizační metodě.</span><span class="sxs-lookup"><span data-stu-id="6460e-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="6460e-121">Pokud více objektů sdílí prostředek, který je manipulován v finalizační metodě třídy, musí objekty synchronizovat veškerý přístup k tomuto prostředku.</span><span class="sxs-lookup"><span data-stu-id="6460e-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6460e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="6460e-122">See also</span></span>

- [<span data-ttu-id="6460e-123">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="6460e-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
