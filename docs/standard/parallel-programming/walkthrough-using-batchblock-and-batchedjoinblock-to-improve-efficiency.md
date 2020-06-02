---
title: 'Návod: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
ms.openlocfilehash: e572c5a14958ccc069ae7649af8c8ed4eb967dc1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284582"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Návod: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock

Knihovna rozhraní TPL Dataflow poskytuje <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> třídy a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> , aby bylo možné přijímat data a ukládat je do vyrovnávací paměti z jednoho nebo více zdrojů a následně šířit tato data do vyrovnávací paměti jako jednu kolekci. Tento mechanismus dávkování je užitečný při shromažďování dat z jednoho nebo více zdrojů a následném zpracování více datových prvků jako dávky. Představte si například aplikaci, která používá tok k vkládání záznamů do databáze. Tato operace může být efektivnější, pokud je vloženo více položek současně namísto jednoho intervalu. Tento dokument popisuje, jak použít <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídu ke zlepšení efektivity těchto operací vložení databáze. Popisuje také, jak použít <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu k zachycení výsledků a všech výjimek, ke kterým dojde, když program čte z databáze.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Požadavky

1. Než začnete tento návod, přečtěte si část bloky spojení v dokumentu [toku](dataflow-task-parallel-library.md) dat.

2. Ujistěte se, že máte kopii databáze Northwind, Northwind. SDF, která je k dispozici ve vašem počítači. Tento soubor je obvykle umístěn ve složce% Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples \\ .

    > [!IMPORTANT]
    > V některých verzích systému Windows se nelze připojit k databázi Northwind. SDF, pokud je aplikace Visual Studio spuštěna v režimu bez oprávnění správce. Pokud se chcete připojit k Northwind. SDF, spusťte aplikaci Visual Studio nebo Developer Command Prompt pro Visual Studio v režimu **Spustit jako správce** .

Tento návod obsahuje následující oddíly:

- [Vytvoření konzolové aplikace](#creating)

- [Definování třídy Employee](#employeeClass)

- [Definování operací databáze zaměstnanců](#operations)

- [Přidání dat zaměstnanců do databáze bez použití ukládání do vyrovnávací paměti](#nonBuffering)

- [Přidání dat zaměstnanců do databáze pomocí ukládání do vyrovnávací paměti](#buffering)

- [Čtení dat zaměstnanců z databáze pomocí připojení do vyrovnávací paměti](#bufferedJoin)

- [Kompletní příklad](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a>Vytvoření konzolové aplikace

1. V aplikaci Visual Studio vytvořte projekt **konzolové aplikace** Visual C# nebo Visual Basic. V tomto dokumentu se projekt jmenuje `DataflowBatchDatabase` .

2. V projektu přidejte odkaz na System. data. SqlServerCe. dll a odkaz na System. Threading. Tasks. Dataflow. dll.

3. Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje `using` následující `Imports` příkazy (v Visual Basic).

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Přidejte do třídy následující datové členy `Program` .

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Definování třídy Employee

Přidejte do `Program` třídy třídu `Employee` .

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

`Employee`Třída obsahuje tři vlastnosti,, `EmployeeID` `LastName` a `FirstName` . Tyto vlastnosti odpovídají `Employee ID` `Last Name` `First Name` sloupcům, a v `Employees` tabulce databáze Northwind. Pro tuto ukázku `Employee` Třída také definuje `Random` metodu, která vytvoří `Employee` objekt, který má náhodné hodnoty pro jeho vlastnosti.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Definování operací databáze zaměstnanců

Přidejte do `Program` třídy `InsertEmployees` `GetEmployeeCount` metody, a `GetEmployeeID` .

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

`InsertEmployees`Metoda přidá do databáze nové záznamy o zaměstnancích. `GetEmployeeCount`Metoda načte počet položek v `Employees` tabulce. `GetEmployeeID`Metoda načte identifikátor prvního zaměstnance, který má zadaný název. Každá z těchto metod vezme připojovací řetězec k databázi Northwind a používá funkce v `System.Data.SqlServerCe` oboru názvů ke komunikaci s databází.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Přidání dat zaměstnanců do databáze bez použití ukládání do vyrovnávací paměti

Přidejte do `Program` třídy `AddEmployees` `PostRandomEmployees` metody a.

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

`AddEmployees`Metoda přidá náhodná data zaměstnanců do databáze pomocí toku dat. Vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který volá `InsertEmployees` metodu pro přidání záznamu zaměstnance do databáze. `AddEmployees`Metoda pak zavolá `PostRandomEmployees` metodu pro odeslání více `Employee` objektů do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu. `AddEmployees`Metoda pak počká na dokončení všech operací vložení.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Přidání dat zaměstnanců do databáze pomocí ukládání do vyrovnávací paměti

Přidejte do `Program` třídy `AddEmployeesBatched` metodu.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Tato metoda se podobá `AddEmployees` , s tím rozdílem, že také používá <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídu k ukládání více objektů do vyrovnávací paměti `Employee` předtím, než je pošle tyto objekty <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu. Vzhledem k tomu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> , že třída šíří více prvků jako kolekci, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt je upraven tak, aby fungoval na poli `Employee` objektů. Stejně jako v `AddEmployees` metodě `AddEmployeesBatched` volá `PostRandomEmployees` metodu pro odeslání více `Employee` objektů; `AddEmployeesBatched` tyto objekty však tyto objekty odešle do <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu. `AddEmployeesBatched`Metoda také čeká na dokončení všech operací vložení.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Čtení dat zaměstnanců z databáze pomocí připojení do vyrovnávací paměti

Přidejte do `Program` třídy `GetRandomEmployees` metodu.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Tato metoda vytiskne informace o náhodných zaměstnancích do konzoly. Vytvoří několik náhodných `Employee` objektů a zavolá `GetEmployeeID` metodu pro načtení jedinečného identifikátoru pro každý objekt. Vzhledem k tomu, že `GetEmployeeID` metoda vyvolá výjimku, pokud neexistuje žádný odpovídající zaměstnanec s danými křestními a posledními názvy, `GetRandomEmployees` Metoda používá <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu k ukládání `Employee` objektů pro úspěšná volání `GetEmployeeID` a <xref:System.Exception?displayProperty=nameWithType> objekty pro volání, která selžou. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>Objekt v tomto příkladu funguje na <xref:System.Tuple%602> objektu, který obsahuje seznam `Employee` objektů a seznam <xref:System.Exception> objektů. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>Objekt šíří tato data v případě, že součet přijatých hodnot `Employee` a <xref:System.Exception> počtu objektů se rovná velikosti dávky.

<a name="complete"></a>

## <a name="the-complete-example"></a>Kompletní příklad

Následující příklad ukazuje úplný kód. `Main`Metoda porovnává dobu potřebnou k provedení vkládání dávkových databází oproti době provádění nedávkových vkládání databází. Ukazuje také použití spojení ve vyrovnávací paměti pro čtení dat zaměstnanců z databáze a také hlášení chyb.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Viz také

- [Tok dat](dataflow-task-parallel-library.md)
