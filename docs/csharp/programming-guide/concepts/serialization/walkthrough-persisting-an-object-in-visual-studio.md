---
title: 'Návod: uchování objektu pomocí jazyka C #'
ms.date: 04/26/2018
ms.openlocfilehash: bbe239008629d687084af7e28a75fa68560ca0ab
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796064"
---
# <a name="walkthrough-persisting-an-object-using-c"></a>Návod: uchování objektu pomocí jazyka C\#

Můžete použít serializaci k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načíst je při příštím vytvoření instance objektu.

V tomto návodu vytvoříte základní `Loan` objekt a zachová jeho data do souboru. Po opětovném vytvoření objektu načtěte data ze souboru.

> [!IMPORTANT]
> Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje. Pokud aplikace musí vytvořit soubor, musí mít `Create` Tato aplikace oprávnění pro tuto složku. Oprávnění se nastavují pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění a menší oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` oprávnění pouze k jednomu souboru (místo oprávnění k vytvoření složky). Je také bezpečnější zapsat data do složek uživatele než do kořenové složky nebo do složky Program Files.

> [!IMPORTANT]
> Tento příklad ukládá data v binárním souboru formátu. Tyto formáty by se neměly používat pro citlivá data, jako jsou hesla nebo informace o kreditních kartách.

## <a name="prerequisites"></a>Požadavky

- Pro sestavení a spuštění nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download).

- Pokud jste to ještě neudělali, nainstalujte svůj oblíbený editor kódu.

> [!TIP]
> Potřebujete nainstalovat editor kódu? Vyzkoušejte [Visual Studio](https://visualstudio.com/downloads)!

- Příklad vyžaduje C# 7,3. Viz [Výběr verze jazyka C#](../../../language-reference/configure-language-version.md) .

Ukázkový kód si můžete prohlédnout online [v úložišti GitHub Samples .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).

## <a name="creating-the-loan-object"></a>Vytvoření objektu výpůjčky

Prvním krokem je vytvoření `Loan` třídy a konzolové aplikace, která používá třídu:

1. Vytvořte novou aplikaci. Zadejte `dotnet new console -o serialization` , chcete-li vytvořit novou konzolovou aplikaci v podadresáři s názvem `serialization`.
1. Otevřete aplikaci v editoru a přidejte novou třídu s názvem `Loan.cs`.
1. Do `Loan` třídy přidejte následující kód:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

Také budete muset vytvořit aplikaci, která používá `Loan` třídu.

## <a name="serialize-the-loan-object"></a>Serializace objektu výpůjčky

1. Otevřete `Program.cs`. Přidejte následující kód:

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

Přidejte obslužnou rutinu události pro `PropertyChanged` událost a několik řádků pro úpravu `Loan` objektu a zobrazte změny. Můžete zobrazit Přidání v následujícím kódu:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

V tomto okamžiku můžete spustit kód a zobrazit aktuální výstup:

```console
New customer value: Henry Clay
7.5
7.1
```

Spuštění této aplikace opakovaně vždy zapisuje stejné hodnoty. Nový objekt výpůjčky se vytvoří pokaždé, když spustíte program. V reálném světě se úrokové sazby pravidelně mění, ale nemusí nutně pokaždé, když je aplikace spuštěná. Serializační kód znamená, že zachováte nejnovější úrokovou sazbu mezi instancemi aplikace. V dalším kroku provedete to tak, že do třídy výpůjčky přidáte serializaci.

## <a name="using-serialization-to-persist-the-object"></a>Zachování objektu pomocí serializace

Aby bylo možné zachovat hodnoty pro třídu výpůjčky, musíte nejprve označit třídu `Serializable` atributem. Do definice třídy výpůjčky přidejte následující kód:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

Rozhraní <xref:System.SerializableAttribute> instruuje kompilátor, že všechno ve třídě lze trvale uložit do souboru. Vzhledem k `PropertyChanged` tomu, že událost nepředstavuje součást grafu objektů, která by měla být uložena, neměla by být serializována. Tím by došlo k serializaci všech objektů, které jsou k této události připojeny. Můžete přidat <xref:System.NonSerializedAttribute> do deklarace pole pro obslužnou rutinu `PropertyChanged` události.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

Počínaje jazykem C# 7,3 můžete přiřadit atributy k poli pro zálohování s automaticky implementovanou vlastností pomocí `field` cílové hodnoty. Následující kód přidá `TimeLastLoaded` vlastnost a označí ji jako neserializovatelný:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

Dalším krokem je přidání kódu serializace do aplikace LoanApp. Aby bylo možné serializovat třídu a zapsat ji do souboru, použijte obory názvů <xref:System.IO> a. <xref:System.Runtime.Serialization.Formatters.Binary> Chcete-li se vyhnout psaní plně kvalifikovaných názvů, můžete přidat odkazy na nezbytné obory názvů, jak je znázorněno v následujícím kódu:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu. Do třídy přidejte konstantu pro název souboru serializovaných dat, jak je znázorněno v následujícím kódu:

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

Dále přidejte následující kód za řádek, který vytvoří `TestLoan` objekt:

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

Nejdřív musíte ověřit, že soubor existuje. Pokud existuje, vytvořte <xref:System.IO.Stream> třídu pro čtení binárního souboru a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třídu pro překlad souboru. Také je nutné převést typ datového proudu na typ objektu výpůjčky.

Dále je nutné přidat kód k serializaci třídy do souboru. Za existující kód v `Main` metodě přidejte následující kód:

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

V tuto chvíli můžete znovu sestavit a spustit aplikaci. Při prvním spuštění si všimněte, že úrokové sazby začínají na 7,5 a pak se změní na 7,1. Ukončete aplikaci a pak ji znovu spusťte. Nyní aplikace vytiskne zprávu, že si uložil uložený soubor, a úrokovou sazbu je 7,1 ještě před kódem, který ho změnil.

## <a name="see-also"></a>Viz také

- [Serializace (C#)](index.md)
- [Průvodce programováním v C#](../../index.md)
