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
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186783"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="6b6dc-102">Zabezpečení a konflikty časování</span><span class="sxs-lookup"><span data-stu-id="6b6dc-102">Security and Race Conditions</span></span>
<span data-ttu-id="6b6dc-103">Další oblastí zájmu je potenciál pro bezpečnostní díry využívané rasovými podmínkami.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="6b6dc-104">Existuje několik způsobů, jak k tomu může dojít.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="6b6dc-105">Dílčí témata, které následují, popisují některé z hlavních úskalí, kterým se vývojář musí vyhnout.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="6b6dc-106">Sporné podmínky v metodě dispose</span><span class="sxs-lookup"><span data-stu-id="6b6dc-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="6b6dc-107">Pokud metoda **Dispose** třídy (další informace naleznete v [tématu Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)) ) není synchronizována, je možné, že vyčištění kódu uvnitř **Dispose** lze spustit více než jednou, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6b6dc-108">Vzhledem k **tomu, že** tato implementace `Cleanup` Dispose není synchronizována, je možné `_myObj` volat první vlákno a potom druhé vlákno před je nastavena na **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="6b6dc-109">Zda se jedná o problém zabezpečení `Cleanup` závisí na tom, co se stane při spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="6b6dc-110">Hlavní problém s nesynchronizované **dispose** implementace zahrnuje použití popisovače prostředků, jako jsou soubory.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="6b6dc-111">Nesprávné vyřazení může způsobit použití nesprávného popisovače, což často vede k ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="6b6dc-112">Závodní podmínky v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="6b6dc-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="6b6dc-113">V některých aplikacích může být možné pro jiné podprocesy pro přístup členů třídy před jejich konstruktory třídy mají zcela spustit.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="6b6dc-114">Měli byste zkontrolovat všechny konstruktory třídy a ujistěte se, že neexistují žádné problémy se zabezpečením, pokud k tomu dojde, nebo v případě potřeby synchronizovat vlákna.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="6b6dc-115">Podmínky časovoleb s objekty uloženými v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="6b6dc-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="6b6dc-116">Kód, který ukládá do mezipaměti informace o zabezpečení nebo používá operaci [Assert](../../../docs/framework/misc/using-the-assert-method.md) zabezpečení přístupu kódu, může být také zranitelný vůči časovacím podmínkám, pokud ostatní části třídy nejsou odpovídajícím způsobem synchronizovány, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6b6dc-117">Pokud existují jiné cesty, `DoOtherWork` které mohou být volány z jiného vlákna se stejným objektem, nedůvěryhodný volající může proklouznout kolem poptávky.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="6b6dc-118">Pokud váš kód ukládá informace o zabezpečení do mezipaměti, zkontrolujte, zda se jedná o tuto chybu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="6b6dc-119">Podmínky závodu ve finalizačních metodách</span><span class="sxs-lookup"><span data-stu-id="6b6dc-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="6b6dc-120">Časování podmínky může dojít také v objektu, který odkazuje na statický nebo nespravovaný prostředek, který pak uvolní ve své finalizační metodě.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="6b6dc-121">Pokud více objektů sdílet prostředek, který je manipulováno ve finalizační metodě třídy, musí objekty synchronizovat veškerý přístup k tomuto prostředku.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b6dc-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b6dc-122">See also</span></span>

- [<span data-ttu-id="6b6dc-123">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="6b6dc-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
