---
title: 'Návod: Uchování objektu pomocí jazyka C#'
ms.date: 04/26/2018
ms.openlocfilehash: 6c9719dc3aaf997ea144515a553f787450e54041
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956179"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="63c1a-102">Návod: uchování objektu pomocí jazyka C#</span><span class="sxs-lookup"><span data-stu-id="63c1a-102">Walkthrough: persisting an object using C#</span></span> #

<span data-ttu-id="63c1a-103">Serializace můžete použít k uchování dat objektu mezi instance, které umožňuje ukládat hodnoty a je načtou při příštím vytvoření instance objektu.</span><span class="sxs-lookup"><span data-stu-id="63c1a-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="63c1a-104">V tomto návodu vytvoříte základní `Loan` objektu a zachovat data do souboru.</span><span class="sxs-lookup"><span data-stu-id="63c1a-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="63c1a-105">Když znovu vytvoříte objekt se budou ze souboru načítat data.</span><span class="sxs-lookup"><span data-stu-id="63c1a-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63c1a-106">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="63c1a-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="63c1a-107">Pokud aplikace musí vytvořit soubor, musí mít tuto aplikaci `Create` oprávnění pro složku.</span><span class="sxs-lookup"><span data-stu-id="63c1a-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="63c1a-108">Oprávnění jsou nastavená pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="63c1a-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="63c1a-109">Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění, nižší úrovní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="63c1a-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="63c1a-110">Pokud je to možné, je bezpečnější k vytvoření tohoto souboru během nasazení a udělit pouze `Read` oprávnění do jednoho souboru (a nikoli vytvořit oprávnění pro složku).</span><span class="sxs-lookup"><span data-stu-id="63c1a-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="63c1a-111">Navíc je bezpečnější zapsat data do složek uživatele než do kořenové složky nebo ve složce Program Files.</span><span class="sxs-lookup"><span data-stu-id="63c1a-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63c1a-112">Tento příklad ukládá data v binárním formátu souboru.</span><span class="sxs-lookup"><span data-stu-id="63c1a-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="63c1a-113">Tyto formáty by nemělo být použito pro citlivých dat, třeba hesla nebo informace o kreditní kartě.</span><span class="sxs-lookup"><span data-stu-id="63c1a-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63c1a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63c1a-114">Prerequisites</span></span>

