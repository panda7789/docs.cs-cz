---
title: 'Návod: Zachování objektu pomocíC#'
ms.date: 04/26/2018
ms.openlocfilehash: 88fb589ca2f9a24f861b528bfd601f837e9aac5f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105926"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="5891c-102">Návod: uchování objektu pomocí jazyka C\#</span><span class="sxs-lookup"><span data-stu-id="5891c-102">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="5891c-103">Můžete použít serializaci k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načíst je při příštím vytvoření instance objektu.</span><span class="sxs-lookup"><span data-stu-id="5891c-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="5891c-104">V tomto návodu vytvoříte základní `Loan` objekt a zachová jeho data do souboru.</span><span class="sxs-lookup"><span data-stu-id="5891c-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="5891c-105">Po opětovném vytvoření objektu načtěte data ze souboru.</span><span class="sxs-lookup"><span data-stu-id="5891c-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5891c-106">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="5891c-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="5891c-107">Pokud aplikace musí vytvořit soubor, musí mít `Create` Tato aplikace oprávnění pro tuto složku.</span><span class="sxs-lookup"><span data-stu-id="5891c-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="5891c-108">Oprávnění se nastavují pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="5891c-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="5891c-109">Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění a menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5891c-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="5891c-110">Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` oprávnění pouze k jednomu souboru (místo oprávnění k vytvoření složky).</span><span class="sxs-lookup"><span data-stu-id="5891c-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="5891c-111">Je také bezpečnější zapsat data do složek uživatele než do kořenové složky nebo do složky Program Files.</span><span class="sxs-lookup"><span data-stu-id="5891c-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5891c-112">Tento příklad ukládá data v binárním souboru formátu.</span><span class="sxs-lookup"><span data-stu-id="5891c-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="5891c-113">Tyto formáty by se neměly používat pro citlivá data, jako jsou hesla nebo informace o kreditních kartách.</span><span class="sxs-lookup"><span data-stu-id="5891c-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5891c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5891c-114">Prerequisites</span></span>

- <span data-ttu-id="5891c-115">Pro sestavení a spuštění nainstalujte [.NET Core SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="5891c-115">To build and run, install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span>

- <span data-ttu-id="5891c-116">Pokud jste to ještě neudělali, nainstalujte svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="5891c-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="5891c-117">Potřebujete nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="5891c-117">Need to install a code editor?</span></span> <span data-ttu-id="5891c-118">Vyzkoušejte [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="5891c-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="5891c-119">Příklad vyžaduje C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="5891c-119">The example requires C# 7.3.</span></span> <span data-ttu-id="5891c-120">Viz [ C# vyberte jazykovou verzi](../../../language-reference/configure-language-version.md) .</span><span class="sxs-lookup"><span data-stu-id="5891c-120">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span> 

<span data-ttu-id="5891c-121">Ukázkový kód si můžete prohlédnout online [v úložišti GitHub Samples .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="5891c-121">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="5891c-122">Vytvoření objektu výpůjčky</span><span class="sxs-lookup"><span data-stu-id="5891c-122">Creating the loan object</span></span>

<span data-ttu-id="5891c-123">Prvním krokem je vytvoření `Loan` třídy a konzolové aplikace, která používá třídu:</span><span class="sxs-lookup"><span data-stu-id="5891c-123">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="5891c-124">Vytvořte novou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5891c-124">Create a new application.</span></span> <span data-ttu-id="5891c-125">Zadejte `dotnet new console -o serialization` , chcete-li vytvořit novou konzolovou aplikaci v podadresáři s názvem `serialization`.</span><span class="sxs-lookup"><span data-stu-id="5891c-125">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="5891c-126">Otevřete aplikaci v editoru a přidejte novou třídu s názvem `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="5891c-126">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="5891c-127">Do `Loan` třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="5891c-127">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="5891c-128">Také budete muset vytvořit aplikaci, která používá `Loan` třídu.</span><span class="sxs-lookup"><span data-stu-id="5891c-128">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="5891c-129">Serializace objektu výpůjčky</span><span class="sxs-lookup"><span data-stu-id="5891c-129">Serialize the loan object</span></span>

