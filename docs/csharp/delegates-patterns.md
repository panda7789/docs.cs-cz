---
title: Obecné vzory pro delegáti
description: Další informace o obecné vzory pro použití delegátů ve vašem kódu předejdete silné párování mezi vaší součásti.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 20d55a1aba345b962c506bbc3f82248a817923ea
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827017"
---
# <a name="common-patterns-for-delegates"></a><span data-ttu-id="0bf90-103">Obecné vzory pro delegáti</span><span class="sxs-lookup"><span data-stu-id="0bf90-103">Common Patterns for Delegates</span></span>

[<span data-ttu-id="0bf90-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="0bf90-104">Previous</span></span>](delegates-strongly-typed.md)

<span data-ttu-id="0bf90-105">Delegáti poskytují mechanismus, který umožňuje návrhy softwaru zahrnující minimální párování mezi součástmi.</span><span class="sxs-lookup"><span data-stu-id="0bf90-105">Delegates provide a mechanism that enables software designs involving minimal coupling between components.</span></span>

<span data-ttu-id="0bf90-106">Příkladem vynikající pro tento typ návrhu je LINQ.</span><span class="sxs-lookup"><span data-stu-id="0bf90-106">One excellent example for this kind of design is LINQ.</span></span> <span data-ttu-id="0bf90-107">Vzor výrazu dotazu LINQ spoléhá na delegáty pro všechny její funkce.</span><span class="sxs-lookup"><span data-stu-id="0bf90-107">The LINQ Query Expression Pattern relies on delegates for all of its features.</span></span> <span data-ttu-id="0bf90-108">Vezměte v úvahu tomto jednoduchém příkladu:</span><span class="sxs-lookup"><span data-stu-id="0bf90-108">Consider this simple example:</span></span>

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

<span data-ttu-id="0bf90-109">Tím se odfiltrují pořadí čísel a pouze ty menší než hodnota 10.</span><span class="sxs-lookup"><span data-stu-id="0bf90-109">This filters the sequence of numbers to only those less than the value 10.</span></span>
<span data-ttu-id="0bf90-110">`Where` Metoda používá delegáta, který určuje, které prvky pořadí předat filtru.</span><span class="sxs-lookup"><span data-stu-id="0bf90-110">The `Where` method uses a delegate that determines which elements of a sequence pass the filter.</span></span> <span data-ttu-id="0bf90-111">Když vytvoříte dotaz LINQ, je třeba zadat implementace delegáta pro tento konkrétní účel.</span><span class="sxs-lookup"><span data-stu-id="0bf90-111">When you create a LINQ query, you supply the implementation of the delegate for this specific purpose.</span></span>

<span data-ttu-id="0bf90-112">Prototyp Where je metoda:</span><span class="sxs-lookup"><span data-stu-id="0bf90-112">The prototype for the Where method is:</span></span>

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

<span data-ttu-id="0bf90-113">V tomto příkladu se opakuje se všechny metody, které jsou součástí LINQ.</span><span class="sxs-lookup"><span data-stu-id="0bf90-113">This example is repeated with all the methods that are part of LINQ.</span></span> <span data-ttu-id="0bf90-114">Všechny spoléhají na delegáty pro kód, který spravuje specifického dotazu.</span><span class="sxs-lookup"><span data-stu-id="0bf90-114">They all rely on delegates for the code that manages the specific query.</span></span> <span data-ttu-id="0bf90-115">Tento vzor návrhu rozhraní API je velice mocný zjišťovat a pochopit.</span><span class="sxs-lookup"><span data-stu-id="0bf90-115">This API design pattern is a very powerful one to learn and understand.</span></span>

<span data-ttu-id="0bf90-116">Tento jednoduchý příklad ukazuje, jak delegáti vyžadují velmi malé párování mezi součástmi.</span><span class="sxs-lookup"><span data-stu-id="0bf90-116">This simple example illustrates how delegates require very little coupling between components.</span></span> <span data-ttu-id="0bf90-117">Nemusíte vytvořte třídu, která je odvozena z určité základní třídy.</span><span class="sxs-lookup"><span data-stu-id="0bf90-117">You don't need to create a class that derives from a particular base class.</span></span> <span data-ttu-id="0bf90-118">Nemusíte implementovat určité rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0bf90-118">You don't need to implement a specific interface.</span></span>
<span data-ttu-id="0bf90-119">Jediným požadavkem je poskytnout implementaci jednu metodu, je nezbytné, aby na prováděné úloze.</span><span class="sxs-lookup"><span data-stu-id="0bf90-119">The only requirement is to provide the implementation of one method that is fundamental to the task at hand.</span></span>

## <a name="building-your-own-components-with-delegates"></a><span data-ttu-id="0bf90-120">Vytváření vlastních součástí s delegáti</span><span class="sxs-lookup"><span data-stu-id="0bf90-120">Building Your Own Components with Delegates</span></span>

<span data-ttu-id="0bf90-121">Umožňuje vytvořit v tomto příkladu vytvořením součást pomocí návrhu, které jsou závislé na delegáti.</span><span class="sxs-lookup"><span data-stu-id="0bf90-121">Let's build on that example by creating a component using a design that relies on delegates.</span></span>

<span data-ttu-id="0bf90-122">Umožňuje definovat komponenty, která by mohly být použity zprávy protokolu ve velkých systému.</span><span class="sxs-lookup"><span data-stu-id="0bf90-122">Let's define a component that could be used for log messages in a large system.</span></span> <span data-ttu-id="0bf90-123">Součásti knihovny může v mnoha různých prostředích, na více různých platformách.</span><span class="sxs-lookup"><span data-stu-id="0bf90-123">The library components could be used in many different environments, on multiple different platforms.</span></span> <span data-ttu-id="0bf90-124">Existuje mnoho běžných funkcí v součásti, která spravuje protokoly.</span><span class="sxs-lookup"><span data-stu-id="0bf90-124">There are a lot of common features in the component that manages the logs.</span></span> <span data-ttu-id="0bf90-125">Může se stát, ji budou muset přijmout zprávy z libovolné součásti v systému.</span><span class="sxs-lookup"><span data-stu-id="0bf90-125">It will need to accept messages from any component in the system.</span></span> <span data-ttu-id="0bf90-126">Tyto zprávy budou mít různé priority, které můžou spravovat součást základních.</span><span class="sxs-lookup"><span data-stu-id="0bf90-126">Those messages will have different priorities, which the core component can manage.</span></span> <span data-ttu-id="0bf90-127">Zprávy musí mít časová razítka v jejich poslední archivovaný formuláře.</span><span class="sxs-lookup"><span data-stu-id="0bf90-127">The messages should have timestamps in their final archived form.</span></span> <span data-ttu-id="0bf90-128">Pro pokročilejší scénáře můžete vyfiltrovat zprávy zdrojovou součástí.</span><span class="sxs-lookup"><span data-stu-id="0bf90-128">For more advanced scenarios, you could filter messages by the source component.</span></span>

<span data-ttu-id="0bf90-129">Neexistuje jeden aspekt funkce, která se často změní: zápis zpráv.</span><span class="sxs-lookup"><span data-stu-id="0bf90-129">There is one aspect of the feature that will change often: where messages are written.</span></span> <span data-ttu-id="0bf90-130">V některých prostředích může být zapsána do konzoly chyby.</span><span class="sxs-lookup"><span data-stu-id="0bf90-130">In some environments, they may be written to the error console.</span></span> <span data-ttu-id="0bf90-131">V jiných případech soubor.</span><span class="sxs-lookup"><span data-stu-id="0bf90-131">In others, a file.</span></span> <span data-ttu-id="0bf90-132">Ostatní možnosti patří úložiště databáze, protokoly událostí operačního systému nebo jiného dokumentu úložiště.</span><span class="sxs-lookup"><span data-stu-id="0bf90-132">Other possibilities include database storage, OS event logs, or other document storage.</span></span>

<span data-ttu-id="0bf90-133">Existují také kombinací výstupu, které lze použít v různých scénářích.</span><span class="sxs-lookup"><span data-stu-id="0bf90-133">There are also combinations of output that might be used in different scenarios.</span></span> <span data-ttu-id="0bf90-134">Můžete pro zápis zpráv do konzoly a do souboru.</span><span class="sxs-lookup"><span data-stu-id="0bf90-134">You may want to write messages to the console and to a file.</span></span>

<span data-ttu-id="0bf90-135">Návrh podle delegáti bude poskytovat značnou flexibilitu a usnadňují podporu úložiště mechanismy, které lze přidat v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="0bf90-135">A design based on delegates will provide a great deal of flexibility, and make it easy to support storage mechanisms that may be added in the future.</span></span>

<span data-ttu-id="0bf90-136">V tomto návrhu může být primární protokolu součásti nevirtuálních, i zapečetěné třídy.</span><span class="sxs-lookup"><span data-stu-id="0bf90-136">Under this design, the primary log component can be a non-virtual, even sealed class.</span></span> <span data-ttu-id="0bf90-137">Můžete zařadit v žádné sadě delegátů k zápisu zprávy do jiného úložiště média.</span><span class="sxs-lookup"><span data-stu-id="0bf90-137">You can plug in any set of delegates to write the messages to different storage media.</span></span> <span data-ttu-id="0bf90-138">Integrované podporu vícesměrového vysílání delegáti usnadňuje podporu scénáře, kde musí být zprávy zapisovány do víc umístění (soubor a konzole).</span><span class="sxs-lookup"><span data-stu-id="0bf90-138">The built in support for multicast delegates makes it easy to support scenarios where messages must be written to multiple locations (a file, and a console).</span></span>

## <a name="a-first-implementation"></a><span data-ttu-id="0bf90-139">První implementace</span><span class="sxs-lookup"><span data-stu-id="0bf90-139">A First Implementation</span></span>

<span data-ttu-id="0bf90-140">Začněme malé: počáteční implementace přijmout nové zprávy a zapsat je pomocí všechny připojené delegáta.</span><span class="sxs-lookup"><span data-stu-id="0bf90-140">Let's start small: the initial implementation will accept new messages, and write them using any attached delegate.</span></span> <span data-ttu-id="0bf90-141">Můžete začít s jeden delegáta, který zapíše zpráv do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0bf90-141">You can start with one delegate that writes messages to the console.</span></span>

[!code-csharp[LoggerImplementation](../../samples/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

<span data-ttu-id="0bf90-142">Statická třída výše je nejjednodušší věcí, které může fungovat.</span><span class="sxs-lookup"><span data-stu-id="0bf90-142">The static class above is the simplest thing that can work.</span></span> <span data-ttu-id="0bf90-143">Je potřeba zapsat jediná implementace pro metody, která zapisuje zpráv do konzoly:</span><span class="sxs-lookup"><span data-stu-id="0bf90-143">We need to write the single implementation for the method that writes messages to the console:</span></span> 

[!code-csharp[LogToConsole](../../samples/csharp/delegates-and-events/Program.cs#LogToConsole "A Console logger.")]

<span data-ttu-id="0bf90-144">Nakonec můžete spojit delegát připojením k WriteMessage delegáta deklarovat v protokolovacího nástroje:</span><span class="sxs-lookup"><span data-stu-id="0bf90-144">Finally, you need to hook up the delegate by attaching it to the WriteMessage delegate declared in the logger:</span></span>

[!code-csharp[ConnectDelegate](../../samples/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a><span data-ttu-id="0bf90-145">Postupy</span><span class="sxs-lookup"><span data-stu-id="0bf90-145">Practices</span></span>

<span data-ttu-id="0bf90-146">Naše ukázka, pokud je docela jednoduchá, ale stále ukazuje některé důležité pokyny pro návrhy zahrnující delegáti.</span><span class="sxs-lookup"><span data-stu-id="0bf90-146">Our sample so far is fairly simple, but it still demonstrates some of the important guidelines for designs involving delegates.</span></span>

<span data-ttu-id="0bf90-147">Použití delegáta typů front definovaných v rámci základní usnadňuje uživatelům pracovat s delegáty.</span><span class="sxs-lookup"><span data-stu-id="0bf90-147">Using the delegate types defined in the Core Framework makes it easier for users to work with the delegates.</span></span> <span data-ttu-id="0bf90-148">Nemusíte definovat nové typy a vývojáře, kteří používají vaše knihovna není potřeba další typy nové, specializované delegáta.</span><span class="sxs-lookup"><span data-stu-id="0bf90-148">You don't need to define new types, and developers using your library do not need to learn new, specialized delegate types.</span></span>

<span data-ttu-id="0bf90-149">Rozhraní používá se jako minimální a co nejpružnější: Pokud chcete vytvořit nové protokoly výstup, musíte vytvořit jednu metodu.</span><span class="sxs-lookup"><span data-stu-id="0bf90-149">The interfaces used are as minimal and as flexible as possible: To create a new output logger, you must create one method.</span></span> <span data-ttu-id="0bf90-150">Tato metoda může být statickou metodu nebo metody instance.</span><span class="sxs-lookup"><span data-stu-id="0bf90-150">That method may be a static method, or an instance method.</span></span> <span data-ttu-id="0bf90-151">Může mít žádné přístup.</span><span class="sxs-lookup"><span data-stu-id="0bf90-151">It may have any access.</span></span>

## <a name="formatting-output"></a><span data-ttu-id="0bf90-152">Výstupní formátování</span><span class="sxs-lookup"><span data-stu-id="0bf90-152">Formatting Output</span></span>

<span data-ttu-id="0bf90-153">Můžeme zpřístupnit tento první verzi bit robustnější a poté spusťte vytváření jiným mechanismem protokolování.</span><span class="sxs-lookup"><span data-stu-id="0bf90-153">Let's make this first version a bit more robust, and then start creating other logging mechanisms.</span></span>

<span data-ttu-id="0bf90-154">V dalším kroku přidejme několik argumenty, které mají `LogMessage()` metoda tak, aby třídě protokolu vytváří více strukturovaných zprávy:</span><span class="sxs-lookup"><span data-stu-id="0bf90-154">Next, let's add a few arguments to the `LogMessage()` method so that your log class creates more structured messages:</span></span>

[!code-csharp[Severity](../../samples/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

<span data-ttu-id="0bf90-155">V dalším kroku provedeme pomocí této `Severity` výstupu argument k filtrování zprávy, které se odesílají do protokolu.</span><span class="sxs-lookup"><span data-stu-id="0bf90-155">Next, let's make use of that `Severity` argument to filter the messages that are sent to the log's output.</span></span> 

[!code-csharp[FinalLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a><span data-ttu-id="0bf90-156">Postupy</span><span class="sxs-lookup"><span data-stu-id="0bf90-156">Practices</span></span>

<span data-ttu-id="0bf90-157">Přidali jste nové funkce protokolování infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="0bf90-157">You've added new features to the logging infrastructure.</span></span> <span data-ttu-id="0bf90-158">Vzhledem k tomu, že komponenta protokolovacího nástroje je velmi volně vázány do jakéhokoli výstupu mechanismu, mohou být přidány tyto nové funkce bez dopadu na kód implementace delegáta protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="0bf90-158">Because the logger component is very loosely coupled to any output mechanism, these new features can be added with no impact on any of the code implementing the logger delegate.</span></span>

<span data-ttu-id="0bf90-159">Jak zachovat sestavování to, zobrazí se další příklady jak tato volné párování umožňuje větší flexibilitu při aktualizaci části webu bez uložení změn do jiných umístění.</span><span class="sxs-lookup"><span data-stu-id="0bf90-159">As you keep building this, you'll see more examples of how this loose coupling enables greater flexibility in updating parts of the site without any changes to other locations.</span></span> <span data-ttu-id="0bf90-160">Ve skutečnosti ve větší aplikaci třídy výstupu protokolovacího nástroje může být v jiném sestavení a ani je třeba znovu sestavit.</span><span class="sxs-lookup"><span data-stu-id="0bf90-160">In fact, in a larger application, the logger output classes might be in a different assembly, and not even need to be rebuilt.</span></span>

## <a name="building-a-second-output-engine"></a><span data-ttu-id="0bf90-161">Druhý modul výstup sestavení</span><span class="sxs-lookup"><span data-stu-id="0bf90-161">Building a Second Output Engine</span></span>

<span data-ttu-id="0bf90-162">Součásti protokolu pochází podél také.</span><span class="sxs-lookup"><span data-stu-id="0bf90-162">The Log component is coming along well.</span></span> <span data-ttu-id="0bf90-163">Umožňuje přidat jeden další modul výstup, který zaznamenává zprávy do souboru.</span><span class="sxs-lookup"><span data-stu-id="0bf90-163">Let's add one more output engine that logs messages to a file.</span></span> <span data-ttu-id="0bf90-164">Bude jím modul výstupní zapojí o něco víc.</span><span class="sxs-lookup"><span data-stu-id="0bf90-164">This will be a slightly more involved output engine.</span></span> <span data-ttu-id="0bf90-165">Je třída, který zapouzdřuje operací se soubory a zajišťuje, že soubor je vždy zavřel po každém zápisu.</span><span class="sxs-lookup"><span data-stu-id="0bf90-165">It will be a class that encapsulates the file operations, and ensures that the file is always closed after each write.</span></span> <span data-ttu-id="0bf90-166">Který zajišťuje, že všechna data vyprazdňuje na disk po vygenerování každé zprávě.</span><span class="sxs-lookup"><span data-stu-id="0bf90-166">That ensures that all the data is flushed to disk after each message is generated.</span></span>

<span data-ttu-id="0bf90-167">Tady je tento soubor na základě protokoly:</span><span class="sxs-lookup"><span data-stu-id="0bf90-167">Here is that file based logger:</span></span>

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]


<span data-ttu-id="0bf90-168">Po vytvoření této třídy, můžete vytvořit jeho instanci a jeho LogMessage – metoda přiloží k komponenta protokolovacího nástroje:</span><span class="sxs-lookup"><span data-stu-id="0bf90-168">Once you've created this class, you can instantiate it and it attaches its LogMessage method to the Logger component:</span></span>

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

<span data-ttu-id="0bf90-169">Tyto dva se vzájemně nevylučují.</span><span class="sxs-lookup"><span data-stu-id="0bf90-169">These two are not mutually exclusive.</span></span> <span data-ttu-id="0bf90-170">Můžete připojit obě metody protokolu a generovat zpráv do konzoly a soubor:</span><span class="sxs-lookup"><span data-stu-id="0bf90-170">You could attach both log methods and generate messages to the console and a file:</span></span>

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

<span data-ttu-id="0bf90-171">Později i ve stejné aplikaci, můžete odebrat jedním z delegáty bez dalších problémů v systému:</span><span class="sxs-lookup"><span data-stu-id="0bf90-171">Later, even in the same application, you can remove one of the delegates without any other issues to the system:</span></span>

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="0bf90-172">Postupy</span><span class="sxs-lookup"><span data-stu-id="0bf90-172">Practices</span></span>

<span data-ttu-id="0bf90-173">Nyní jste přidali Druhá obslužná rutina výstup pro dílčí systém protokolování.</span><span class="sxs-lookup"><span data-stu-id="0bf90-173">Now, you've added a second output handler for the logging sub-system.</span></span>
<span data-ttu-id="0bf90-174">Tato potřebuje trochu další infrastrukturu pro správně podporu systému souborů.</span><span class="sxs-lookup"><span data-stu-id="0bf90-174">This one needs a bit more infrastructure to correctly support the file system.</span></span> <span data-ttu-id="0bf90-175">Delegát je metoda instance.</span><span class="sxs-lookup"><span data-stu-id="0bf90-175">The delegate is an instance method.</span></span> <span data-ttu-id="0bf90-176">Je také soukromá metoda.</span><span class="sxs-lookup"><span data-stu-id="0bf90-176">It's also a private method.</span></span>
<span data-ttu-id="0bf90-177">Není nutné pro větší usnadnění, protože delegáta infrastruktury můžete připojit delegáty.</span><span class="sxs-lookup"><span data-stu-id="0bf90-177">There's no need for greater accessibility because the delegate infrastructure can connect the delegates.</span></span>

<span data-ttu-id="0bf90-178">Druhý návrhu na základě delegáta umožňuje více metod výstupu bez jakékoli další kód.</span><span class="sxs-lookup"><span data-stu-id="0bf90-178">Second, the delegate-based design enables multiple output methods without any extra code.</span></span> <span data-ttu-id="0bf90-179">Nemusíte vytvářet žádné další infrastrukturu pro podporu více metod výstup.</span><span class="sxs-lookup"><span data-stu-id="0bf90-179">You don't need to build any additional infrastructure to support multiple output methods.</span></span> <span data-ttu-id="0bf90-180">Jednoduše budou jinou metodu na seznamu vyvolání.</span><span class="sxs-lookup"><span data-stu-id="0bf90-180">They simply become another method on the invocation list.</span></span>

<span data-ttu-id="0bf90-181">Věnujte zvláštní pozornost kód v souboru protokolování způsob výstupu.</span><span class="sxs-lookup"><span data-stu-id="0bf90-181">Pay special attention to the code in the file logging output method.</span></span> <span data-ttu-id="0bf90-182">Je zakódované Ujistěte se, že nevyvolá jakékoli výjimky.</span><span class="sxs-lookup"><span data-stu-id="0bf90-182">It is coded to ensure that it does not throw any exceptions.</span></span> <span data-ttu-id="0bf90-183">Když to není vždy nezbytně nutné, je vhodné.</span><span class="sxs-lookup"><span data-stu-id="0bf90-183">While this isn't always strictly necessary, it's often a good practice.</span></span> <span data-ttu-id="0bf90-184">Pokud některou z metod delegát vyvolá výjimku, nebude volána zbývající delegáti, které jsou pro vyvolání.</span><span class="sxs-lookup"><span data-stu-id="0bf90-184">If either of the delegate methods throws an exception, the remaining delegates that are on the invocation won't be invoked.</span></span>

<span data-ttu-id="0bf90-185">Jako poslední Poznámka protokolovacího nástroje souboru musí spravovat její prostředky otvírání a zavírání souborů v každé zprávě protokolu.</span><span class="sxs-lookup"><span data-stu-id="0bf90-185">As a last note, the file logger must manage its resources by opening and closing the file on each log message.</span></span> <span data-ttu-id="0bf90-186">Mohli byste nechat otevřený soubor a implementovat rozhraní IDisposable po dokončení zavřete soubor.</span><span class="sxs-lookup"><span data-stu-id="0bf90-186">You could choose to keep the file open and implement IDisposable to close the file when you are completed.</span></span>
<span data-ttu-id="0bf90-187">Některé z metod má své výhody a nevýhody.</span><span class="sxs-lookup"><span data-stu-id="0bf90-187">Either method has its advantages and disadvantages.</span></span> <span data-ttu-id="0bf90-188">Jak vytvořit trochu další párování mezi třídami.</span><span class="sxs-lookup"><span data-stu-id="0bf90-188">Both do create a bit more coupling between the classes.</span></span>

<span data-ttu-id="0bf90-189">Žádný kód ve třídě protokolovacího nástroje by musela být aktualizované kvůli podpoře buď scénář.</span><span class="sxs-lookup"><span data-stu-id="0bf90-189">None of the code in the Logger class would need to be updated in order to support either scenario.</span></span>

## <a name="handling-null-delegates"></a><span data-ttu-id="0bf90-190">Zpracování Null delegáti</span><span class="sxs-lookup"><span data-stu-id="0bf90-190">Handling Null Delegates</span></span>

<span data-ttu-id="0bf90-191">Nakonec umožňuje aktualizovat metodu LogMessage tak, aby se robustní pro případy, pokud je vybrána mechanismus žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="0bf90-191">Finally, let's update the LogMessage method so that it is robust for those cases when no output mechanism is selected.</span></span> <span data-ttu-id="0bf90-192">Aktuální implementace vyvolá výjimku `NullReferenceException` při `WriteMessage` delegáta nemá seznam vyvolání připojen.</span><span class="sxs-lookup"><span data-stu-id="0bf90-192">The current implementation will throw a `NullReferenceException` when the `WriteMessage` delegate does not have an invocation list attached.</span></span>
<span data-ttu-id="0bf90-193">Dáváte přednost tomu návrh, který pokračuje bez upozornění při byly připojeny žádné metody.</span><span class="sxs-lookup"><span data-stu-id="0bf90-193">You may prefer a design that silently continues when no methods have been attached.</span></span> <span data-ttu-id="0bf90-194">Toto je snadný při použití null podmíněný operátor v kombinaci s `Delegate.Invoke()` metoda:</span><span class="sxs-lookup"><span data-stu-id="0bf90-194">This is easy using the null conditional operator, combined with the `Delegate.Invoke()` method:</span></span>

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

<span data-ttu-id="0bf90-195">Podmíněný operátor s hodnotou null (`?.`) při zkratům levý operand (`WriteMessage` v tomto případě) je null, což znamená žádné pokusu o zprávu protokolu.</span><span class="sxs-lookup"><span data-stu-id="0bf90-195">The null conditional operator (`?.`) short-circuits when the left operand (`WriteMessage` in this case) is null, which means no attempt is made to log a message.</span></span>

<span data-ttu-id="0bf90-196">Nebude možné najít `Invoke()` metoda uvedeny v dokumentaci k `System.Delegate` nebo `System.MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="0bf90-196">You won't find the `Invoke()` method listed in the documentation for `System.Delegate` or `System.MulticastDelegate`.</span></span> <span data-ttu-id="0bf90-197">Kompilátor generuje bezpečnost typů `Invoke` delegovat metoda pro libovolný typ deklarovaný.</span><span class="sxs-lookup"><span data-stu-id="0bf90-197">The compiler generates a type safe `Invoke` method for any delegate type declared.</span></span> <span data-ttu-id="0bf90-198">V tomto příkladu to znamená `Invoke` přebírá jediný `string` argument, a má typ vrácené hodnoty void.</span><span class="sxs-lookup"><span data-stu-id="0bf90-198">In this example, that means `Invoke` takes a single `string` argument, and has a void return type.</span></span>

## <a name="summary-of-practices"></a><span data-ttu-id="0bf90-199">Souhrn postupů</span><span class="sxs-lookup"><span data-stu-id="0bf90-199">Summary of Practices</span></span>

<span data-ttu-id="0bf90-200">Seznámili jste se začátku protokolu součásti, která by mohla být rozšířena s další zapisovače a další funkce.</span><span class="sxs-lookup"><span data-stu-id="0bf90-200">You've seen the beginnings of a log component that could be expanded with other writers, and other features.</span></span> <span data-ttu-id="0bf90-201">Pomocí delegátů v návrhu jsou velmi volně vázány tyto různé součásti.</span><span class="sxs-lookup"><span data-stu-id="0bf90-201">By using delegates in the design these different components are very loosely coupled.</span></span> <span data-ttu-id="0bf90-202">To poskytuje několik výhod.</span><span class="sxs-lookup"><span data-stu-id="0bf90-202">This provides several advantages.</span></span> <span data-ttu-id="0bf90-203">Je velmi snadné vytvořit nový výstupní mechanismy a jejich připojení k systému.</span><span class="sxs-lookup"><span data-stu-id="0bf90-203">It's very easy to create new output mechanisms and attach them to the system.</span></span> <span data-ttu-id="0bf90-204">Tyto další mechanismy, stačí jeden metoda: metody, která zapisuje zprávy protokolu.</span><span class="sxs-lookup"><span data-stu-id="0bf90-204">These other mechanisms only need one method: the method that writes the log message.</span></span> <span data-ttu-id="0bf90-205">Je k návrhu, který je velmi odolné, když se přidají nové funkce.</span><span class="sxs-lookup"><span data-stu-id="0bf90-205">It's a design that is very resilient when new features are added.</span></span> <span data-ttu-id="0bf90-206">Kontrakt potřebné pro všechny zapisovače je implementovat jednu metodu.</span><span class="sxs-lookup"><span data-stu-id="0bf90-206">The contract required for any writer is to implement one method.</span></span> <span data-ttu-id="0bf90-207">Tato metoda může být statické nebo metodu instance.</span><span class="sxs-lookup"><span data-stu-id="0bf90-207">That method could be a static or instance method.</span></span> <span data-ttu-id="0bf90-208">To může být veřejné, privátní nebo jiné právní přístup.</span><span class="sxs-lookup"><span data-stu-id="0bf90-208">It could be public, private, or any other legal access.</span></span>

<span data-ttu-id="0bf90-209">Třída protokolovacího nástroje můžete nastavit libovolný počet vylepšení nebo změny bez zavedení nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="0bf90-209">The Logger class can make any number of enhancements or changes without introducing breaking changes.</span></span> <span data-ttu-id="0bf90-210">Podobně jako všechny třídy nelze změnit veřejné rozhraní API bez riziko nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="0bf90-210">Like any class, you cannot modify the public API without the risk of breaking changes.</span></span> <span data-ttu-id="0bf90-211">Ale protože párování mezi protokolovacího nástroje a všechny moduly výstupu je pouze prostřednictvím delegáta, se podílejí žádné jiné typy (například rozhraní nebo základní třídy).</span><span class="sxs-lookup"><span data-stu-id="0bf90-211">But, because the coupling between the logger and any output engines is only through the delegate, no other types (like interfaces or base classes) are involved.</span></span> <span data-ttu-id="0bf90-212">Vazba je co nejmenší.</span><span class="sxs-lookup"><span data-stu-id="0bf90-212">The coupling is as small as possible.</span></span>

[<span data-ttu-id="0bf90-213">Next</span><span class="sxs-lookup"><span data-stu-id="0bf90-213">Next</span></span>](events-overview.md)
