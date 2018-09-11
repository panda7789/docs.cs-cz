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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ceaedc7c38ae70a0db5a7fd584a765a7474aff
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339336"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="ec27a-102">Zabezpečení a konflikty časování</span><span class="sxs-lookup"><span data-stu-id="ec27a-102">Security and Race Conditions</span></span>
<span data-ttu-id="ec27a-103">Další oblastí zájmu je potenciální bezpečnostní rizika zneužité časování.</span><span class="sxs-lookup"><span data-stu-id="ec27a-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="ec27a-104">Existuje několik způsobů, ve kterých k tomu může dojít.</span><span class="sxs-lookup"><span data-stu-id="ec27a-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="ec27a-105">Související témata, které následují popisují některé z hlavních problémů, které musí vývojáři vyhnout.</span><span class="sxs-lookup"><span data-stu-id="ec27a-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="ec27a-106">Časování v metody Dispose</span><span class="sxs-lookup"><span data-stu-id="ec27a-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="ec27a-107">Případě, že třída **Dispose** – metoda (Další informace najdete v tématu [uvolňování](../../../docs/standard/garbage-collection/index.md)) není synchronizována, je možné tento kód pro vyčištění uvnitř **Dispose** můžete spustit více než jednou, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ec27a-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ec27a-108">Protože toto **Dispose** implementace není synchronizovaný, je možné, `Cleanup` má být volána nejprve jedno vlákno a pak druhého podprocesu před `_myObj` je nastavena na **null**.</span><span class="sxs-lookup"><span data-stu-id="ec27a-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="ec27a-109">Zda se jedná o problém zabezpečení závisí na co se stane, když `Cleanup` spuštěn kód.</span><span class="sxs-lookup"><span data-stu-id="ec27a-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="ec27a-110">Hlavní problém s nesynchronizované **Dispose** implementací zahrnuje použití popisovače prostředku, jako jsou například soubory.</span><span class="sxs-lookup"><span data-stu-id="ec27a-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="ec27a-111">Nesprávné odstranění může způsobit nesprávné popisovač, kterou chcete použít, což často vede k ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ec27a-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="ec27a-112">Časování v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="ec27a-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="ec27a-113">V některých aplikacích je možné pro ostatní vlákna pro přístup ke členům třídy před jejich konstruktor třídy zcela spustili.</span><span class="sxs-lookup"><span data-stu-id="ec27a-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="ec27a-114">Měli byste zkontrolovat všechny třídy konstruktory, abyste měli jistotu, že pokud k tomu musí dojít, nebo synchronizaci vláken, v případě potřeby neexistují žádné problémy se zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="ec27a-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="ec27a-115">Ke konfliktům časování s objekty uložené v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="ec27a-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="ec27a-116">Kód, který ukládá informace o zabezpečení nebo který používá zabezpečení přístupu kódu [Assert](../../../docs/framework/misc/using-the-assert-method.md) operace může být také snadno napadnutelný časování Pokud jiné části třídy nejsou synchronizované odpovídajícím způsobem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ec27a-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ec27a-117">Pokud existují další cesty k `DoOtherWork` , který lze volat z jiného vlákna se stejným objektem, nedůvěryhodné volající může zpozdit poslední požadavek.</span><span class="sxs-lookup"><span data-stu-id="ec27a-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="ec27a-118">Pokud váš kód mezipaměti informace o zabezpečení, ujistěte se, abyste si pro toto ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ec27a-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="ec27a-119">Časování v finalizační metody</span><span class="sxs-lookup"><span data-stu-id="ec27a-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="ec27a-120">V objektu, který odkazuje na statickou nebo nespravovaný prostředek, který poté uvolní v jeho finalizační metoda může také dojít ke konfliktům časování.</span><span class="sxs-lookup"><span data-stu-id="ec27a-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="ec27a-121">Pokud více objektů sdílí prostředek, který je zpracováván v finalizační metodu třídy, musíte synchronizovat objekty veškerý přístup k prostředku.</span><span class="sxs-lookup"><span data-stu-id="ec27a-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec27a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec27a-122">See also</span></span>

- [<span data-ttu-id="ec27a-123">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="ec27a-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