1. <span data-ttu-id="5891c-130">Otevřít `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="5891c-130">Open `Program.cs`.</span></span> <span data-ttu-id="5891c-131">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="5891c-131">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

<span data-ttu-id="5891c-132">Přidejte obslužnou rutinu události pro `PropertyChanged` událost a několik řádků pro `Loan` úpravu objektu a zobrazte změny.</span><span class="sxs-lookup"><span data-stu-id="5891c-132">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="5891c-133">Můžete zobrazit Přidání v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5891c-133">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

<span data-ttu-id="5891c-134">V tomto okamžiku můžete spustit kód a zobrazit aktuální výstup:</span><span class="sxs-lookup"><span data-stu-id="5891c-134">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="5891c-135">Spuštění této aplikace opakovaně vždy zapisuje stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5891c-135">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="5891c-136">Nový objekt výpůjčky se vytvoří pokaždé, když spustíte program.</span><span class="sxs-lookup"><span data-stu-id="5891c-136">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="5891c-137">V reálném světě se úrokové sazby pravidelně mění, ale nemusí nutně pokaždé, když je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="5891c-137">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="5891c-138">Serializační kód znamená, že zachováte nejnovější úrokovou sazbu mezi instancemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="5891c-138">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="5891c-139">V dalším kroku provedete to tak, že do třídy výpůjčky přidáte serializaci.</span><span class="sxs-lookup"><span data-stu-id="5891c-139">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="5891c-140">Zachování objektu pomocí serializace</span><span class="sxs-lookup"><span data-stu-id="5891c-140">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="5891c-141">Aby bylo možné zachovat hodnoty pro třídu výpůjčky, musíte nejprve označit třídu `Serializable` atributem.</span><span class="sxs-lookup"><span data-stu-id="5891c-141">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="5891c-142">Do definice třídy výpůjčky přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="5891c-142">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="5891c-143">Rozhraní <xref:System.SerializableAttribute> instruuje kompilátor, že všechno ve třídě lze trvale uložit do souboru.</span><span class="sxs-lookup"><span data-stu-id="5891c-143">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="5891c-144">Vzhledem k `PropertyChanged` tomu, že událost nepředstavuje součást grafu objektů, která by měla být uložena, neměla by být serializována.</span><span class="sxs-lookup"><span data-stu-id="5891c-144">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="5891c-145">Tím by došlo k serializaci všech objektů, které jsou k této události připojeny.</span><span class="sxs-lookup"><span data-stu-id="5891c-145">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="5891c-146">Můžete přidat <xref:System.NonSerializedAttribute> do deklarace pole `PropertyChanged` pro obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="5891c-146">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="5891c-147">Počínaje C# 7,3 můžete k poli pro zálohování automaticky implementované vlastnosti připojit atributy pomocí `field` cílové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5891c-147">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="5891c-148">Následující kód přidá `TimeLastLoaded` vlastnost a označí ji jako neserializovatelný:</span><span class="sxs-lookup"><span data-stu-id="5891c-148">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="5891c-149">Dalším krokem je přidání kódu serializace do aplikace LoanApp.</span><span class="sxs-lookup"><span data-stu-id="5891c-149">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="5891c-150">Aby bylo možné serializovat třídu a zapsat ji do souboru, použijte <xref:System.IO> obory názvů a. <xref:System.Runtime.Serialization.Formatters.Binary></span><span class="sxs-lookup"><span data-stu-id="5891c-150">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="5891c-151">Chcete-li se vyhnout psaní plně kvalifikovaných názvů, můžete přidat odkazy na nezbytné obory názvů, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5891c-151">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

<span data-ttu-id="5891c-152">Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="5891c-152">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="5891c-153">Do třídy přidejte konstantu pro název souboru serializovaných dat, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5891c-153">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

<span data-ttu-id="5891c-154">Dále přidejte následující kód za řádek, který vytvoří `TestLoan` objekt:</span><span class="sxs-lookup"><span data-stu-id="5891c-154">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

<span data-ttu-id="5891c-155">Nejdřív musíte ověřit, že soubor existuje.</span><span class="sxs-lookup"><span data-stu-id="5891c-155">You first must check that the file exists.</span></span> <span data-ttu-id="5891c-156">Pokud existuje, vytvořte <xref:System.IO.Stream> třídu pro čtení binárního souboru <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a třídu pro překlad souboru.</span><span class="sxs-lookup"><span data-stu-id="5891c-156">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="5891c-157">Také je nutné převést typ datového proudu na typ objektu výpůjčky.</span><span class="sxs-lookup"><span data-stu-id="5891c-157">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="5891c-158">Dále je nutné přidat kód k serializaci třídy do souboru.</span><span class="sxs-lookup"><span data-stu-id="5891c-158">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="5891c-159">Za existující kód v `Main` metodě přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="5891c-159">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

<span data-ttu-id="5891c-160">V tuto chvíli můžete znovu sestavit a spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5891c-160">At this point, you can again build and run the application.</span></span> <span data-ttu-id="5891c-161">Při prvním spuštění si všimněte, že úrokové sazby začínají na 7,5 a pak se změní na 7,1.</span><span class="sxs-lookup"><span data-stu-id="5891c-161">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="5891c-162">Ukončete aplikaci a pak ji znovu spusťte.</span><span class="sxs-lookup"><span data-stu-id="5891c-162">Close the application and then run it again.</span></span> <span data-ttu-id="5891c-163">Nyní aplikace vytiskne zprávu, že si uložil uložený soubor, a úrokovou sazbu je 7,1 ještě před kódem, který ho změnil.</span><span class="sxs-lookup"><span data-stu-id="5891c-163">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="5891c-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5891c-164">See also</span></span>

- [<span data-ttu-id="5891c-165">SerializaceC#()</span><span class="sxs-lookup"><span data-stu-id="5891c-165">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="5891c-166">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5891c-166">C# Programming Guide</span></span>](../..//index.md)
