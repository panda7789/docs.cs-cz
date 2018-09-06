---
title: Vzor dispose
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
ms.openlocfilehash: ff52e17cfe4a4236e4d165c0961ca3a23fed9a72
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864641"
---
# <a name="dispose-pattern"></a><span data-ttu-id="45c20-102">Vzor dispose</span><span class="sxs-lookup"><span data-stu-id="45c20-102">Dispose Pattern</span></span>
<span data-ttu-id="45c20-103">Všechny programy získat jeden nebo více systémových prostředků, jako je například paměť, popisovače systému nebo připojení k databázi, v průběhu jejich provádění.</span><span class="sxs-lookup"><span data-stu-id="45c20-103">All programs acquire one or more system resources, such as memory, system handles, or database connections, during the course of their execution.</span></span> <span data-ttu-id="45c20-104">Vývojáři musí být opatrní při používání těchto systémových prostředků, protože musí být uvolněny po svém získat a používat.</span><span class="sxs-lookup"><span data-stu-id="45c20-104">Developers have to be careful when using such system resources, because they must be released after they have been acquired and used.</span></span>  
  
 <span data-ttu-id="45c20-105">CLR poskytuje podporu pro automatická správa paměti.</span><span class="sxs-lookup"><span data-stu-id="45c20-105">The CLR provides support for automatic memory management.</span></span> <span data-ttu-id="45c20-106">Spravované paměti (paměť přidělena pomocí operátoru jazyka C# `new`) nemusí být explicitně uvolněn.</span><span class="sxs-lookup"><span data-stu-id="45c20-106">Managed memory (memory allocated using the C# operator `new`) does not need to be explicitly released.</span></span> <span data-ttu-id="45c20-107">Uvolní se automaticky podle systému uvolňování paměti (GC).</span><span class="sxs-lookup"><span data-stu-id="45c20-107">It is released automatically by the garbage collector (GC).</span></span> <span data-ttu-id="45c20-108">To se vaši vývojáři z únavné a složité úlohy uvolňování paměti a jestli se jeden z hlavních důvodů pro dosažení nebývalé produktivity poskytované rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45c20-108">This frees developers from the tedious and difficult task of releasing memory and has been one of the main reasons for the unprecedented productivity afforded by the .NET Framework.</span></span>  
  
 <span data-ttu-id="45c20-109">Bohužel spravované paměti je právě jeden z mnoha typů systémových prostředků.</span><span class="sxs-lookup"><span data-stu-id="45c20-109">Unfortunately, managed memory is just one of many types of system resources.</span></span> <span data-ttu-id="45c20-110">Prostředky než spravované paměti stále nutné explicitně uvolnit a jsou označovány jako nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="45c20-110">Resources other than managed memory still need to be released explicitly and are referred to as unmanaged resources.</span></span> <span data-ttu-id="45c20-111">Uvolňování paměti konkrétně je navržená ke správě těchto nespravované prostředky, což znamená, že odpovědnost za správu nespravované prostředky spočívá v rukou vývojáře.</span><span class="sxs-lookup"><span data-stu-id="45c20-111">The GC was specifically not designed to manage such unmanaged resources, which means that the responsibility for managing unmanaged resources lies in the hands of the developers.</span></span>  
  
 <span data-ttu-id="45c20-112">CLR poskytuje pomoc při uvolnění nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="45c20-112">The CLR provides some help in releasing unmanaged resources.</span></span> <span data-ttu-id="45c20-113"><xref:System.Object?displayProperty=nameWithType> deklaruje virtuální metoda <xref:System.Object.Finalize%2A> (také nazývané finalizační metody), který je volán uvolňování paměti, než paměti objektu je uvolněn systémem uvolňování paměti a může být potlačena za účelem uvolnění nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="45c20-113"><xref:System.Object?displayProperty=nameWithType> declares a virtual method <xref:System.Object.Finalize%2A> (also called the finalizer) that is called by the GC before the object’s memory is reclaimed by the GC and can be overridden to release unmanaged resources.</span></span> <span data-ttu-id="45c20-114">Typy, které přepsat finalizační metody jsou označovány jako finalizovatelný typy.</span><span class="sxs-lookup"><span data-stu-id="45c20-114">Types that override the finalizer are referred to as finalizable types.</span></span>  
  
 <span data-ttu-id="45c20-115">I když v některých scénářích vyčištění platí finalizační metody, mají dvě významné nevýhody:</span><span class="sxs-lookup"><span data-stu-id="45c20-115">Although finalizers are effective in some cleanup scenarios, they have two significant drawbacks:</span></span>  
  
-   <span data-ttu-id="45c20-116">Finalizační metoda se volá, když uvolňování paměti zjistí, že objekt je vhodné pro kolekci.</span><span class="sxs-lookup"><span data-stu-id="45c20-116">The finalizer is called when the GC detects that an object is eligible for collection.</span></span> <span data-ttu-id="45c20-117">K tomu dochází v některých neurčeném časový úsek, po prostředku není už potřeba.</span><span class="sxs-lookup"><span data-stu-id="45c20-117">This happens at some undetermined period of time after the resource is not needed anymore.</span></span> <span data-ttu-id="45c20-118">Zpoždění mezi při vývojář může nebo chcete verzi prostředku a čas, když prostředek skutečně vydal finalizační metoda může nepřijatelné v aplikacích, které získají mnoho vzácné prostředky (prostředky, které může dojít k vyčerpání snadno) nebo v případy, ve kterých jsou prostředky nákladné zachovat používá (například vyrovnávací paměti velkých nespravované paměti).</span><span class="sxs-lookup"><span data-stu-id="45c20-118">The delay between when the developer could or would like to release the resource and the time when the resource is actually released by the finalizer might be unacceptable in programs that acquire many scarce resources (resources that can be easily exhausted) or in cases in which resources are costly to keep in use (e.g., large unmanaged memory buffers).</span></span>  
  
-   <span data-ttu-id="45c20-119">Když modul CLR je potřeba volat finalizační metodu, se musí odložit kolekce paměti objektu dokud zaokrouhlí na další kolekce paměti (finalizační metody spuštění mezi kolekcí).</span><span class="sxs-lookup"><span data-stu-id="45c20-119">When the CLR needs to call a finalizer, it must postpone collection of the object’s memory until the next round of garbage collection (the finalizers run between collections).</span></span> <span data-ttu-id="45c20-120">To znamená, že pro delší časové období nebude všeobecně dostupné paměti objektu (a všechny objekty, které odkazuje na).</span><span class="sxs-lookup"><span data-stu-id="45c20-120">This means that the object’s memory (and all objects it refers to) will not be released for a longer period of time.</span></span>  
  
 <span data-ttu-id="45c20-121">Proto spoléhání se výhradně na finalizační metody nemusí být vhodný v případech, pokud je důležité co nejrychleji uvolnit nespravované prostředky při zpracování komplexnějších vzácné prostředky, nebo vysoce výkonné scénářů, ve kterých přidání režie uvolňování paměti Finalizace nepřijatelné.</span><span class="sxs-lookup"><span data-stu-id="45c20-121">Therefore, relying exclusively on finalizers might not be appropriate in many scenarios when it is important to reclaim unmanaged resources as quickly as possible, when dealing with scarce resources, or in highly performant scenarios in which the added GC overhead of finalization is unacceptable.</span></span>  
  
 <span data-ttu-id="45c20-122">Poskytuje rozhraní <xref:System.IDisposable?displayProperty=nameWithType> rozhraní, které by měla být implementována vybranými vývojář ruční k uvolnění nespravovaných prostředků, jakmile se v případě potřeby zapíná.</span><span class="sxs-lookup"><span data-stu-id="45c20-122">The Framework provides the <xref:System.IDisposable?displayProperty=nameWithType> interface that should be implemented to provide the developer a manual way to release unmanaged resources as soon as they are not needed.</span></span> <span data-ttu-id="45c20-123">Poskytuje také <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> metodu, která můžete říct, že uvolňování paměti objektu byl ručně odstraněn z a nemusí být finalizován už nepotřebujeme, v takovém případě paměti objektu se nedá uvolnit dříve.</span><span class="sxs-lookup"><span data-stu-id="45c20-123">It also provides the <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> method that can tell the GC that an object was manually disposed of and does not need to be finalized anymore, in which case the object’s memory can be reclaimed earlier.</span></span> <span data-ttu-id="45c20-124">Typy, které implementují `IDisposable` rozhraní se označují jako uvolnitelné typy.</span><span class="sxs-lookup"><span data-stu-id="45c20-124">Types that implement the `IDisposable` interface are referred to as disposable types.</span></span>  
  
 <span data-ttu-id="45c20-125">Vzor Dispose má standardizovat používání a implementace finalizační metody a `IDisposable` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="45c20-125">The Dispose Pattern is intended to standardize the usage and implementation of finalizers and the `IDisposable` interface.</span></span>  
  
 <span data-ttu-id="45c20-126">Hlavní motivace pro vzor je ke snížení složitosti implementace <xref:System.Object.Finalize%2A> a <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="45c20-126">The main motivation for the pattern is to reduce the complexity of the implementation of the <xref:System.Object.Finalize%2A> and the <xref:System.IDisposable.Dispose%2A> methods.</span></span> <span data-ttu-id="45c20-127">Složitost vyplývá ze skutečnosti, že metody sdílet některé, ale ne všechny cesty kódu (rozdíly jsou popsány dále v kapitole).</span><span class="sxs-lookup"><span data-stu-id="45c20-127">The complexity stems from the fact that the methods share some but not all code paths (the differences are described later in the chapter).</span></span> <span data-ttu-id="45c20-128">Kromě toho jsou historických důvodů, proč některé prvky vzor souvisejícími s vývojem jazyková podpora v nástroji Správa deterministické prostředků.</span><span class="sxs-lookup"><span data-stu-id="45c20-128">In addition, there are historical reasons for some elements of the pattern related to the evolution of language support for deterministic resource management.</span></span>  
  
 <span data-ttu-id="45c20-129">**✓ DO** implementace základní Dispose vzoru na typy obsahující instance uvolnitelné typy.</span><span class="sxs-lookup"><span data-stu-id="45c20-129">**✓ DO** implement the Basic Dispose Pattern on types containing instances of disposable types.</span></span> <span data-ttu-id="45c20-130">Zobrazit [základní vzor Dispose](#basic_pattern) podrobné informace o základní vzor.</span><span class="sxs-lookup"><span data-stu-id="45c20-130">See the [Basic Dispose Pattern](#basic_pattern) section for details on the basic pattern.</span></span>  
  
 <span data-ttu-id="45c20-131">Pokud typ je zodpovědný za dobu života jiné uvolnitelné objekty, vývojáři potřebují způsob, jak vyřadit, je moc.</span><span class="sxs-lookup"><span data-stu-id="45c20-131">If a type is responsible for the lifetime of other disposable objects, developers need a way to dispose of them, too.</span></span> <span data-ttu-id="45c20-132">Pomocí kontejneru `Dispose` metoda nabízí pohodlný způsob, aby to možné.</span><span class="sxs-lookup"><span data-stu-id="45c20-132">Using the container’s `Dispose` method is a convenient way to make this possible.</span></span>  
  
 <span data-ttu-id="45c20-133">**✓ DO** implementovat základní vzor Dispose a zadejte finalizační metody pro typy prostředků podniku, které je potřeba explicitně uvolnit a které nemají finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="45c20-133">**✓ DO** implement the Basic Dispose Pattern and provide a finalizer on types holding resources that need to be freed explicitly and that do not have finalizers.</span></span>  
  
 <span data-ttu-id="45c20-134">Například by měla být implementována vzoru na typy ukládání nespravované paměti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="45c20-134">For example, the pattern should be implemented on types storing unmanaged memory buffers.</span></span> <span data-ttu-id="45c20-135">[Finalizovatelný typy](#finalizable_types) část popisuje pokyny týkající se implementace finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="45c20-135">The [Finalizable Types](#finalizable_types) section discusses guidelines related to implementing finalizers.</span></span>  
  
 <span data-ttu-id="45c20-136">**✓ CONSIDER** implementace vzoru Dispose základní na třídách sami nemáte uložení nespravovaných prostředků nebo na jedno použití objekty jsou ale mohou mít podtypů, které provádějí.</span><span class="sxs-lookup"><span data-stu-id="45c20-136">**✓ CONSIDER** implementing the Basic Dispose Pattern on classes that themselves don’t hold unmanaged resources or disposable objects but are likely to have subtypes that do.</span></span>  
  
 <span data-ttu-id="45c20-137">Je to skvělý například <xref:System.IO.Stream?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="45c20-137">A great example of this is the <xref:System.IO.Stream?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="45c20-138">I když je abstraktní základní třídu, která nebude obsahovat žádné prostředky, proveďte většina jejích podtříd a z toho důvodu implementuje tento model.</span><span class="sxs-lookup"><span data-stu-id="45c20-138">Although it is an abstract base class that doesn’t hold any resources, most of its subclasses do and because of this, it implements this pattern.</span></span>  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a><span data-ttu-id="45c20-139">Vzor Dispose pro základní</span><span class="sxs-lookup"><span data-stu-id="45c20-139">Basic Dispose Pattern</span></span>  
 <span data-ttu-id="45c20-140">Zahrnuje základní implementaci modelu implementace `System.IDisposable` rozhraní a deklarační popisovač `Dispose(bool)` metody, která implementuje veškerou logiku vyčištění prostředků sdílen `Dispose` metoda a volitelné finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="45c20-140">The basic implementation of the pattern involves implementing the `System.IDisposable` interface and declaring the `Dispose(bool)` method that implements all resource cleanup logic to be shared between the `Dispose` method and the optional finalizer.</span></span>  
  
 <span data-ttu-id="45c20-141">Následující příklad ukazuje, jednoduché provedení základní vzor:</span><span class="sxs-lookup"><span data-stu-id="45c20-141">The following example shows a simple implementation of the basic pattern:</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder() {  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposing) {  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="45c20-142">Parametr logické hodnoty `disposing` označuje, zda metoda byla vyvolána z `IDisposable.Dispose` implementace nebo z finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="45c20-142">The Boolean parameter `disposing` indicates whether the method was invoked from the `IDisposable.Dispose` implementation or from the finalizer.</span></span> <span data-ttu-id="45c20-143">`Dispose(bool)` Implementace zkontrolujte parametr před přístupem k další odkaz na objekty (například pole prostředků v předchozím příkladu).</span><span class="sxs-lookup"><span data-stu-id="45c20-143">The `Dispose(bool)` implementation should check the parameter before accessing other reference objects (e.g., the resource field in the preceding sample).</span></span> <span data-ttu-id="45c20-144">Tyto objekty by měl mít přístup jenom Pokud metoda je volána z `IDisposable.Dispose` implementace (když `disposing` rovná parametru na hodnotu true).</span><span class="sxs-lookup"><span data-stu-id="45c20-144">Such objects should only be accessed when the method is called from the `IDisposable.Dispose` implementation (when the `disposing` parameter is equal to true).</span></span> <span data-ttu-id="45c20-145">Pokud je metoda vyvolána z finalizační metody (`disposing` je false), by neměl být přístupný jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="45c20-145">If the method is invoked from the finalizer (`disposing` is false), other objects should not be accessed.</span></span> <span data-ttu-id="45c20-146">Důvodem je, že objekty jsou dokončeny v pořadí nepředvídatelné a proto jsou, nebo žádnou z jeho závislostí, může již mít finalizován.</span><span class="sxs-lookup"><span data-stu-id="45c20-146">The reason is that objects are finalized in an unpredictable order and so they, or any of their dependencies, might already have been finalized.</span></span>  
  
 <span data-ttu-id="45c20-147">Tato část platí také, pro třídy na bázi již neimplementuje vzor Dispose.</span><span class="sxs-lookup"><span data-stu-id="45c20-147">Also, this section applies to classes with a base that does not already implement the Dispose Pattern.</span></span> <span data-ttu-id="45c20-148">Pokud se dědí z třídy, která již implementuje vzor, jednoduše přepsat `Dispose(bool)` metodu k dispozici logiky vyčištění dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="45c20-148">If you are inheriting from a class that already implements the pattern, simply override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="45c20-149">**✓ DO** deklarovat `protected virtual void Dispose(bool disposing)` metoda a centralizovat veškerou logiku s uvolňováním nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="45c20-149">**✓ DO** declare a `protected virtual void Dispose(bool disposing)` method to centralize all logic related to releasing unmanaged resources.</span></span>  
  
 <span data-ttu-id="45c20-150">V této metodě se budou objevovat všechny vyčištění prostředků.</span><span class="sxs-lookup"><span data-stu-id="45c20-150">All resource cleanup should occur in this method.</span></span> <span data-ttu-id="45c20-151">Metoda je volána z obou finalizační metody a `IDisposable.Dispose` metoda.</span><span class="sxs-lookup"><span data-stu-id="45c20-151">The method is called from both the finalizer and the `IDisposable.Dispose` method.</span></span> <span data-ttu-id="45c20-152">Parametr bude hodnotu false, pokud volaná z uvnitř finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="45c20-152">The parameter will be false if being invoked from inside a finalizer.</span></span> <span data-ttu-id="45c20-153">By měla sloužit k zajištění, že veškerý kód během finalizace není přístup k jiné dokončitelné objekty.</span><span class="sxs-lookup"><span data-stu-id="45c20-153">It should be used to ensure any code running during finalization is not accessing other finalizable objects.</span></span> <span data-ttu-id="45c20-154">Podrobnosti implementace finalizační metody jsou popsané v další části.</span><span class="sxs-lookup"><span data-stu-id="45c20-154">Details of implementing finalizers are described in the next section.</span></span>  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 <span data-ttu-id="45c20-155">**✓ DO** implementovat `IDisposable` rozhraní jednoduše voláním `Dispose(true)` následuje `GC.SuppressFinalize(this)`.</span><span class="sxs-lookup"><span data-stu-id="45c20-155">**✓ DO** implement the `IDisposable` interface by simply calling `Dispose(true)` followed by `GC.SuppressFinalize(this)`.</span></span>  
  
 <span data-ttu-id="45c20-156">Volání `SuppressFinalize` dojde pouze pokud `Dispose(true)` úspěšně spustí.</span><span class="sxs-lookup"><span data-stu-id="45c20-156">The call to `SuppressFinalize` should only occur if `Dispose(true)` executes successfully.</span></span>  
  
```csharp
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 <span data-ttu-id="45c20-157">**X DO NOT** zkontrolujte bezparametrový `Dispose` metoda virtuální.</span><span class="sxs-lookup"><span data-stu-id="45c20-157">**X DO NOT** make the parameterless `Dispose` method virtual.</span></span>  
  
 <span data-ttu-id="45c20-158">`Dispose(bool)` Metoda je ta, kterou by měla být přepsána podtřídami.</span><span class="sxs-lookup"><span data-stu-id="45c20-158">The `Dispose(bool)` method is the one that should be overridden by subclasses.</span></span>  
  
```csharp
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
```  
  
 <span data-ttu-id="45c20-159">**X DO NOT** deklarovat žádné přetížení `Dispose` jinak než `Dispose()` a `Dispose(bool)`.</span><span class="sxs-lookup"><span data-stu-id="45c20-159">**X DO NOT** declare any overloads of the `Dispose` method other than `Dispose()` and `Dispose(bool)`.</span></span>  
  
 <span data-ttu-id="45c20-160">`Dispose` považovat za vyhrazené slovo kodifikovat tento model a prevence nejasnostem mezi implementátory, uživatelů a kompilátory.</span><span class="sxs-lookup"><span data-stu-id="45c20-160">`Dispose` should be considered a reserved word to help codify this pattern and prevent confusion among implementers, users, and compilers.</span></span> <span data-ttu-id="45c20-161">Některé jazyky mohou automaticky tento model implementovat na určitých typech.</span><span class="sxs-lookup"><span data-stu-id="45c20-161">Some languages might choose to automatically implement this pattern on certain types.</span></span>  
  
 <span data-ttu-id="45c20-162">**✓ DO** povolit `Dispose(bool)` metoda, která se má volat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="45c20-162">**✓ DO** allow the `Dispose(bool)` method to be called more than once.</span></span> <span data-ttu-id="45c20-163">Neprovádět žádnou akci po prvním volání zvolit metodu.</span><span class="sxs-lookup"><span data-stu-id="45c20-163">The method might choose to do nothing after the first call.</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="45c20-164">**X AVOID** došlo k výjimce z uvnitř `Dispose(bool)` nejsou pod kritických situací, kdy je proces obsahující poškozená (nevracení, nekonzistentní sdíleného stavu atd.).</span><span class="sxs-lookup"><span data-stu-id="45c20-164">**X AVOID** throwing an exception from within `Dispose(bool)` except under critical situations where the containing process has been corrupted (leaks, inconsistent shared state, etc.).</span></span>  
  
 <span data-ttu-id="45c20-165">Uživatelé očekávají, že volání `Dispose` nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="45c20-165">Users expect that a call to `Dispose` will not raise an exception.</span></span>  
  
 <span data-ttu-id="45c20-166">Pokud `Dispose` může vyvolat výjimku, další logiky vyčištění závěrečný blok nebude spuštěno.</span><span class="sxs-lookup"><span data-stu-id="45c20-166">If `Dispose` could raise an exception, further finally-block cleanup logic will not execute.</span></span> <span data-ttu-id="45c20-167">Chcete-li tento problém obejít, uživatel by potřeba všechna volání `Dispose` (v rámci bloku finally!) v bloku try, což vede k velmi složité vyčištění obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="45c20-167">To work around this, the user would need to wrap every call to `Dispose` (within the finally block!) in a try block, which leads to very complex cleanup handlers.</span></span> <span data-ttu-id="45c20-168">Pokud provádění `Dispose(bool disposing)` metoda, nikdy throw výjimku, pokud disposing má hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="45c20-168">If executing a `Dispose(bool disposing)` method, never throw an exception if disposing is false.</span></span> <span data-ttu-id="45c20-169">Tím se ukončit proces při provádění v rámci finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="45c20-169">Doing so will terminate the process if executing inside a finalizer context.</span></span>  
  
 <span data-ttu-id="45c20-170">**✓ DO** throw <xref:System.ObjectDisposedException> z kteréhokoli člena, který nelze použít po objekt byl vyřazen.</span><span class="sxs-lookup"><span data-stu-id="45c20-170">**✓ DO** throw an <xref:System.ObjectDisposedException> from any member that cannot be used after the object has been disposed of.</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething() {  
        if (disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
        ...  
    }  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="45c20-171">**✓ CONSIDER** poskytuje metoda `Close()`, kromě `Dispose()`, pokud je zavřete standardní terminologii v oblasti.</span><span class="sxs-lookup"><span data-stu-id="45c20-171">**✓ CONSIDER** providing method `Close()`, in addition to the `Dispose()`, if close is standard terminology in the area.</span></span>  
  
 <span data-ttu-id="45c20-172">Pokud tak učiníte, je důležité, abyste si udělali `Close` identické s implementací `Dispose` a zvažte implementaci `IDisposable.Dispose` metoda explicitně.</span><span class="sxs-lookup"><span data-stu-id="45c20-172">When doing so, it is important that you make the `Close` implementation identical to `Dispose` and consider implementing the `IDisposable.Dispose` method explicitly.</span></span>  
  
```csharp
public class Stream : IDisposable {  
    IDisposable.Dispose() {  
        Close();  
    }  
    public void Close() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a><span data-ttu-id="45c20-173">Finalizovatelný typy</span><span class="sxs-lookup"><span data-stu-id="45c20-173">Finalizable Types</span></span>  
 <span data-ttu-id="45c20-174">Finalizovatelný typy jsou typy, které rozšiřují základní vzor Dispose přepisuje finalizační metody a poskytnutím finalizace kódové cestě v `Dispose(bool)` metody.</span><span class="sxs-lookup"><span data-stu-id="45c20-174">Finalizable types are types that extend the Basic Dispose Pattern by overriding the finalizer and providing finalization code path in the `Dispose(bool)` method.</span></span>  
  
 <span data-ttu-id="45c20-175">Finalizační metody je známo, že těžké implementovat správně, především, protože je nelze předem určité domněnky (obvykle platný) o stavu systému při jejich provádění.</span><span class="sxs-lookup"><span data-stu-id="45c20-175">Finalizers are notoriously difficult to implement correctly, primarily because you cannot make certain (normally valid) assumptions about the state of the system during their execution.</span></span> <span data-ttu-id="45c20-176">Podle následujících pokynů byste vzít v úvahu opatrní.</span><span class="sxs-lookup"><span data-stu-id="45c20-176">The following guidelines should be taken into careful consideration.</span></span>  
  
 <span data-ttu-id="45c20-177">Všimněte si, že některé pokyny platí není jen pro `Finalize` metody, ale pro libovolný kód volá z finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="45c20-177">Note that some of the guidelines apply not just to the `Finalize` method, but to any code called from a finalizer.</span></span> <span data-ttu-id="45c20-178">V případě základní Dispose vzor dříve definované, to znamená, že logiky, která provede uvnitř `Dispose(bool disposing)` při `disposing` parametr má hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="45c20-178">In the case of the Basic Dispose Pattern previously defined, this means logic that executes inside `Dispose(bool disposing)` when the `disposing` parameter is false.</span></span>  
  
 <span data-ttu-id="45c20-179">Pokud základní třídy už je finalizovatelný a implementuje základní vzor Dispose, by neměla přepsat `Finalize` znovu.</span><span class="sxs-lookup"><span data-stu-id="45c20-179">If the base class already is finalizable and implements the Basic Dispose Pattern, you should not override `Finalize` again.</span></span> <span data-ttu-id="45c20-180">Měli byste místo toho jenom přepsat `Dispose(bool)` metodu k dispozici logiky vyčištění dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="45c20-180">You should instead just override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="45c20-181">Následující kód ukazuje příklad finalizovatelný typu:</span><span class="sxs-lookup"><span data-stu-id="45c20-181">The following code shows an example of a finalizable type:</span></span>  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder() {  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing) {  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing) { // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    public void Dispose() {
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 <span data-ttu-id="45c20-182">**X AVOID** provedení finalizable typy.</span><span class="sxs-lookup"><span data-stu-id="45c20-182">**X AVOID** making types finalizable.</span></span>  
  
 <span data-ttu-id="45c20-183">Pečlivě zvažte, případ, ve kterém si myslíte, že je potřeba finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="45c20-183">Carefully consider any case in which you think a finalizer is needed.</span></span> <span data-ttu-id="45c20-184">Se o skutečné náklady spojené s instancí s finalizační metody, z hlediska výkonu a kód složitost.</span><span class="sxs-lookup"><span data-stu-id="45c20-184">There is a real cost associated with instances with finalizers, from both a performance and code complexity standpoint.</span></span> <span data-ttu-id="45c20-185">Dáváte přednost, například pomocí obálky prostředků <xref:System.Runtime.InteropServices.SafeHandle> pro zapouzdření nespravovaných prostředků, kde je to možné, v takovém případě finalizační metodu stane nepotřebné vzhledem k tomu, že obálky je zodpovědná za své vlastní vyčištění prostředků.</span><span class="sxs-lookup"><span data-stu-id="45c20-185">Prefer using resource wrappers such as <xref:System.Runtime.InteropServices.SafeHandle> to encapsulate unmanaged resources where possible, in which case a finalizer becomes unnecessary because the wrapper is responsible for its own resource cleanup.</span></span>  
  
 <span data-ttu-id="45c20-186">**X DO NOT** zkontrolujte finalizable typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="45c20-186">**X DO NOT** make value types finalizable.</span></span>  
  
 <span data-ttu-id="45c20-187">Pouze typy odkazů ve skutečnosti získat dokončí modulem CLR, a proto se bude ignorovat jakékoli pokusy o finalizační metody umístit na typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="45c20-187">Only reference types actually get finalized by the CLR, and thus any attempt to place a finalizer on a value type will be ignored.</span></span> <span data-ttu-id="45c20-188">C# a C++ kompilátory vynucují toto pravidlo.</span><span class="sxs-lookup"><span data-stu-id="45c20-188">The C# and C++ compilers enforce this rule.</span></span>  
  
 <span data-ttu-id="45c20-189">**✓ DO** zkontrolujte finalizable typu, pokud typ je zodpovědná za uvolnění nespravovaných zdrojů, který nemá vlastní finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="45c20-189">**✓ DO** make a type finalizable if the type is responsible for releasing an unmanaged resource that does not have its own finalizer.</span></span>  
  
 <span data-ttu-id="45c20-190">Při implementaci finalizační metodu, jednoduše zavolejte `Dispose(false)` a umístěte veškerou logiku vyčištění prostředků uvnitř `Dispose(bool disposing)` metody.</span><span class="sxs-lookup"><span data-stu-id="45c20-190">When implementing the finalizer, simply call `Dispose(false)` and place all resource cleanup logic inside the `Dispose(bool disposing)` method.</span></span>  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing) {
        ...  
    }  
}  
```  
  
 <span data-ttu-id="45c20-191">**✓ DO** implementovat základní vzor Dispose u každé finalizable typu.</span><span class="sxs-lookup"><span data-stu-id="45c20-191">**✓ DO** implement the Basic Dispose Pattern on every finalizable type.</span></span>  
  
 <span data-ttu-id="45c20-192">Díky tomu uživatelé typu prostředek pro explicitně deterministické vyčištění tyto stejné prostředky, pro které je zodpovědný finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="45c20-192">This gives users of the type a means to explicitly perform deterministic cleanup of those same resources for which the finalizer is responsible.</span></span>  
  
 <span data-ttu-id="45c20-193">**X DO NOT** přístup finalizable objekty v kódové cestě finalizační metodu, protože významné riziko, že se bude mít již byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="45c20-193">**X DO NOT** access any finalizable objects in the finalizer code path, because there is significant risk that they will have already been finalized.</span></span>  
  
 <span data-ttu-id="45c20-194">Například finalizovatelný objekt A, který odkazuje na jiný finalizovatelný objekt B nelze použít spolehlivě B v příslušné finalizační metodu, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="45c20-194">For example, a finalizable object A that has a reference to another finalizable object B cannot reliably use B in A’s finalizer, or vice versa.</span></span> <span data-ttu-id="45c20-195">Finalizační metody jsou volány v náhodném pořadí (nemá slabé řazení záruku kritická dokončení).</span><span class="sxs-lookup"><span data-stu-id="45c20-195">Finalizers are called in a random order (short of a weak ordering guarantee for critical finalization).</span></span>  
  
 <span data-ttu-id="45c20-196">Také mějte na paměti, že objekty uložené ve statické proměnné získat neshromáždí v určitých bodech během uvolnění domény aplikace nebo při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="45c20-196">Also, be aware that objects stored in static variables will get collected at certain points during an application domain unload or while exiting the process.</span></span> <span data-ttu-id="45c20-197">Přístup k statická proměnná, která odkazuje na finalizovatelný objekt (nebo zavolání statické metody, která může používat hodnotám uloženým ve statické proměnné) nemusí být bezpečné if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> vrací hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="45c20-197">Accessing a static variable that refers to a finalizable object (or calling a static method that might use values stored in static variables) might not be safe if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> returns true.</span></span>  
  
 <span data-ttu-id="45c20-198">**✓ DO** zkontrolujte vaše `Finalize` metoda chráněný.</span><span class="sxs-lookup"><span data-stu-id="45c20-198">**✓ DO** make your `Finalize` method protected.</span></span>  
  
 <span data-ttu-id="45c20-199">Vývojáře v C#, C++ a VB.NET nemusíte starat o to, protože umožňují kompilátory vynucují toto pravidlo.</span><span class="sxs-lookup"><span data-stu-id="45c20-199">C#, C++, and VB.NET developers do not need to worry about this, because the compilers help to enforce this guideline.</span></span>  
  
 <span data-ttu-id="45c20-200">**X DO NOT** řídicí umožňují výjimky z finalizační metodu logiku, s výjimkou systému kritické chyby.</span><span class="sxs-lookup"><span data-stu-id="45c20-200">**X DO NOT** let exceptions escape from the finalizer logic, except for system-critical failures.</span></span>  
  
 <span data-ttu-id="45c20-201">Pokud z finalizační metody, je vyvolána výjimka, modul CLR se vypne celý proces (od verze rozhraní .NET Framework verze 2.0), bránit v provádění a prostředkům se vydávají ve kontrolovaně jiných finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="45c20-201">If an exception is thrown from a finalizer, the CLR will shut down the entire process (as of .NET Framework version 2.0), preventing other finalizers from executing and resources from being released in a controlled manner.</span></span>  
  
 <span data-ttu-id="45c20-202">**✓ CONSIDER** vytváření a používání objekt kritické finalizable (typu s hierarchie typů, která obsahuje <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) pro situace, ve kterých finalizační metody absolutně musí být spuštěn i při krátkodobém uvolnění domény aplikace vynucené a přístup z více vláken zruší.</span><span class="sxs-lookup"><span data-stu-id="45c20-202">**✓ CONSIDER** creating and using a critical finalizable object (a type with a type hierarchy that contains <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) for situations in which a finalizer absolutely must execute even in the face of forced application domain unloads and thread aborts.</span></span>  
  
 <span data-ttu-id="45c20-203">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="45c20-203">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="45c20-204">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="45c20-204">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c20-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45c20-205">See also</span></span>

- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="45c20-206">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="45c20-206">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="45c20-207">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="45c20-207">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
- [<span data-ttu-id="45c20-208">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="45c20-208">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
