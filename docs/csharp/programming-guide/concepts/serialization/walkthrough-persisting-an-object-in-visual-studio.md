---
title: 'Návod: Trvalé objektu pomocí C #'
ms.date: 04/26/2018
ms.openlocfilehash: 85c5d1b711180eda5734d5860d996242c6bc89d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167567"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="59e5a-102">Návod: uchování objektu pomocí C\#</span><span class="sxs-lookup"><span data-stu-id="59e5a-102">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="59e5a-103">Serializace můžete použít k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načítat je při příštím vytvoření instance objektu.</span><span class="sxs-lookup"><span data-stu-id="59e5a-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="59e5a-104">V tomto návodu vytvoříte `Loan` základní objekt a zachováte jeho data do souboru.</span><span class="sxs-lookup"><span data-stu-id="59e5a-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="59e5a-105">Potom načtete data ze souboru při opětovném vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="59e5a-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59e5a-106">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="59e5a-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="59e5a-107">Pokud aplikace musí vytvořit soubor, musí `Create` mít oprávnění pro složku.</span><span class="sxs-lookup"><span data-stu-id="59e5a-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="59e5a-108">Oprávnění jsou nastavena pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="59e5a-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="59e5a-109">Pokud soubor již existuje, aplikace `Write` potřebuje pouze oprávnění, menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="59e5a-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="59e5a-110">Pokud je to možné, je bezpečnější vytvořit soubor `Read` během nasazení a udělit oprávnění pouze k jednomu souboru (namísto vytvořit oprávnění pro složku).</span><span class="sxs-lookup"><span data-stu-id="59e5a-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="59e5a-111">Také je bezpečnější zapisovat data do uživatelských složek než do kořenové složky nebo do složky Program Files.</span><span class="sxs-lookup"><span data-stu-id="59e5a-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59e5a-112">Tento příklad ukládá data v binárním formátu souboru.</span><span class="sxs-lookup"><span data-stu-id="59e5a-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="59e5a-113">Tyto formáty by neměly být používány pro citlivá data, jako jsou hesla nebo informace o kreditní kartě.</span><span class="sxs-lookup"><span data-stu-id="59e5a-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59e5a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59e5a-114">Prerequisites</span></span>

