---
title: 'Návod: Uchování objektu pomocí jazyka C#'
ms.date: 04/26/2018
ms.openlocfilehash: 85c447ae43086cc789338e77555b7400a523662a
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086074"
---
# <a name="walkthrough-persisting-an-object-using-c"></a>Návod: uchování objektu pomocí jazyka C# #

Serializace můžete použít k uchování dat objektu mezi instancemi, které vám umožní uložení hodnot a načíst je další čas, který je vytvořena instance objektu.

V tomto návodu vytvoříte základní `Loan` objektu a zachovat data do souboru. Když znovu vytvoříte objekt se budou ze souboru načítat data.

> [!IMPORTANT]
> Tento příklad vytvoří nový soubor, pokud soubor již neexistuje. Pokud aplikace musí vytvořit soubor, musí mít tuto aplikaci `Create` oprávnění pro složku. Oprávnění jsou nastavená pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění, nižší oprávnění. Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze `Read` oprávnění do jednoho souboru (místo vytvořit oprávnění pro složku). Navíc je bezpečnější zapsat data do uživatelské složky než do kořenové složky nebo ve složce Program Files.

> [!IMPORTANT]
> V tomto příkladu ukládá data v binárním formátu souboru. Tyto formáty by neměla používat pro citlivá data, jako jsou hesla nebo informace o platební kartě.

## <a name="prerequisites"></a>Požadavky

* Sestavte a spusťte, nainstalujte [.NET Core SDK](https://www.microsoft.com/net/core).

* Pokud jste tak dosud neučinili, nainstalujte váš oblíbený editor kódu.

> [!TIP]
> Je potřeba nainstalovat editor kódu? Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!

* V příkladu vyžaduje C# 7.3. Zobrazit [vyberte verzi jazyka C#](../../../language-reference/configure-language-version.md) 

Můžete prozkoumat ukázkový kód online [v úložišti GitHub s ukázkami .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).

## <a name="creating-the-loan-object"></a>Vytvoření objektu půjčky

Prvním krokem je vytvoření `Loan` třídy a Konzolová aplikace, která používá třídu:

1. Vytvořte novou aplikaci. Typ `dotnet new console -o serialization` vytvořte novou konzolovou aplikaci v podadresáři s názvem `serialization`.
1. Otevřete aplikaci ve svém editoru a přidejte novou třídu s názvem `Loan.cs`.
1. Přidejte následující kód, který vaše `Loan` třídy:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

Budete také muset vytvořit aplikaci, která se používá `Loan` třídy.

## <a name="serialize-the-loan-object"></a>Serializace objektu půjčky

1. Otevřít `Program.cs`. Přidejte následující kód:

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

Přidat obslužnou rutinu události pro `PropertyChanged` událost a několik řádků změnit `Loan` objektu a zobrazte změny. Můžete zobrazit dodatky v následujícím kódu:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

V tomto okamžiku můžete spuštění kódu a zobrazit aktuální výstup:

```console
New customer value: Henry Clay
7.5
7.1
```

Spuštění této aplikace opakovaně vždy zapíše stejné hodnoty. Pokaždé, když program spustíte, je vytvořen nový objekt půjčky. V praxi úrokové sazby změnit pravidelně, ale ne nutně pokaždé, když je aplikace spuštěna. Serializační kód znamená, že zachovat nejnovější úrokové sazby mezi instancemi aplikace. V dalším kroku se přesně to provést přidáním serializace do třídy půjčky.

## <a name="using-serialization-to-persist-the-object"></a>Pomocí serializace k uchování objektu

Aby bylo možné zachovat hodnoty pro třídu půjček, musíte nejprve označte třídu `Serializable` atribut. Přidejte následující kód, výše půjčky definice třídy:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<xref:System.SerializableAttribute> Sděluje kompilátoru, že všechno, co ve třídě, můžete nastavit jako trvalý, do souboru. Vzhledem k tomu, `PropertyChanged` události nepředstavuje součástí graf objektu, který by měla být uložena, nesmí být serializován. Mohlo by serializaci všechny objekty, které jsou připojené k této události. Můžete přidat <xref:System.NonSerializedAttribute> deklarace pole pro `PropertyChanged` obslužné rutiny události.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

Od verze C# 7.3, můžete připojit atributy na pomocné pole automaticky implementované vlastnosti pomocí `field` cílovou hodnotu. Následující kód přidává `TimeLastLoaded` vlastnost a označí je jako nelze serializovat:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

Dalším krokem je přidání Serializační kód do aplikace LoanApp. Aby bylo možné serializovat třídu a zápis do souboru, je použít <xref:System.IO> a <xref:System.Runtime.Serialization.Formatters.Binary> obory názvů. Abyste nemuseli zadávat plně kvalifikované názvy, můžete přidat odkazy na obory názvů nezbytné, jak je znázorněno v následujícím kódu:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu. Přidejte konstanty do třídy pro název souboru serializovaná data, jak je znázorněno v následujícím kódu:

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

V dalším kroku přidejte následující kód po řádek, který vytvoří `TestLoan` objektu:

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

Nejdřív musíte zkontrolovat, zda soubor existuje. Pokud existuje, vytvořit <xref:System.IO.Stream> třídy ke čtení binárního souboru a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třídy pro převod souboru. Také je potřeba převést z typu datový proud na typ objektu půjčky.

Dále je nutné přidat kód k serializaci třídy do souboru. Přidejte následující kód za existující kód ve třídě `Main` metody:

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

V tomto okamžiku můžete znovu sestavte a spusťte aplikaci. Při prvním spuštění, Všimněte si, že začíná 7.5 úrokové sazby a poté změní na 7.1. Ukončete aplikaci a znovu jej spusťte. Teď se aplikace zobrazí zprávu, aby četl uloženého souboru a úrokové sazby 7.1 ještě před kód, který změní.

## <a name="see-also"></a>Viz také

- [Serializace (C#)](index.md)  
- [Průvodce programováním v jazyce C#](../..//index.md)  
