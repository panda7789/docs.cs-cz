---
title: Dispose – vzor
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdcb746ae2d8c2262b0cd0c6c9dcaababb12bd63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578986"
---
# <a name="dispose-pattern"></a><span data-ttu-id="d55da-102">Dispose – vzor</span><span class="sxs-lookup"><span data-stu-id="d55da-102">Dispose Pattern</span></span>
<span data-ttu-id="d55da-103">Všechny programy získat jeden nebo více systémových prostředků, například paměť, popisovače systému nebo připojení databáze, v průběhu jejich provádění.</span><span class="sxs-lookup"><span data-stu-id="d55da-103">All programs acquire one or more system resources, such as memory, system handles, or database connections, during the course of their execution.</span></span> <span data-ttu-id="d55da-104">Vývojáři mají být opatrní při použití takových systémové prostředky, protože musí být vydané po svém získat a použít.</span><span class="sxs-lookup"><span data-stu-id="d55da-104">Developers have to be careful when using such system resources, because they must be released after they have been acquired and used.</span></span>  
  
 <span data-ttu-id="d55da-105">Modul CLR poskytuje podporu pro automatická správa paměti.</span><span class="sxs-lookup"><span data-stu-id="d55da-105">The CLR provides support for automatic memory management.</span></span> <span data-ttu-id="d55da-106">Spravované paměti (paměť přidělená pomocí operátoru jazyka C# `new`) nemusí být explicitně vydání.</span><span class="sxs-lookup"><span data-stu-id="d55da-106">Managed memory (memory allocated using the C# operator `new`) does not need to be explicitly released.</span></span> <span data-ttu-id="d55da-107">Je vydala automaticky modulem garbage collector (GC).</span><span class="sxs-lookup"><span data-stu-id="d55da-107">It is released automatically by the garbage collector (GC).</span></span> <span data-ttu-id="d55da-108">Tím uvolní vývojáři z zdlouhavé a složité úlohy uvolňování paměti a musí být jedním z hlavních důvodů pro nebývalá produktivitu poskytované rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d55da-108">This frees developers from the tedious and difficult task of releasing memory and has been one of the main reasons for the unprecedented productivity afforded by the .NET Framework.</span></span>  
  
 <span data-ttu-id="d55da-109">Bohužel spravované paměti se právě jeden z mnoha typů prostředků systému.</span><span class="sxs-lookup"><span data-stu-id="d55da-109">Unfortunately, managed memory is just one of many types of system resources.</span></span> <span data-ttu-id="d55da-110">Prostředky než spravované paměti stále potřeba explicitně vydané a jsou označovány jako nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="d55da-110">Resources other than managed memory still need to be released explicitly and are referred to as unmanaged resources.</span></span> <span data-ttu-id="d55da-111">Globální Katalog se konkrétně není navržená ke správě takové nespravované prostředky, což znamená, že odpovědnost za správu nespravované prostředky leží do nesprávných rukou vývojáři.</span><span class="sxs-lookup"><span data-stu-id="d55da-111">The GC was specifically not designed to manage such unmanaged resources, which means that the responsibility for managing unmanaged resources lies in the hands of the developers.</span></span>  
  
 <span data-ttu-id="d55da-112">Modul CLR poskytuje pomoc v uvolnění nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="d55da-112">The CLR provides some help in releasing unmanaged resources.</span></span> <span data-ttu-id="d55da-113"><xref:System.Object?displayProperty=nameWithType> deklaruje virtuální metoda <xref:System.Object.Finalize%2A> (také nazývané finalizační metodu), je volána metodou globální Katalog před paměti objektu je požadovaná globální Katalog a může být potlačena za účelem uvolnění nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="d55da-113"><xref:System.Object?displayProperty=nameWithType> declares a virtual method <xref:System.Object.Finalize%2A> (also called the finalizer) that is called by the GC before the object’s memory is reclaimed by the GC and can be overridden to release unmanaged resources.</span></span> <span data-ttu-id="d55da-114">Typy, které potlačí finalizační metodu jsou označovány jako finalizable typy.</span><span class="sxs-lookup"><span data-stu-id="d55da-114">Types that override the finalizer are referred to as finalizable types.</span></span>  
  
 <span data-ttu-id="d55da-115">I když finalizační metody jsou platné v některých scénářích čištění, mají dvě důležité nevýhody:</span><span class="sxs-lookup"><span data-stu-id="d55da-115">Although finalizers are effective in some cleanup scenarios, they have two significant drawbacks:</span></span>  
  
-   <span data-ttu-id="d55da-116">Finalizační metodu je volána, když globální Katalog zjistí, že objekt je vhodné pro kolekci.</span><span class="sxs-lookup"><span data-stu-id="d55da-116">The finalizer is called when the GC detects that an object is eligible for collection.</span></span> <span data-ttu-id="d55da-117">K tomu dojde při některých neurčená časovém intervalu po už není potřeba prostředek.</span><span class="sxs-lookup"><span data-stu-id="d55da-117">This happens at some undetermined period of time after the resource is not needed anymore.</span></span> <span data-ttu-id="d55da-118">Zpoždění mezi při může vývojář, nebo chcete verzi prostředku a čas, kdy prostředek ve skutečnosti vydal finalizační metodu může nepřijatelné v programech, které získat mnoho omezených prostředky (prostředky, které můžete snadno vyčerpán) nebo v případy, ve kterých jsou prostředky nákladná zachovat používá (například vyrovnávací paměti velkých nespravované paměti).</span><span class="sxs-lookup"><span data-stu-id="d55da-118">The delay between when the developer could or would like to release the resource and the time when the resource is actually released by the finalizer might be unacceptable in programs that acquire many scarce resources (resources that can be easily exhausted) or in cases in which resources are costly to keep in use (e.g., large unmanaged memory buffers).</span></span>  
  
-   <span data-ttu-id="d55da-119">Když modulu CLR potřebuje volat finalizační metody, se musí odložit kolekce paměti objektu dokud další zaokrouhlit uvolnění paměti (finalizační metody spustit mezi kolekce).</span><span class="sxs-lookup"><span data-stu-id="d55da-119">When the CLR needs to call a finalizer, it must postpone collection of the object’s memory until the next round of garbage collection (the finalizers run between collections).</span></span> <span data-ttu-id="d55da-120">To znamená, že objektu paměti (a všechny objekty, které se odkazuje) nebude vydané pro delší časové období.</span><span class="sxs-lookup"><span data-stu-id="d55da-120">This means that the object’s memory (and all objects it refers to) will not be released for a longer period of time.</span></span>  
  
 <span data-ttu-id="d55da-121">Tedy spoléhat výhradně na finalizační metody nemusí být vhodné v mnoha scénářích, když je potřeba provést co nejrychleji, uvolnění nespravovaných prostředků při plánování práce s omezených prostředků, nebo vysoce původce scénářů, ve kterých přidané režii uvolňování paměti Finalizace nepřijatelné.</span><span class="sxs-lookup"><span data-stu-id="d55da-121">Therefore, relying exclusively on finalizers might not be appropriate in many scenarios when it is important to reclaim unmanaged resources as quickly as possible, when dealing with scarce resources, or in highly performant scenarios in which the added GC overhead of finalization is unacceptable.</span></span>  
  
 <span data-ttu-id="d55da-122">Poskytuje rozhraní <xref:System.IDisposable?displayProperty=nameWithType> rozhraní, které by měla být implementována zajistit vývojář manuální způsob, jak co nejrychleji nejsou potřeba uvolnění nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="d55da-122">The Framework provides the <xref:System.IDisposable?displayProperty=nameWithType> interface that should be implemented to provide the developer a manual way to release unmanaged resources as soon as they are not needed.</span></span> <span data-ttu-id="d55da-123">Také poskytuje <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> metoda, která se dá zjistit globální Katalog, který objekt ručně vyřazena a nemusí být dokončen už, v takovém případě objektu paměť se nedá uvolnit dříve.</span><span class="sxs-lookup"><span data-stu-id="d55da-123">It also provides the <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> method that can tell the GC that an object was manually disposed of and does not need to be finalized anymore, in which case the object’s memory can be reclaimed earlier.</span></span> <span data-ttu-id="d55da-124">Typy, které implementují `IDisposable` rozhraní jsou označovány jako uvolnitelné typy.</span><span class="sxs-lookup"><span data-stu-id="d55da-124">Types that implement the `IDisposable` interface are referred to as disposable types.</span></span>  
  
 <span data-ttu-id="d55da-125">Vzor Dispose je určený pro standardizaci využití a provádění finalizační metody a `IDisposable` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d55da-125">The Dispose Pattern is intended to standardize the usage and implementation of finalizers and the `IDisposable` interface.</span></span>  
  
 <span data-ttu-id="d55da-126">Hlavní motivace pro vzor je ke snížení složitosti implementace <xref:System.Object.Finalize%2A> a <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d55da-126">The main motivation for the pattern is to reduce the complexity of the implementation of the <xref:System.Object.Finalize%2A> and the <xref:System.IDisposable.Dispose%2A> methods.</span></span> <span data-ttu-id="d55da-127">Složitost vyplývá z faktu, že metody sdílet některé, ale ne všechny cesty kódu (rozdíly jsou popsány dále v kapitole).</span><span class="sxs-lookup"><span data-stu-id="d55da-127">The complexity stems from the fact that the methods share some but not all code paths (the differences are described later in the chapter).</span></span> <span data-ttu-id="d55da-128">Kromě toho jsou historických důvody pro některé prvky vzoru související s vývoj jazyková podpora pro správu prostředků deterministický.</span><span class="sxs-lookup"><span data-stu-id="d55da-128">In addition, there are historical reasons for some elements of the pattern related to the evolution of language support for deterministic resource management.</span></span>  
  
 <span data-ttu-id="d55da-129">**PROVEĎTE ✓** implementace základní Dispose vzoru na typy obsahující instance uvolnitelné typy.</span><span class="sxs-lookup"><span data-stu-id="d55da-129">**✓ DO** implement the Basic Dispose Pattern on types containing instances of disposable types.</span></span> <span data-ttu-id="d55da-130">Najdete v článku [základní vzor Dispose](#basic_pattern) část Podrobnosti o základní vzor.</span><span class="sxs-lookup"><span data-stu-id="d55da-130">See the [Basic Dispose Pattern](#basic_pattern) section for details on the basic pattern.</span></span>  
  
 <span data-ttu-id="d55da-131">Pokud je zodpovědná za dobu životnosti jiné na jedno použití objekty typu, vývojáři potřebovat způsob, jak k uvolnění z nich, příliš.</span><span class="sxs-lookup"><span data-stu-id="d55da-131">If a type is responsible for the lifetime of other disposable objects, developers need a way to dispose of them, too.</span></span> <span data-ttu-id="d55da-132">Pomocí kontejneru `Dispose` metoda je pohodlný způsob, jak to umožňují.</span><span class="sxs-lookup"><span data-stu-id="d55da-132">Using the container’s `Dispose` method is a convenient way to make this possible.</span></span>  
  
 <span data-ttu-id="d55da-133">**PROVEĎTE ✓** implementovat základní vzor Dispose a zadejte finalizační metody pro typy prostředků podniku, které je potřeba explicitně uvolnit a které nemají finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="d55da-133">**✓ DO** implement the Basic Dispose Pattern and provide a finalizer on types holding resources that need to be freed explicitly and that do not have finalizers.</span></span>  
  
 <span data-ttu-id="d55da-134">Například by měla být implementována vzoru na typy ukládání nespravované paměti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d55da-134">For example, the pattern should be implemented on types storing unmanaged memory buffers.</span></span> <span data-ttu-id="d55da-135">[Finalizable typy](#finalizable_types) část popisuje pokyny týkající se implementace finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="d55da-135">The [Finalizable Types](#finalizable_types) section discusses guidelines related to implementing finalizers.</span></span>  
  
 <span data-ttu-id="d55da-136">**✓ ZVAŽTE** implementace vzoru Dispose základní na třídách sami nemáte uložení nespravovaných prostředků nebo na jedno použití objekty jsou ale mohou mít podtypů, které provádějí.</span><span class="sxs-lookup"><span data-stu-id="d55da-136">**✓ CONSIDER** implementing the Basic Dispose Pattern on classes that themselves don’t hold unmanaged resources or disposable objects but are likely to have subtypes that do.</span></span>  
  
 <span data-ttu-id="d55da-137">Je to skvělý například <xref:System.IO.Stream?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="d55da-137">A great example of this is the <xref:System.IO.Stream?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d55da-138">Přestože je abstraktní základní třída, která nebude obsahovat žádné prostředky, nezadávejte většinu jeho podtřídy a z toho důvodu se implementuje tohoto vzoru.</span><span class="sxs-lookup"><span data-stu-id="d55da-138">Although it is an abstract base class that doesn’t hold any resources, most of its subclasses do and because of this, it implements this pattern.</span></span>  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a><span data-ttu-id="d55da-139">Dispose základní vzor</span><span class="sxs-lookup"><span data-stu-id="d55da-139">Basic Dispose Pattern</span></span>  
 <span data-ttu-id="d55da-140">Základní implementace vzoru zahrnuje implementace `System.IDisposable` rozhraní a deklarace `Dispose(bool)` metodu, která implementuje veškerou logiku vyčištění prostředků se dělí `Dispose` metoda a volitelné finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="d55da-140">The basic implementation of the pattern involves implementing the `System.IDisposable` interface and declaring the `Dispose(bool)` method that implements all resource cleanup logic to be shared between the `Dispose` method and the optional finalizer.</span></span>  
  
 <span data-ttu-id="d55da-141">Následující příklad ukazuje jednoduchou implementaci základní vzor:</span><span class="sxs-lookup"><span data-stu-id="d55da-141">The following example shows a simple implementation of the basic pattern:</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="d55da-142">Logická hodnota parametru `disposing` označuje, zda byla vyvolána metoda z `IDisposable.Dispose` implementace nebo z finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="d55da-142">The Boolean parameter `disposing` indicates whether the method was invoked from the `IDisposable.Dispose` implementation or from the finalizer.</span></span> <span data-ttu-id="d55da-143">`Dispose(bool)` Implementace měli zkontrolovat parametr před přístupem k jiné odkaz na objekty (například pole zdroje v předchozím příkladu).</span><span class="sxs-lookup"><span data-stu-id="d55da-143">The `Dispose(bool)` implementation should check the parameter before accessing other reference objects (e.g., the resource field in the preceding sample).</span></span> <span data-ttu-id="d55da-144">Tyto objekty by měly být dostupné jenom při metoda je volána z `IDisposable.Dispose` implementace (když `disposing` rovná parametru na hodnotu true).</span><span class="sxs-lookup"><span data-stu-id="d55da-144">Such objects should only be accessed when the method is called from the `IDisposable.Dispose` implementation (when the `disposing` parameter is equal to true).</span></span> <span data-ttu-id="d55da-145">Pokud metoda je volána z finalizační metodu (`disposing` je false), by neměl přístup k jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="d55da-145">If the method is invoked from the finalizer (`disposing` is false), other objects should not be accessed.</span></span> <span data-ttu-id="d55da-146">Důvodem je, že objekty jsou dokončeny v nepředvídatelným pořadí a tak se ani žádné z jejich závislosti, může již mít byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="d55da-146">The reason is that objects are finalized in an unpredictable order and so they, or any of their dependencies, might already have been finalized.</span></span>  
  
 <span data-ttu-id="d55da-147">Tato část platí také, pro třídy na bázi, který již neimplementuje vzoru Dispose.</span><span class="sxs-lookup"><span data-stu-id="d55da-147">Also, this section applies to classes with a base that does not already implement the Dispose Pattern.</span></span> <span data-ttu-id="d55da-148">Pokud se dědí z třídy, která již implementuje vzor, jednoduše přepsat `Dispose(bool)` metody můžete zajistit logiku čištění dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="d55da-148">If you are inheriting from a class that already implements the pattern, simply override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="d55da-149">**PROVEĎTE ✓** deklarovat `protected virtual void Dispose(bool disposing)` metoda a centralizovat veškerou logiku s uvolňováním nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="d55da-149">**✓ DO** declare a `protected virtual void Dispose(bool disposing)` method to centralize all logic related to releasing unmanaged resources.</span></span>  
  
 <span data-ttu-id="d55da-150">Tato metoda by měla dojít všechny vyčištění prostředků.</span><span class="sxs-lookup"><span data-stu-id="d55da-150">All resource cleanup should occur in this method.</span></span> <span data-ttu-id="d55da-151">Metoda je volána z obou finalizační metodu a `IDisposable.Dispose` metoda.</span><span class="sxs-lookup"><span data-stu-id="d55da-151">The method is called from both the finalizer and the `IDisposable.Dispose` method.</span></span> <span data-ttu-id="d55da-152">Parametr bude mít hodnotu false, pokud volané z uvnitř finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="d55da-152">The parameter will be false if being invoked from inside a finalizer.</span></span> <span data-ttu-id="d55da-153">Slouží k zajištění, že jakýkoli kód spuštěn během dokončení není přístup k jiné finalizable objekty.</span><span class="sxs-lookup"><span data-stu-id="d55da-153">It should be used to ensure any code running during finalization is not accessing other finalizable objects.</span></span> <span data-ttu-id="d55da-154">Podrobnosti implementace finalizační metody jsou popsané v další části.</span><span class="sxs-lookup"><span data-stu-id="d55da-154">Details of implementing finalizers are described in the next section.</span></span>  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 <span data-ttu-id="d55da-155">**PROVEĎTE ✓** implementovat `IDisposable` rozhraní jednoduše voláním `Dispose(true)` následuje `GC.SuppressFinalize(this)`.</span><span class="sxs-lookup"><span data-stu-id="d55da-155">**✓ DO** implement the `IDisposable` interface by simply calling `Dispose(true)` followed by `GC.SuppressFinalize(this)`.</span></span>  
  
 <span data-ttu-id="d55da-156">Volání `SuppressFinalize` by měl použít pouze v případě `Dispose(true)` úspěšně spustí.</span><span class="sxs-lookup"><span data-stu-id="d55da-156">The call to `SuppressFinalize` should only occur if `Dispose(true)` executes successfully.</span></span>  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 <span data-ttu-id="d55da-157">**X nesmí** zkontrolujte bezparametrový `Dispose` metoda virtuální.</span><span class="sxs-lookup"><span data-stu-id="d55da-157">**X DO NOT** make the parameterless `Dispose` method virtual.</span></span>  
  
 <span data-ttu-id="d55da-158">`Dispose(bool)` Metoda je ten, který by měla být potlačena podtřídy.</span><span class="sxs-lookup"><span data-stu-id="d55da-158">The `Dispose(bool)` method is the one that should be overridden by subclasses.</span></span>  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 <span data-ttu-id="d55da-159">**X nesmí** deklarovat žádné přetížení `Dispose` jinak než `Dispose()` a `Dispose(bool)`.</span><span class="sxs-lookup"><span data-stu-id="d55da-159">**X DO NOT** declare any overloads of the `Dispose` method other than `Dispose()` and `Dispose(bool)`.</span></span>  
  
 <span data-ttu-id="d55da-160">`Dispose` měli byste zvážit vyhrazené slovo pomohou kodifikovat tohoto vzoru a nedošlo k záměně mezi implementátory informačních technologií, uživatelů a kompilátory.</span><span class="sxs-lookup"><span data-stu-id="d55da-160">`Dispose` should be considered a reserved word to help codify this pattern and prevent confusion among implementers, users, and compilers.</span></span> <span data-ttu-id="d55da-161">Některé jazyky vybrat automaticky implementovat tento vzor na určité typy.</span><span class="sxs-lookup"><span data-stu-id="d55da-161">Some languages might choose to automatically implement this pattern on certain types.</span></span>  
  
 <span data-ttu-id="d55da-162">**PROVEĎTE ✓** povolit `Dispose(bool)` metoda, která se má volat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="d55da-162">**✓ DO** allow the `Dispose(bool)` method to be called more than once.</span></span> <span data-ttu-id="d55da-163">Zvolit metodu se nic nestane. po prvním volání.</span><span class="sxs-lookup"><span data-stu-id="d55da-163">The method might choose to do nothing after the first call.</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="d55da-164">**X nepoužívejte** došlo k výjimce z uvnitř `Dispose(bool)` nejsou pod kritických situací, kdy je proces obsahující poškozená (nevracení, nekonzistentní sdíleného stavu atd.).</span><span class="sxs-lookup"><span data-stu-id="d55da-164">**X AVOID** throwing an exception from within `Dispose(bool)` except under critical situations where the containing process has been corrupted (leaks, inconsistent shared state, etc.).</span></span>  
  
 <span data-ttu-id="d55da-165">Uživatelé očekávají, že který volání `Dispose` nebude vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="d55da-165">Users expect that a call to `Dispose` will not raise an exception.</span></span>  
  
 <span data-ttu-id="d55da-166">Pokud `Dispose` může vyvolat výjimku, nebude spustit další blok finally čištění logiky.</span><span class="sxs-lookup"><span data-stu-id="d55da-166">If `Dispose` could raise an exception, further finally-block cleanup logic will not execute.</span></span> <span data-ttu-id="d55da-167">Chcete-li tento problém obejít, bude uživatel muset zabalení každé volání `Dispose` (v rámci nakonec blokovat!) v bloku try, což vede k velmi složité čištění obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="d55da-167">To work around this, the user would need to wrap every call to `Dispose` (within the finally block!) in a try block, which leads to very complex cleanup handlers.</span></span> <span data-ttu-id="d55da-168">Pokud provádění `Dispose(bool disposing)` metoda, nikdy throw výjimku, pokud uvolnění je false.</span><span class="sxs-lookup"><span data-stu-id="d55da-168">If executing a `Dispose(bool disposing)` method, never throw an exception if disposing is false.</span></span> <span data-ttu-id="d55da-169">Díky tomu bude ukončit proces, pokud provádění uvnitř kontextu finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="d55da-169">Doing so will terminate the process if executing inside a finalizer context.</span></span>  
  
 <span data-ttu-id="d55da-170">**PROVEĎTE ✓** throw <xref:System.ObjectDisposedException> z kteréhokoli člena, který nelze použít po objekt byl vyřazen.</span><span class="sxs-lookup"><span data-stu-id="d55da-170">**✓ DO** throw an <xref:System.ObjectDisposedException> from any member that cannot be used after the object has been disposed of.</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="d55da-171">**✓ ZVAŽTE** poskytuje metoda `Close()`, kromě `Dispose()`, pokud je zavřete standardní terminologii v oblasti.</span><span class="sxs-lookup"><span data-stu-id="d55da-171">**✓ CONSIDER** providing method `Close()`, in addition to the `Dispose()`, if close is standard terminology in the area.</span></span>  
  
 <span data-ttu-id="d55da-172">Když to uděláte, je důležité, abyste vytvořili `Close` implementace identické `Dispose` a zvažte implementaci `IDisposable.Dispose` metoda explicitně.</span><span class="sxs-lookup"><span data-stu-id="d55da-172">When doing so, it is important that you make the `Close` implementation identical to `Dispose` and consider implementing the `IDisposable.Dispose` method explicitly.</span></span>  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a><span data-ttu-id="d55da-173">Finalizable typy</span><span class="sxs-lookup"><span data-stu-id="d55da-173">Finalizable Types</span></span>  
 <span data-ttu-id="d55da-174">Finalizable typy jsou typy, které rozšiřují základní vzor Dispose přepsání finalizační metodu a poskytnutím finalizace kódové cestě v `Dispose(bool)` metoda.</span><span class="sxs-lookup"><span data-stu-id="d55da-174">Finalizable types are types that extend the Basic Dispose Pattern by overriding the finalizer and providing finalization code path in the `Dispose(bool)` method.</span></span>  
  
 <span data-ttu-id="d55da-175">Finalizační metody jsou často těžké implementovat správně, především proto nelze provádět určité předpoklady (obvykle platný) o stavu systému při jejich provádění.</span><span class="sxs-lookup"><span data-stu-id="d55da-175">Finalizers are notoriously difficult to implement correctly, primarily because you cannot make certain (normally valid) assumptions about the state of the system during their execution.</span></span> <span data-ttu-id="d55da-176">Následující pokyny měli vzít v úvahu opatrní.</span><span class="sxs-lookup"><span data-stu-id="d55da-176">The following guidelines should be taken into careful consideration.</span></span>  
  
 <span data-ttu-id="d55da-177">Nezapomeňte, že některé pokyny platí není právě k `Finalize` metoda, ale pro jakýkoli kód volat z finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="d55da-177">Note that some of the guidelines apply not just to the `Finalize` method, but to any code called from a finalizer.</span></span> <span data-ttu-id="d55da-178">V případě základní Dispose vzor předtím definovaný, to znamená logiky, která provede uvnitř `Dispose(bool disposing)` při `disposing` parametr je false.</span><span class="sxs-lookup"><span data-stu-id="d55da-178">In the case of the Basic Dispose Pattern previously defined, this means logic that executes inside `Dispose(bool disposing)` when the `disposing` parameter is false.</span></span>  
  
 <span data-ttu-id="d55da-179">Pokud základní třídy již je finalizable a implementuje základní vzor Dispose, by neměl přepsat `Finalize` znovu.</span><span class="sxs-lookup"><span data-stu-id="d55da-179">If the base class already is finalizable and implements the Basic Dispose Pattern, you should not override `Finalize` again.</span></span> <span data-ttu-id="d55da-180">Měli byste místo toho právě přepsat `Dispose(bool)` metody můžete zajistit logiku čištění dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="d55da-180">You should instead just override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="d55da-181">Následující kód ukazuje příklad finalizable typu:</span><span class="sxs-lookup"><span data-stu-id="d55da-181">The following code shows an example of a finalizable type:</span></span>  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 <span data-ttu-id="d55da-182">**X nepoužívejte** provedení finalizable typy.</span><span class="sxs-lookup"><span data-stu-id="d55da-182">**X AVOID** making types finalizable.</span></span>  
  
 <span data-ttu-id="d55da-183">Pečlivě zvažte žádné případ, ve kterém si myslíte, že je potřeba finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="d55da-183">Carefully consider any case in which you think a finalizer is needed.</span></span> <span data-ttu-id="d55da-184">Je o skutečné náklady spojené s instancemi s finalizační metody, z hlediska výkonu i kód složitost.</span><span class="sxs-lookup"><span data-stu-id="d55da-184">There is a real cost associated with instances with finalizers, from both a performance and code complexity standpoint.</span></span> <span data-ttu-id="d55da-185">Dáváte přednost pomocí obálky prostředků, jako třeba <xref:System.Runtime.InteropServices.SafeHandle> k zapouzdření nespravovaných prostředků, kde je to možné, v takovém případě finalizační metody stane nepotřebné protože obálku zodpovídá za vlastní vyčištění prostředků.</span><span class="sxs-lookup"><span data-stu-id="d55da-185">Prefer using resource wrappers such as <xref:System.Runtime.InteropServices.SafeHandle> to encapsulate unmanaged resources where possible, in which case a finalizer becomes unnecessary because the wrapper is responsible for its own resource cleanup.</span></span>  
  
 <span data-ttu-id="d55da-186">**X nesmí** zkontrolujte finalizable typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="d55da-186">**X DO NOT** make value types finalizable.</span></span>  
  
 <span data-ttu-id="d55da-187">Pouze typy odkazů ve skutečnosti získat CLR dokončené, a proto bude ignorována pokusy o umístit finalizační metody na typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d55da-187">Only reference types actually get finalized by the CLR, and thus any attempt to place a finalizer on a value type will be ignored.</span></span> <span data-ttu-id="d55da-188">C# a C++ kompilátory vynutit toto pravidlo.</span><span class="sxs-lookup"><span data-stu-id="d55da-188">The C# and C++ compilers enforce this rule.</span></span>  
  
 <span data-ttu-id="d55da-189">**PROVEĎTE ✓** zkontrolujte finalizable typu, pokud typ je zodpovědná za uvolnění nespravovaných zdrojů, který nemá vlastní finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="d55da-189">**✓ DO** make a type finalizable if the type is responsible for releasing an unmanaged resource that does not have its own finalizer.</span></span>  
  
 <span data-ttu-id="d55da-190">Při implementaci finalizační metodu, jednoduše volání `Dispose(false)` a umístěte veškerou logiku vyčištění prostředků uvnitř `Dispose(bool disposing)` metoda.</span><span class="sxs-lookup"><span data-stu-id="d55da-190">When implementing the finalizer, simply call `Dispose(false)` and place all resource cleanup logic inside the `Dispose(bool disposing)` method.</span></span>  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="d55da-191">**PROVEĎTE ✓** implementovat základní vzor Dispose u každé finalizable typu.</span><span class="sxs-lookup"><span data-stu-id="d55da-191">**✓ DO** implement the Basic Dispose Pattern on every finalizable type.</span></span>  
  
 <span data-ttu-id="d55da-192">To poskytuje prostředky ke explicitně vyčistit deterministický tyto stejné prostředky, pro které finalizační metodu zodpovídá uživatelům typu.</span><span class="sxs-lookup"><span data-stu-id="d55da-192">This gives users of the type a means to explicitly perform deterministic cleanup of those same resources for which the finalizer is responsible.</span></span>  
  
 <span data-ttu-id="d55da-193">**X nesmí** přístup finalizable objekty v kódové cestě finalizační metodu, protože významné riziko, že se bude mít již byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="d55da-193">**X DO NOT** access any finalizable objects in the finalizer code path, because there is significant risk that they will have already been finalized.</span></span>  
  
 <span data-ttu-id="d55da-194">Například finalizable objekt, A který obsahuje odkaz na jiný objekt finalizable B v nelze použít spolehlivě B na finalizační metodu, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="d55da-194">For example, a finalizable object A that has a reference to another finalizable object B cannot reliably use B in A’s finalizer, or vice versa.</span></span> <span data-ttu-id="d55da-195">Finalizační metody se nazývají v náhodném pořadí (souborem slabé řazení záruku kritické finalizace).</span><span class="sxs-lookup"><span data-stu-id="d55da-195">Finalizers are called in a random order (short of a weak ordering guarantee for critical finalization).</span></span>  
  
 <span data-ttu-id="d55da-196">Mějte také na objekty uložené v statické proměnné se získat shromažďovat v určitých bodech během uvolnění domény aplikace nebo při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="d55da-196">Also, be aware that objects stored in static variables will get collected at certain points during an application domain unload or while exiting the process.</span></span> <span data-ttu-id="d55da-197">Přístup k statické proměnné, která odkazuje na objekt finalizable (nebo volání statickou metodu, která může používat hodnotami uloženými v statické proměnné) nemusí být bezpečné Pokud <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> vrací hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="d55da-197">Accessing a static variable that refers to a finalizable object (or calling a static method that might use values stored in static variables) might not be safe if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> returns true.</span></span>  
  
 <span data-ttu-id="d55da-198">**PROVÉST ✓** zkontrolujte vaše `Finalize` metoda chráněný.</span><span class="sxs-lookup"><span data-stu-id="d55da-198">**✓ DO** make your `Finalize` method protected.</span></span>  
  
 <span data-ttu-id="d55da-199">C#, C++ a VB.NET vývojáři nemusíte starat o to, protože kompilátory vám pomoct vynutit tyto obecné zásady.</span><span class="sxs-lookup"><span data-stu-id="d55da-199">C#, C++, and VB.NET developers do not need to worry about this, because the compilers help to enforce this guideline.</span></span>  
  
 <span data-ttu-id="d55da-200">**X nesmí** řídicí umožňují výjimky z finalizační metodu logiku, s výjimkou systému kritické chyby.</span><span class="sxs-lookup"><span data-stu-id="d55da-200">**X DO NOT** let exceptions escape from the finalizer logic, except for system-critical failures.</span></span>  
  
 <span data-ttu-id="d55da-201">Pokud z finalizační metody je vyvolána výjimka, modul CLR se zastaví celý proces (od verze rozhraní .NET Framework verze 2.0), dalších finalizační metody brání provádění a prostředky uvolnění řízené způsobem.</span><span class="sxs-lookup"><span data-stu-id="d55da-201">If an exception is thrown from a finalizer, the CLR will shut down the entire process (as of .NET Framework version 2.0), preventing other finalizers from executing and resources from being released in a controlled manner.</span></span>  
  
 <span data-ttu-id="d55da-202">**✓ ZVAŽTE** vytváření a používání objekt kritické finalizable (typu s hierarchie typů, která obsahuje <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) pro situace, ve kterých finalizační metody absolutně musí být spuštěn i při krátkodobém uvolnění domény aplikace vynucené a přístup z více vláken zruší.</span><span class="sxs-lookup"><span data-stu-id="d55da-202">**✓ CONSIDER** creating and using a critical finalizable object (a type with a type hierarchy that contains <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) for situations in which a finalizer absolutely must execute even in the face of forced application domain unloads and thread aborts.</span></span>  
  
 <span data-ttu-id="d55da-203">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="d55da-203">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d55da-204">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d55da-204">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d55da-205">Viz také</span><span class="sxs-lookup"><span data-stu-id="d55da-205">See Also</span></span>  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d55da-206">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="d55da-206">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="d55da-207">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="d55da-207">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [<span data-ttu-id="d55da-208">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="d55da-208">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
