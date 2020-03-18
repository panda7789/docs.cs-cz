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
# <a name="walkthrough-persisting-an-object-using-c"></a>Návod: uchování objektu pomocí C\#

Serializace můžete použít k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načítat je při příštím vytvoření instance objektu.

V tomto návodu vytvoříte `Loan` základní objekt a zachováte jeho data do souboru. Potom načtete data ze souboru při opětovném vytvoření objektu.

> [!IMPORTANT]
> Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje. Pokud aplikace musí vytvořit soubor, musí `Create` mít oprávnění pro složku. Oprávnění jsou nastavena pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace `Write` potřebuje pouze oprávnění, menší oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor `Read` během nasazení a udělit oprávnění pouze k jednomu souboru (namísto vytvořit oprávnění pro složku). Také je bezpečnější zapisovat data do uživatelských složek než do kořenové složky nebo do složky Program Files.

> [!IMPORTANT]
> Tento příklad ukládá data v binárním formátu souboru. Tyto formáty by neměly být používány pro citlivá data, jako jsou hesla nebo informace o kreditní kartě.

## <a name="prerequisites"></a>Požadavky

- Chcete-li vytvořit a spustit, nainstalujte sadu [.NET Core SDK](https://dotnet.microsoft.com/download).

- Pokud jste tak ještě neučinili, nainstalujte si svůj oblíbený editor kódu.

> [!TIP]
> Potřebujete nainstalovat editor kódu? Vyzkoušejte [visual studio!](https://visualstudio.com/downloads)

- Příklad vyžaduje C# 7.3. Viz [Výběr jazykové verze jazyka C#](../../../language-reference/configure-language-version.md)

Ukázkový kód můžete zkontrolovat online [v úložišti .NET samples GitHub](https://github.com/dotnet/samples/tree/master/csharp/serialization).

## <a name="creating-the-loan-object"></a>Vytvoření objektu půjčky

Prvním krokem je vytvoření `Loan` třídy a konzolové aplikace, která používá třídu:

1. Vytvořte novou aplikaci. Chcete-li `dotnet new console -o serialization` vytvořit novou konzolovou aplikaci v podadresáři s názvem `serialization`.
1. Otevřete aplikaci v editoru a `Loan.cs`přidejte novou třídu s názvem .
1. Přidejte do třídy `Loan` následující kód:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

Budete také muset vytvořit aplikaci, `Loan` která používá třídu.

## <a name="serialize-the-loan-object"></a>Serializace objektu půjčky

1. Otevřete `Program.cs`. Přidejte následující kód:

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

Přidejte obslužnou rutinu `PropertyChanged` události pro `Loan` událost a několik řádků pro úpravu objektu a zobrazení změn. Můžete vidět dodatky v následujícím kódu:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

V tomto okamžiku můžete spustit kód a zobrazit aktuální výstup:

```console
New customer value: Henry Clay
7.5
7.1
```

Spuštění této aplikace opakovaně vždy zapíše stejné hodnoty. Při každém spuštění programu je vytvořen nový objekt Loan. V reálném světě se úrokové sazby pravidelně mění, ale ne nutně při každém spuštění aplikace. Serializační kód znamená zachování nejnovější úrokové sazby mezi instancemi aplikace. V dalším kroku provedete právě to přidáním serializace do třídy Loan.

## <a name="using-serialization-to-persist-the-object"></a>Použití serializace k zachování objektu

Chcete-li zachovat hodnoty pro loan třídy, musíte nejprve označit třídu atributem. `Serializable` Nad definici třídy Loan přidejte následující kód:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

Říká <xref:System.SerializableAttribute> kompilátoru, že vše ve třídě může být trvalé do souboru. Vzhledem `PropertyChanged` k tomu, že událost nepředstavuje část grafu objektu, který by měl být uložen, by neměl být serializován. Tím by serializovat všechny objekty, které jsou připojeny k této události. Můžete přidat <xref:System.NonSerializedAttribute> do deklarace pole `PropertyChanged` pro obslužnou rutinu události.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

Počínaje C# 7.3, můžete připojit atributy k záložnímu poli automaticky `field` implementované vlastnosti pomocí cílové hodnoty. Následující kód přidá `TimeLastLoaded` vlastnost a označí ji jako neserializovatelné:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

Dalším krokem je přidání serializačního kódu do aplikace LoanApp. Chcete-li třídu serializovat a zapsat do souboru, použijte obory názvů <xref:System.IO> a. <xref:System.Runtime.Serialization.Formatters.Binary> Chcete-li se vyhnout zadávání plně kvalifikovaných názvů, můžete přidat odkazy na nezbytné jmenné prostory, jak je znázorněno v následujícím kódu:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

Dalším krokem je přidání kódu pro rekonstrukci objektu ze souboru při vytvoření objektu. Přidejte konstantu do třídy pro název souboru serializovaných dat, jak je znázorněno v následujícím kódu:

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

Dále přidejte následující kód za řádek, který vytvoří `TestLoan` objekt:

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

Nejprve je nutné zkontrolovat, zda soubor existuje. Pokud existuje, vytvořte <xref:System.IO.Stream> třídu pro čtení <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> binárního souboru a třídu pro překlad souboru. Je také nutné převést z typu datového proudu na typ objektu Loan.

Dále je nutné přidat kód serializovat třídy do souboru. Přidejte následující kód za existující `Main` kód v metodě:

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

V tomto okamžiku můžete znovu sestavit a spustit aplikaci. Při prvním spuštění si všimněte, že úrokové sazby začínají na 7,5 a pak se změní na 7,1. Zavřete aplikaci a spusťte ji znovu. Nyní aplikace vytiskne zprávu, že si přečetl uložený soubor a úroková sazba je 7.1 ještě před kódem, který jej změní.

## <a name="see-also"></a>Viz také

- [Serializace (C#)](index.md)
- [Programovací příručka jazyka C#](../..//index.md)
