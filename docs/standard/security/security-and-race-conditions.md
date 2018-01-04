---
title: "Zabezpečení a konflikty časování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 73664df9c072189f11d451da46bc3019c8593ec9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="8325d-102">Zabezpečení a konflikty časování</span><span class="sxs-lookup"><span data-stu-id="8325d-102">Security and Race Conditions</span></span>
<span data-ttu-id="8325d-103">Další oblastí zájmu je potenciální bezpečnostní rizika zneužité časování.</span><span class="sxs-lookup"><span data-stu-id="8325d-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="8325d-104">Existuje několik způsobů, ve kterých k tomu může dojít.</span><span class="sxs-lookup"><span data-stu-id="8325d-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="8325d-105">Související témata, které následují popisují některé z hlavních problémů, kterým musí vývojář vyhnout.</span><span class="sxs-lookup"><span data-stu-id="8325d-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="8325d-106">Konflikty časování v metodu Dispose</span><span class="sxs-lookup"><span data-stu-id="8325d-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="8325d-107">Pokud na třídu **Dispose** – metoda (Další informace najdete v tématu [uvolňování paměti](../../../docs/standard/garbage-collection/index.md)) není synchronizována, je možné tento kód čištění uvnitř **Dispose** lze spustit více než jednou, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8325d-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="8325d-108">Protože to **Dispose** implementace není synchronizována, je možné pro `Cleanup` má být volána nejprve jedno vlákno a pak druhý vlákno před `_myObj` je nastaven na **null**.</span><span class="sxs-lookup"><span data-stu-id="8325d-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="8325d-109">Jestli se jedná o problém zabezpečení závisí na co se stane, když `Cleanup` kód běží.</span><span class="sxs-lookup"><span data-stu-id="8325d-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="8325d-110">Hlavní problém s nesynchronizovaných **Dispose** implementací zahrnuje použití popisovače prostředku, jako jsou například soubory.</span><span class="sxs-lookup"><span data-stu-id="8325d-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="8325d-111">Nesprávné odstranění může způsobit nesprávnou popisovač použije, což často vede k ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8325d-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="8325d-112">Konflikty časování v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="8325d-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="8325d-113">V některých aplikacích může být jiná vlákna přístup ke členům třídy před jejich konstruktory třídy zcela spustí.</span><span class="sxs-lookup"><span data-stu-id="8325d-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="8325d-114">Měli byste zkontrolovat všechny třídy konstruktory a ujistěte se, že pokud tomu má dojít, nebo synchronizovat vláken v případě potřeby neexistují žádné problémy se zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="8325d-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="8325d-115">Konflikty časování s objekty v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="8325d-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="8325d-116">Kód, který ukládá do mezipaměti informace o zabezpečení nebo používá zabezpečení přístupu kódu [Assert](../../../docs/framework/misc/using-the-assert-method.md) operace může být ohrožen časování Pokud dalších částí třídy nejsou správně synchronizovány, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8325d-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
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
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
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
  
 <span data-ttu-id="8325d-117">Pokud jsou jiné cesty k `DoOtherWork` , lze volat z jiného vlákna se stejný objekt, nedůvěryhodný volající může proklouznout požadavku.</span><span class="sxs-lookup"><span data-stu-id="8325d-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="8325d-118">Pokud váš kód ukládá do mezipaměti informace o zabezpečení, ujistěte se, zkontrolujte pro toto ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8325d-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="8325d-119">Konflikty časování v finalizační metody</span><span class="sxs-lookup"><span data-stu-id="8325d-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="8325d-120">Konflikty časování může dojít také v objektu, který odkazuje na statickou nebo nespravovaný prostředek, který poté uvolní v jeho finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="8325d-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="8325d-121">Pokud více objektů sdílet na prostředek, který je v finalizační metodu třídy a s nimi manipulovat, musí synchronizovat objekty veškerý přístup k prostředku.</span><span class="sxs-lookup"><span data-stu-id="8325d-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8325d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8325d-122">See Also</span></span>  
 [<span data-ttu-id="8325d-123">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="8325d-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