* <span data-ttu-id="63c1a-115">Sestavení a spuštění, nainstalujte [.NET Core SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="63c1a-115">To build and run, install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="63c1a-116">Pokud jste to ještě neudělali, nainstalujte editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="63c1a-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="63c1a-117">Je potřeba nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="63c1a-117">Need to install a code editor?</span></span> <span data-ttu-id="63c1a-118">Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="63c1a-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

<span data-ttu-id="63c1a-119">Můžete zkontrolovat ukázkový kód online [v úložišti GitHub ukázky rozhraní .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="63c1a-119">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="63c1a-120">Vytvoření objektu úvěr</span><span class="sxs-lookup"><span data-stu-id="63c1a-120">Creating the loan object</span></span>

<span data-ttu-id="63c1a-121">Prvním krokem je vytvoření `Loan` třídy a konzolovou aplikaci, která používá třídu:</span><span class="sxs-lookup"><span data-stu-id="63c1a-121">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="63c1a-122">Vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="63c1a-122">Create a new application.</span></span> <span data-ttu-id="63c1a-123">Typ `dotnet new console -o serialization` k vytvoření nové aplikace konzoly v podadresáři s názvem `serialization`.</span><span class="sxs-lookup"><span data-stu-id="63c1a-123">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="63c1a-124">Otevřete aplikaci ve svém editoru a přidejte novou třídu s názvem `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="63c1a-124">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="63c1a-125">Přidejte následující kód do vaší `Loan` třídy:</span><span class="sxs-lookup"><span data-stu-id="63c1a-125">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="63c1a-126">Budete také muset vytvořit aplikaci, která používá `Loan` třídy.</span><span class="sxs-lookup"><span data-stu-id="63c1a-126">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="63c1a-127">Serializaci objektu úvěr</span><span class="sxs-lookup"><span data-stu-id="63c1a-127">Serialize the loan object</span></span>

1. <span data-ttu-id="63c1a-128">Otevřete `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="63c1a-128">Open `Program.cs`.</span></span> <span data-ttu-id="63c1a-129">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="63c1a-129">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

<span data-ttu-id="63c1a-130">Přidání obslužné rutiny události pro `PropertyChanged` událostí a zadání několika řádků změnit `Loan` objektu a zobrazit změny.</span><span class="sxs-lookup"><span data-stu-id="63c1a-130">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="63c1a-131">Zobrazí se dodatky v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="63c1a-131">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

<span data-ttu-id="63c1a-132">V tomto okamžiku můžete spustit kód a zobrazit aktuální výstup:</span><span class="sxs-lookup"><span data-stu-id="63c1a-132">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="63c1a-133">Spuštění této aplikace opakovaně vždy zapíše stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="63c1a-133">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="63c1a-134">Nový objekt úvěr se vytvoří při každém spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="63c1a-134">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="63c1a-135">V praxi úrokové sazby změnit pravidelně, ale nemusí nutně prokázat pokaždé, když je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="63c1a-135">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="63c1a-136">Serializace kódu znamená, že zachovat nejnovější úrokové sazby mezi instancemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="63c1a-136">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="63c1a-137">V dalším kroku můžete se přesně k tomu přidáním serializace k třídě úvěr.</span><span class="sxs-lookup"><span data-stu-id="63c1a-137">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="63c1a-138">Pomocí serializace k uchování objektu</span><span class="sxs-lookup"><span data-stu-id="63c1a-138">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="63c1a-139">Chcete-li zachovat hodnoty pro třídy úvěr, je nejprve třeba označit třídu pomocí `Serializable` atribut.</span><span class="sxs-lookup"><span data-stu-id="63c1a-139">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="63c1a-140">Přidejte následující kód výše úvěr definici třídy:</span><span class="sxs-lookup"><span data-stu-id="63c1a-140">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="63c1a-141"><xref:System.SerializableAttribute> Říká kompilátoru, že všechno ve třídě, můžete nastavit jako trvalý, do souboru.</span><span class="sxs-lookup"><span data-stu-id="63c1a-141">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="63c1a-142">Protože `PropertyChanged` událostí nepředstavuje součástí grafu objekt, který by měla být uložena, nesmí být serializován.</span><span class="sxs-lookup"><span data-stu-id="63c1a-142">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="63c1a-143">Díky tomu by serializovat všechny objekty, které jsou připojené k této události.</span><span class="sxs-lookup"><span data-stu-id="63c1a-143">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="63c1a-144">Můžete přidat <xref:System.NonSerializedAttribute> k deklaraci pole pro `PropertyChanged` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="63c1a-144">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="63c1a-145">Počínaje 7.3 C#, můžete připojit atributy základní pole použití automaticky implementované vlastnosti `field` cílovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="63c1a-145">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="63c1a-146">Přidá následující kód `TimeLastLoaded` vlastnost a označí je jako nelze serializovat:</span><span class="sxs-lookup"><span data-stu-id="63c1a-146">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="63c1a-147">Dalším krokem je přidejte do aplikace LoanApp kód serializace.</span><span class="sxs-lookup"><span data-stu-id="63c1a-147">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="63c1a-148">K serializaci třídy a zapisovat do souboru, můžete použít <xref:System.IO> a <xref:System.Runtime.Serialization.Formatters.Binary> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="63c1a-148">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="63c1a-149">Se pokud chcete vyhnout, zadejte plně kvalifikované názvy, můžete přidat odkazy na nezbytné obory názvů, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="63c1a-149">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

<span data-ttu-id="63c1a-150">Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="63c1a-150">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="63c1a-151">Konstanta přidejte do třídy pro název souboru serializovaná data, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="63c1a-151">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

<span data-ttu-id="63c1a-152">Dál přidejte následující kód po řádek, který vytvoří `TestLoan` objektu:</span><span class="sxs-lookup"><span data-stu-id="63c1a-152">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

<span data-ttu-id="63c1a-153">Nejdřív musíte zkontrolovat, zda soubor existuje.</span><span class="sxs-lookup"><span data-stu-id="63c1a-153">You first must check that the file exists.</span></span> <span data-ttu-id="63c1a-154">Pokud existuje, vytvoření <xref:System.IO.Stream> třídy číst binární soubor a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třída přeložit soubor.</span><span class="sxs-lookup"><span data-stu-id="63c1a-154">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="63c1a-155">Také musíte převést na typ objektu úvěr typ datového proudu.</span><span class="sxs-lookup"><span data-stu-id="63c1a-155">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="63c1a-156">Dále je nutné přidat kód pro serializaci třídy do souboru.</span><span class="sxs-lookup"><span data-stu-id="63c1a-156">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="63c1a-157">Přidejte následující kód po existující kód v `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="63c1a-157">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

<span data-ttu-id="63c1a-158">V tomto okamžiku můžete znovu sestavit a spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="63c1a-158">At this point, you can again build and run the application.</span></span> <span data-ttu-id="63c1a-159">Při prvním spuštění, Všimněte si, že začíná na 7.5 úrokové sazby a poté změní na 7.1.</span><span class="sxs-lookup"><span data-stu-id="63c1a-159">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="63c1a-160">Zavřete aplikaci a znovu jej spusťte.</span><span class="sxs-lookup"><span data-stu-id="63c1a-160">Close the application and then run it again.</span></span> <span data-ttu-id="63c1a-161">Nyní aplikace zobrazí zpráva, že se má číst uložený soubor, a úrokovou sazbu je 7.1 ani před kód, který se změní.</span><span class="sxs-lookup"><span data-stu-id="63c1a-161">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="63c1a-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="63c1a-162">See also</span></span>

 [<span data-ttu-id="63c1a-163">Serializace (C# )</span><span class="sxs-lookup"><span data-stu-id="63c1a-163">Serialization (C# )</span></span>](index.md)  
 [<span data-ttu-id="63c1a-164">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="63c1a-164">C# Programming Guide</span></span>](../..//index.md)  
