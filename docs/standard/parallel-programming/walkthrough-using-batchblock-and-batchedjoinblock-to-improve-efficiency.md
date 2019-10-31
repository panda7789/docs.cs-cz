---
title: 'Postupy: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
ms.openlocfilehash: 4b2b6a6124bf8cc0fb3b379607135283678e3268
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091363"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Postupy: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock

Knihovna Dataflow v TPL poskytuje třídy <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType>, abyste mohli přijímat data a ukládat je do vyrovnávací paměti z jednoho nebo více zdrojů a potom šířit tato data do vyrovnávací paměti jako jednu kolekci. Tento mechanismus dávkování je užitečný při shromažďování dat z jednoho nebo více zdrojů a následném zpracování více datových prvků jako dávky. Představte si například aplikaci, která používá tok k vkládání záznamů do databáze. Tato operace může být efektivnější, pokud je vloženo více položek současně namísto jednoho intervalu. Tento dokument popisuje, jak použít třídu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> ke zlepšení efektivity těchto operací vložení databáze. Popisuje také, jak použít třídu <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> k zachycení výsledků a všech výjimek, ke kterým dojde, když program čte z databáze.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Požadavky

1. Než začnete tento návod, přečtěte si část bloky spojení v dokumentu [toku](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dat.

2. Ujistěte se, že máte kopii databáze Northwind, Northwind. SDF, která je k dispozici ve vašem počítači. Tento soubor je obvykle umístěn ve složce% Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.

    > [!IMPORTANT]
    > V některých verzích systému Windows se nelze připojit k databázi Northwind. SDF, pokud je aplikace Visual Studio spuštěna v režimu bez oprávnění správce. Pokud se chcete připojit k Northwind. SDF, spusťte aplikaci Visual Studio nebo Developer Command Prompt pro Visual Studio v režimu **Spustit jako správce** .

Tento návod obsahuje následující oddíly:

- [Vytvoření konzolové aplikace](#creating)

- [Definování třídy Employee](#employeeClass)

- [Definování operací databáze zaměstnanců](#operations)

- [Přidání dat zaměstnanců do databáze bez použití ukládání do vyrovnávací paměti](#nonBuffering)

- [Přidání dat zaměstnanců do databáze pomocí ukládání do vyrovnávací paměti](#buffering)

- [Čtení dat zaměstnanců z databáze pomocí připojení do vyrovnávací paměti](#bufferedJoin)

- [Úplný příklad](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a>Vytvoření konzolové aplikace

1. V aplikaci Visual Studio vytvořte projekt C# **konzolové aplikace** pro Visual nebo Visual Basic. V tomto dokumentu má projekt název `DataflowBatchDatabase`.

2. V projektu přidejte odkaz na System. data. SqlServerCe. dll a odkaz na System. Threading. Tasks. Dataflow. dll.

3. Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje následující příkazy `using` (`Imports` v Visual Basic).

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Do třídy `Program` přidejte následující datové členy.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Definování třídy Employee

Do třídy `Program` přidejte třídu `Employee`.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

Třída `Employee` obsahuje tři vlastnosti, `EmployeeID`, `LastName`a `FirstName`. Tyto vlastnosti odpovídají sloupcům `Employee ID`, `Last Name`a `First Name` v tabulce `Employees` v databázi Northwind. Pro tuto ukázku třída `Employee` definuje také metodu `Random`, která vytvoří objekt `Employee`, který má náhodné hodnoty pro jeho vlastnosti.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Definování operací databáze zaměstnanců

Do `Program` třídy přidejte metody `InsertEmployees`, `GetEmployeeCount`a `GetEmployeeID`.

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

Metoda `InsertEmployees` přidá do databáze nové záznamy o zaměstnancích. Metoda `GetEmployeeCount` načítá počet položek v tabulce `Employees`. Metoda `GetEmployeeID` načte identifikátor prvního zaměstnance, který má zadaný název. Každá z těchto metod vezme připojovací řetězec k databázi Northwind a používá funkce v oboru názvů `System.Data.SqlServerCe` ke komunikaci s databází.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Přidání dat zaměstnanců do databáze bez použití ukládání do vyrovnávací paměti

Do `Program` třídy přidejte metody `AddEmployees` a `PostRandomEmployees`.

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

Metoda `AddEmployees` přidá náhodná data zaměstnanců do databáze pomocí toku dat. Vytvoří objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, který volá metodu `InsertEmployees` pro přidání záznamu zaměstnance do databáze. Metoda `AddEmployees` pak zavolá metodu `PostRandomEmployees` pro odeslání více objektů `Employee` do objektu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. Metoda `AddEmployees` pak počká na dokončení všech operací vložení.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Přidání dat zaměstnanců do databáze pomocí ukládání do vyrovnávací paměti

Do `Program` třídy přidejte metodu `AddEmployeesBatched`.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Tato metoda se podobá `AddEmployees`, s tím rozdílem, že používá také třídu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> k ukládání více objektů `Employee` do vyrovnávací paměti předtím, než je pošle objektům <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. Vzhledem k tomu, že třída <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> rozšířila více prvků jako kolekci, je objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> změněn tak, aby fungoval na poli objektů `Employee`. Stejně jako v metodě `AddEmployees` `AddEmployeesBatched` volá metodu `PostRandomEmployees` pro odeslání více objektů `Employee`; `AddEmployeesBatched` však tyto objekty přemístit do objektu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>. Metoda `AddEmployeesBatched` také čeká na dokončení všech operací vložení.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Čtení dat zaměstnanců z databáze pomocí připojení do vyrovnávací paměti

Do `Program` třídy přidejte metodu `GetRandomEmployees`.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Tato metoda vytiskne informace o náhodných zaměstnancích do konzoly. Vytvoří několik náhodných `Employee` objektů a zavolá metodu `GetEmployeeID` pro získání jedinečného identifikátoru pro každý objekt. Vzhledem k tomu, že metoda `GetEmployeeID` vyvolá výjimku, pokud neexistuje žádný odpovídající zaměstnanec s danými křestními a posledními jmény, metoda `GetRandomEmployees` používá třídu <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> k ukládání `Employee` objektů pro úspěšné volání `GetEmployeeID` a <xref:System.Exception?displayProperty=nameWithType> objektů pro volání, která selžou . Objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> v tomto příkladu funguje na objektu <xref:System.Tuple%602>, který obsahuje seznam `Employee` objektů a seznam objektů <xref:System.Exception>. Objekt <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> rozšíří tato data, když se součet přijatých objektů `Employee` a <xref:System.Exception> rovná velikosti dávky.

<a name="complete"></a>

## <a name="the-complete-example"></a>Kompletní příklad

Následující příklad ukazuje úplný kód. Metoda `Main` porovnává dobu potřebnou k provedení vkládání dávkových databází v době, kdy je potřeba provést nedávková vkládání databáze. Ukazuje také použití spojení ve vyrovnávací paměti pro čtení dat zaměstnanců z databáze a také hlášení chyb.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
