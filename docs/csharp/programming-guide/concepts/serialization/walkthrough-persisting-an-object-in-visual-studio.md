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
# <a name="walkthrough-persisting-an-object-using-c"></a>Návod: uchování objektu pomocí jazyka C# #

Serializace můžete použít k uchování dat objektu mezi instance, které umožňuje ukládat hodnoty a je načtou při příštím vytvoření instance objektu.

V tomto návodu vytvoříte základní `Loan` objektu a zachovat data do souboru. Když znovu vytvoříte objekt se budou ze souboru načítat data.

> [!IMPORTANT]
> Tento příklad vytvoří nový soubor, pokud soubor již neexistuje. Pokud aplikace musí vytvořit soubor, musí mít tuto aplikaci `Create` oprávnění pro složku. Oprávnění jsou nastavená pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění, nižší úrovní oprávnění. Pokud je to možné, je bezpečnější k vytvoření tohoto souboru během nasazení a udělit pouze `Read` oprávnění do jednoho souboru (a nikoli vytvořit oprávnění pro složku). Navíc je bezpečnější zapsat data do složek uživatele než do kořenové složky nebo ve složce Program Files.

> [!IMPORTANT]
> Tento příklad ukládá data v binárním formátu souboru. Tyto formáty by nemělo být použito pro citlivých dat, třeba hesla nebo informace o kreditní kartě.

## <a name="prerequisites"></a>Požadavky

* Sestavení a spuštění, nainstalujte [.NET Core SDK](https://www.microsoft.com/net/core).

* Pokud jste to ještě neudělali, nainstalujte editor vaše oblíbené kódu.

> [!TIP]
> Je potřeba nainstalovat editor kódu? Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!

Můžete zkontrolovat ukázkový kód online [v úložišti GitHub ukázky rozhraní .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).

## <a name="creating-the-loan-object"></a>Vytvoření objektu úvěr

Prvním krokem je vytvoření `Loan` třídy a konzolovou aplikaci, která používá třídu:

1. Vytvoření nové aplikace. Typ `dotnet new console -o serialization` k vytvoření nové aplikace konzoly v podadresáři s názvem `serialization`.
1. Otevřete aplikaci ve svém editoru a přidejte novou třídu s názvem `Loan.cs`.
1. Přidejte následující kód do vaší `Loan` třídy:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

Budete také muset vytvořit aplikaci, která používá `Loan` třídy.

## <a name="serialize-the-loan-object"></a>Serializaci objektu úvěr

1. Otevřete `Program.cs`. Přidejte následující kód:

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

Přidání obslužné rutiny události pro `PropertyChanged` událostí a zadání několika řádků změnit `Loan` objektu a zobrazit změny. Zobrazí se dodatky v následujícím kódu:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

V tomto okamžiku můžete spustit kód a zobrazit aktuální výstup:

```console
New customer value: Henry Clay
7.5
7.1
```

Spuštění této aplikace opakovaně vždy zapíše stejné hodnoty. Nový objekt úvěr se vytvoří při každém spuštění programu. V praxi úrokové sazby změnit pravidelně, ale nemusí nutně prokázat pokaždé, když je aplikace spuštěna. Serializace kódu znamená, že zachovat nejnovější úrokové sazby mezi instancemi aplikace. V dalším kroku můžete se přesně k tomu přidáním serializace k třídě úvěr.

## <a name="using-serialization-to-persist-the-object"></a>Pomocí serializace k uchování objektu

Chcete-li zachovat hodnoty pro třídy úvěr, je nejprve třeba označit třídu pomocí `Serializable` atribut. Přidejte následující kód výše úvěr definici třídy:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<xref:System.SerializableAttribute> Říká kompilátoru, že všechno ve třídě, můžete nastavit jako trvalý, do souboru. Protože `PropertyChanged` událostí nepředstavuje součástí grafu objekt, který by měla být uložena, nesmí být serializován. Díky tomu by serializovat všechny objekty, které jsou připojené k této události. Můžete přidat <xref:System.NonSerializedAttribute> k deklaraci pole pro `PropertyChanged` obslužné rutiny události.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

Počínaje 7.3 C#, můžete připojit atributy základní pole použití automaticky implementované vlastnosti `field` cílovou hodnotu. Přidá následující kód `TimeLastLoaded` vlastnost a označí je jako nelze serializovat:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

Dalším krokem je přidejte do aplikace LoanApp kód serializace. K serializaci třídy a zapisovat do souboru, můžete použít <xref:System.IO> a <xref:System.Runtime.Serialization.Formatters.Binary> obory názvů. Se pokud chcete vyhnout, zadejte plně kvalifikované názvy, můžete přidat odkazy na nezbytné obory názvů, jak je znázorněno v následujícím kódu:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu. Konstanta přidejte do třídy pro název souboru serializovaná data, jak je znázorněno v následujícím kódu:

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

Dál přidejte následující kód po řádek, který vytvoří `TestLoan` objektu:

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

Nejdřív musíte zkontrolovat, zda soubor existuje. Pokud existuje, vytvoření <xref:System.IO.Stream> třídy číst binární soubor a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třída přeložit soubor. Také musíte převést na typ objektu úvěr typ datového proudu.

Dále je nutné přidat kód pro serializaci třídy do souboru. Přidejte následující kód po existující kód v `Main` metoda:

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

V tomto okamžiku můžete znovu sestavit a spustit aplikaci. Při prvním spuštění, Všimněte si, že začíná na 7.5 úrokové sazby a poté změní na 7.1. Zavřete aplikaci a znovu jej spusťte. Nyní aplikace zobrazí zpráva, že se má číst uložený soubor, a úrokovou sazbu je 7.1 ani před kód, který se změní.

## <a name="see-also"></a>Viz také

 [Serializace (C# )](index.md)  
 [Průvodce programováním v jazyce C#](../..//index.md)  
