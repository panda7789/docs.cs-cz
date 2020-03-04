---
title: 'Návod: zachování objektu pomocíC#'
ms.date: 04/26/2018
ms.openlocfilehash: 9531909bdf1ed61305c292411ef2cd08b7b67465
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240464"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="65bd0-102">Návod: uchování objektu pomocí jazyka C\#</span><span class="sxs-lookup"><span data-stu-id="65bd0-102">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="65bd0-103">Můžete použít serializaci k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načíst je při příštím vytvoření instance objektu.</span><span class="sxs-lookup"><span data-stu-id="65bd0-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="65bd0-104">V tomto návodu vytvoříte základní objekt `Loan` a zachová jeho data do souboru.</span><span class="sxs-lookup"><span data-stu-id="65bd0-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="65bd0-105">Po opětovném vytvoření objektu načtěte data ze souboru.</span><span class="sxs-lookup"><span data-stu-id="65bd0-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65bd0-106">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="65bd0-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="65bd0-107">Pokud aplikace musí vytvořit soubor, musí mít tato aplikace oprávnění `Create` pro tuto složku.</span><span class="sxs-lookup"><span data-stu-id="65bd0-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="65bd0-108">Oprávnění se nastavují pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="65bd0-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="65bd0-109">Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění, menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="65bd0-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="65bd0-110">Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a udělit pouze `Read` oprávnění k jednomu souboru (místo oprávnění k vytváření složky).</span><span class="sxs-lookup"><span data-stu-id="65bd0-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="65bd0-111">Je také bezpečnější zapsat data do složek uživatele než do kořenové složky nebo do složky Program Files.</span><span class="sxs-lookup"><span data-stu-id="65bd0-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65bd0-112">Tento příklad ukládá data v binárním souboru formátu.</span><span class="sxs-lookup"><span data-stu-id="65bd0-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="65bd0-113">Tyto formáty by se neměly používat pro citlivá data, jako jsou hesla nebo informace o kreditních kartách.</span><span class="sxs-lookup"><span data-stu-id="65bd0-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65bd0-114">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="65bd0-114">Prerequisites</span></span>

- <span data-ttu-id="65bd0-115">Pro sestavení a spuštění nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="65bd0-115">To build and run, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

- <span data-ttu-id="65bd0-116">Pokud jste to ještě neudělali, nainstalujte svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="65bd0-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="65bd0-117">Potřebujete nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="65bd0-117">Need to install a code editor?</span></span> <span data-ttu-id="65bd0-118">Vyzkoušejte [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="65bd0-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="65bd0-119">Příklad vyžaduje C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="65bd0-119">The example requires C# 7.3.</span></span> <span data-ttu-id="65bd0-120">Viz [Vyberte C# jazykovou verzi](../../../language-reference/configure-language-version.md) .</span><span class="sxs-lookup"><span data-stu-id="65bd0-120">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span> 