- <span data-ttu-id="59e5a-115">Chcete-li vytvořit a spustit, nainstalujte sadu [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="59e5a-115">To build and run, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

- <span data-ttu-id="59e5a-116">Pokud jste tak ještě neučinili, nainstalujte si svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="59e5a-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="59e5a-117">Potřebujete nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="59e5a-117">Need to install a code editor?</span></span> <span data-ttu-id="59e5a-118">Vyzkoušejte [visual studio!](https://visualstudio.com/downloads)</span><span class="sxs-lookup"><span data-stu-id="59e5a-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="59e5a-119">Příklad vyžaduje C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="59e5a-119">The example requires C# 7.3.</span></span> <span data-ttu-id="59e5a-120">Viz [Výběr jazykové verze jazyka C#](../../../language-reference/configure-language-version.md)</span><span class="sxs-lookup"><span data-stu-id="59e5a-120">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span>

<span data-ttu-id="59e5a-121">Ukázkový kód můžete zkontrolovat online [v úložišti .NET samples GitHub](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="59e5a-121">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="59e5a-122">Vytvoření objektu půjčky</span><span class="sxs-lookup"><span data-stu-id="59e5a-122">Creating the loan object</span></span>

<span data-ttu-id="59e5a-123">Prvním krokem je vytvoření `Loan` třídy a konzolové aplikace, která používá třídu:</span><span class="sxs-lookup"><span data-stu-id="59e5a-123">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="59e5a-124">Vytvořte novou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="59e5a-124">Create a new application.</span></span> <span data-ttu-id="59e5a-125">Chcete-li `dotnet new console -o serialization` vytvořit novou konzolovou aplikaci v podadresáři s názvem `serialization`.</span><span class="sxs-lookup"><span data-stu-id="59e5a-125">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="59e5a-126">Otevřete aplikaci v editoru a `Loan.cs`přidejte novou třídu s názvem .</span><span class="sxs-lookup"><span data-stu-id="59e5a-126">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="59e5a-127">Přidejte do třídy `Loan` následující kód:</span><span class="sxs-lookup"><span data-stu-id="59e5a-127">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="59e5a-128">Budete také muset vytvořit aplikaci, `Loan` která používá třídu.</span><span class="sxs-lookup"><span data-stu-id="59e5a-128">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="59e5a-129">Serializace objektu půjčky</span><span class="sxs-lookup"><span data-stu-id="59e5a-129">Serialize the loan object</span></span>

1. <span data-ttu-id="59e5a-130">Otevřete `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="59e5a-130">Open `Program.cs`.</span></span> <span data-ttu-id="59e5a-131">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="59e5a-131">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

<span data-ttu-id="59e5a-132">Přidejte obslužnou rutinu `PropertyChanged` události pro `Loan` událost a několik řádků pro úpravu objektu a zobrazení změn.</span><span class="sxs-lookup"><span data-stu-id="59e5a-132">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="59e5a-133">Můžete vidět dodatky v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="59e5a-133">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

<span data-ttu-id="59e5a-134">V tomto okamžiku můžete spustit kód a zobrazit aktuální výstup:</span><span class="sxs-lookup"><span data-stu-id="59e5a-134">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="59e5a-135">Spuštění této aplikace opakovaně vždy zapíše stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="59e5a-135">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="59e5a-136">Při každém spuštění programu je vytvořen nový objekt Loan.</span><span class="sxs-lookup"><span data-stu-id="59e5a-136">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="59e5a-137">V reálném světě se úrokové sazby pravidelně mění, ale ne nutně při každém spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="59e5a-137">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="59e5a-138">Serializační kód znamená zachování nejnovější úrokové sazby mezi instancemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="59e5a-138">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="59e5a-139">V dalším kroku provedete právě to přidáním serializace do třídy Loan.</span><span class="sxs-lookup"><span data-stu-id="59e5a-139">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="59e5a-140">Použití serializace k zachování objektu</span><span class="sxs-lookup"><span data-stu-id="59e5a-140">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="59e5a-141">Chcete-li zachovat hodnoty pro loan třídy, musíte nejprve označit třídu atributem. `Serializable`</span><span class="sxs-lookup"><span data-stu-id="59e5a-141">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="59e5a-142">Nad definici třídy Loan přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="59e5a-142">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="59e5a-143">Říká <xref:System.SerializableAttribute> kompilátoru, že vše ve třídě může být trvalé do souboru.</span><span class="sxs-lookup"><span data-stu-id="59e5a-143">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="59e5a-144">Vzhledem `PropertyChanged` k tomu, že událost nepředstavuje část grafu objektu, který by měl být uložen, by neměl být serializován.</span><span class="sxs-lookup"><span data-stu-id="59e5a-144">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="59e5a-145">Tím by serializovat všechny objekty, které jsou připojeny k této události.</span><span class="sxs-lookup"><span data-stu-id="59e5a-145">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="59e5a-146">Můžete přidat <xref:System.NonSerializedAttribute> do deklarace pole `PropertyChanged` pro obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="59e5a-146">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="59e5a-147">Počínaje C# 7.3, můžete připojit atributy k záložnímu poli automaticky `field` implementované vlastnosti pomocí cílové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="59e5a-147">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="59e5a-148">Následující kód přidá `TimeLastLoaded` vlastnost a označí ji jako neserializovatelné:</span><span class="sxs-lookup"><span data-stu-id="59e5a-148">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="59e5a-149">Dalším krokem je přidání serializačního kódu do aplikace LoanApp.</span><span class="sxs-lookup"><span data-stu-id="59e5a-149">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="59e5a-150">Chcete-li třídu serializovat a zapsat do souboru, použijte obory názvů <xref:System.IO> a. <xref:System.Runtime.Serialization.Formatters.Binary></span><span class="sxs-lookup"><span data-stu-id="59e5a-150">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="59e5a-151">Chcete-li se vyhnout zadávání plně kvalifikovaných názvů, můžete přidat odkazy na nezbytné jmenné prostory, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="59e5a-151">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

<span data-ttu-id="59e5a-152">Dalším krokem je přidání kódu pro rekonstrukci objektu ze souboru při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="59e5a-152">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="59e5a-153">Přidejte konstantu do třídy pro název souboru serializovaných dat, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="59e5a-153">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

<span data-ttu-id="59e5a-154">Dále přidejte následující kód za řádek, který vytvoří `TestLoan` objekt:</span><span class="sxs-lookup"><span data-stu-id="59e5a-154">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

<span data-ttu-id="59e5a-155">Nejprve je nutné zkontrolovat, zda soubor existuje.</span><span class="sxs-lookup"><span data-stu-id="59e5a-155">You first must check that the file exists.</span></span> <span data-ttu-id="59e5a-156">Pokud existuje, vytvořte <xref:System.IO.Stream> třídu pro čtení <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> binárního souboru a třídu pro překlad souboru.</span><span class="sxs-lookup"><span data-stu-id="59e5a-156">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="59e5a-157">Je také nutné převést z typu datového proudu na typ objektu Loan.</span><span class="sxs-lookup"><span data-stu-id="59e5a-157">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="59e5a-158">Dále je nutné přidat kód serializovat třídy do souboru.</span><span class="sxs-lookup"><span data-stu-id="59e5a-158">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="59e5a-159">Přidejte následující kód za existující `Main` kód v metodě:</span><span class="sxs-lookup"><span data-stu-id="59e5a-159">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

<span data-ttu-id="59e5a-160">V tomto okamžiku můžete znovu sestavit a spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="59e5a-160">At this point, you can again build and run the application.</span></span> <span data-ttu-id="59e5a-161">Při prvním spuštění si všimněte, že úrokové sazby začínají na 7,5 a pak se změní na 7,1.</span><span class="sxs-lookup"><span data-stu-id="59e5a-161">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="59e5a-162">Zavřete aplikaci a spusťte ji znovu.</span><span class="sxs-lookup"><span data-stu-id="59e5a-162">Close the application and then run it again.</span></span> <span data-ttu-id="59e5a-163">Nyní aplikace vytiskne zprávu, že si přečetl uložený soubor a úroková sazba je 7.1 ještě před kódem, který jej změní.</span><span class="sxs-lookup"><span data-stu-id="59e5a-163">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="59e5a-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="59e5a-164">See also</span></span>

- [<span data-ttu-id="59e5a-165">Serializace (C#)</span><span class="sxs-lookup"><span data-stu-id="59e5a-165">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="59e5a-166">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="59e5a-166">C# Programming Guide</span></span>](../..//index.md)