<span data-ttu-id="65bd0-121">Ukázkový kód si můžete prohlédnout online [v úložišti GitHub Samples .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="65bd0-121">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="65bd0-122">Vytvoření objektu výpůjčky</span><span class="sxs-lookup"><span data-stu-id="65bd0-122">Creating the loan object</span></span>

<span data-ttu-id="65bd0-123">Prvním krokem je vytvoření třídy `Loan` a konzolové aplikace, která používá třídu:</span><span class="sxs-lookup"><span data-stu-id="65bd0-123">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="65bd0-124">Vytvořte novou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="65bd0-124">Create a new application.</span></span> <span data-ttu-id="65bd0-125">Zadejte `dotnet new console -o serialization` pro vytvoření nové konzolové aplikace v podadresáři s názvem `serialization`.</span><span class="sxs-lookup"><span data-stu-id="65bd0-125">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="65bd0-126">Otevřete aplikaci v editoru a přidejte novou třídu s názvem `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="65bd0-126">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="65bd0-127">Do své `Loan` třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="65bd0-127">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="65bd0-128">Také budete muset vytvořit aplikaci, která používá třídu `Loan`.</span><span class="sxs-lookup"><span data-stu-id="65bd0-128">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="65bd0-129">Serializace objektu výpůjčky</span><span class="sxs-lookup"><span data-stu-id="65bd0-129">Serialize the loan object</span></span>

1. <span data-ttu-id="65bd0-130">Otevřete `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="65bd0-130">Open `Program.cs`.</span></span> <span data-ttu-id="65bd0-131">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="65bd0-131">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

<span data-ttu-id="65bd0-132">Přidejte obslužnou rutinu události pro událost `PropertyChanged` a několik řádků pro úpravu objektu `Loan` a zobrazte změny.</span><span class="sxs-lookup"><span data-stu-id="65bd0-132">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="65bd0-133">Můžete zobrazit Přidání v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="65bd0-133">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

<span data-ttu-id="65bd0-134">V tomto okamžiku můžete spustit kód a zobrazit aktuální výstup:</span><span class="sxs-lookup"><span data-stu-id="65bd0-134">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="65bd0-135">Spuštění této aplikace opakovaně vždy zapisuje stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="65bd0-135">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="65bd0-136">Nový objekt výpůjčky se vytvoří pokaždé, když spustíte program.</span><span class="sxs-lookup"><span data-stu-id="65bd0-136">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="65bd0-137">V reálném světě se úrokové sazby pravidelně mění, ale nemusí nutně pokaždé, když je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="65bd0-137">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="65bd0-138">Serializační kód znamená, že zachováte nejnovější úrokovou sazbu mezi instancemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="65bd0-138">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="65bd0-139">V dalším kroku provedete to tak, že do třídy výpůjčky přidáte serializaci.</span><span class="sxs-lookup"><span data-stu-id="65bd0-139">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="65bd0-140">Zachování objektu pomocí serializace</span><span class="sxs-lookup"><span data-stu-id="65bd0-140">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="65bd0-141">Aby bylo možné zachovat hodnoty pro třídu výpůjčky, musíte nejprve označit třídu atributem `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="65bd0-141">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="65bd0-142">Do definice třídy výpůjčky přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="65bd0-142">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="65bd0-143"><xref:System.SerializableAttribute> instruuje kompilátor, že všechno ve třídě lze trvale uložit do souboru.</span><span class="sxs-lookup"><span data-stu-id="65bd0-143">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="65bd0-144">Vzhledem k tomu, že událost `PropertyChanged` nepředstavuje součást grafu objektů, která by měla být uložena, neměla by být serializována.</span><span class="sxs-lookup"><span data-stu-id="65bd0-144">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="65bd0-145">Tím by došlo k serializaci všech objektů, které jsou k této události připojeny.</span><span class="sxs-lookup"><span data-stu-id="65bd0-145">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="65bd0-146">Můžete přidat <xref:System.NonSerializedAttribute> k deklaraci pole pro obslužnou rutinu události `PropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="65bd0-146">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="65bd0-147">Počínaje C# 7,3 můžete přiřadit atributy k poli pro zálohování automaticky implementované vlastnosti pomocí `field` cílové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="65bd0-147">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="65bd0-148">Následující kód přidá vlastnost `TimeLastLoaded` a označí ji jako neserializovatelný:</span><span class="sxs-lookup"><span data-stu-id="65bd0-148">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="65bd0-149">Dalším krokem je přidání kódu serializace do aplikace LoanApp.</span><span class="sxs-lookup"><span data-stu-id="65bd0-149">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="65bd0-150">Aby bylo možné serializovat třídu a zapsat ji do souboru, použijte obory názvů <xref:System.IO> a <xref:System.Runtime.Serialization.Formatters.Binary>.</span><span class="sxs-lookup"><span data-stu-id="65bd0-150">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="65bd0-151">Chcete-li se vyhnout psaní plně kvalifikovaných názvů, můžete přidat odkazy na nezbytné obory názvů, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="65bd0-151">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

<span data-ttu-id="65bd0-152">Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="65bd0-152">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="65bd0-153">Do třídy přidejte konstantu pro název souboru serializovaných dat, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="65bd0-153">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

<span data-ttu-id="65bd0-154">Dále přidejte následující kód za řádek, který vytvoří objekt `TestLoan`:</span><span class="sxs-lookup"><span data-stu-id="65bd0-154">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

<span data-ttu-id="65bd0-155">Nejdřív musíte ověřit, že soubor existuje.</span><span class="sxs-lookup"><span data-stu-id="65bd0-155">You first must check that the file exists.</span></span> <span data-ttu-id="65bd0-156">Pokud existuje, vytvořte třídu <xref:System.IO.Stream> pro čtení binárního souboru a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třídy k překladu souboru.</span><span class="sxs-lookup"><span data-stu-id="65bd0-156">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="65bd0-157">Také je nutné převést typ datového proudu na typ objektu výpůjčky.</span><span class="sxs-lookup"><span data-stu-id="65bd0-157">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="65bd0-158">Dále je nutné přidat kód k serializaci třídy do souboru.</span><span class="sxs-lookup"><span data-stu-id="65bd0-158">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="65bd0-159">Přidejte následující kód za existující kód v metodě `Main`:</span><span class="sxs-lookup"><span data-stu-id="65bd0-159">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

<span data-ttu-id="65bd0-160">V tuto chvíli můžete znovu sestavit a spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="65bd0-160">At this point, you can again build and run the application.</span></span> <span data-ttu-id="65bd0-161">Při prvním spuštění si všimněte, že úrokové sazby začínají na 7,5 a pak se změní na 7,1.</span><span class="sxs-lookup"><span data-stu-id="65bd0-161">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="65bd0-162">Ukončete aplikaci a pak ji znovu spusťte.</span><span class="sxs-lookup"><span data-stu-id="65bd0-162">Close the application and then run it again.</span></span> <span data-ttu-id="65bd0-163">Nyní aplikace vytiskne zprávu, že si uložil uložený soubor, a úrokovou sazbu je 7,1 ještě před kódem, který ho změnil.</span><span class="sxs-lookup"><span data-stu-id="65bd0-163">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="65bd0-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="65bd0-164">See also</span></span>

- [<span data-ttu-id="65bd0-165">SerializaceC#()</span><span class="sxs-lookup"><span data-stu-id="65bd0-165">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="65bd0-166">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="65bd0-166">C# Programming Guide</span></span>](../..//index.md)
