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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d704702e74b5f7d4a315bd14a467296245f90257
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046490"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Návod: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock

Knihovna rozhraní <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> TPL Dataflow poskytuje třídy a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> , aby bylo možné přijímat data a ukládat je do vyrovnávací paměti z jednoho nebo více zdrojů a následně šířit tato data do vyrovnávací paměti jako jednu kolekci. Tento mechanismus dávkování je užitečný při shromažďování dat z jednoho nebo více zdrojů a následném zpracování více datových prvků jako dávky. Představte si například aplikaci, která používá tok k vkládání záznamů do databáze. Tato operace může být efektivnější, pokud je vloženo více položek současně namísto jednoho intervalu. Tento dokument popisuje, jak použít <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídu ke zlepšení efektivity těchto operací vložení databáze. Popisuje také, jak použít <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu k zachycení výsledků a všech výjimek, ke kterým dojde, když program čte z databáze.

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

<a name="consoleApp"></a>
1. V aplikaci Visual Studio vytvořte projekt konzolové C# **aplikace** pro Visual nebo Visual Basic. V tomto dokumentu se projekt jmenuje `DataflowBatchDatabase`.

2. V projektu přidejte odkaz na System. data. SqlServerCe. dll a odkaz na System. Threading. Tasks. Dataflow. dll.

3. Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje `using` následující`Imports` příkazy (v Visual Basic).

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Přidejte do `Program` třídy následující datové členy.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Definování třídy Employee

Přidejte do `Program` `Employee` třídy třídu.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

Třída obsahuje tři vlastnosti `EmployeeID` `FirstName`,, a. `LastName` `Employee` Tyto vlastnosti odpovídají `Employee ID`sloupcům, `Last Name`a `First Name` v `Employees` tabulce databáze Northwind. Pro tuto ukázku `Employee` třída také `Random` definuje `Employee` metodu, která vytvoří objekt, který má náhodné hodnoty pro jeho vlastnosti.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Definování operací databáze zaměstnanců

Přidejte do `Program` `GetEmployeeCount`třídy metody `InsertEmployees`, a `GetEmployeeID` .

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

`InsertEmployees` Metoda přidá do databáze nové záznamy o zaměstnancích. Metoda načte počet položek `Employees` v tabulce. `GetEmployeeCount` `GetEmployeeID` Metoda načte identifikátor prvního zaměstnance, který má zadaný název. Každá z těchto metod vezme připojovací řetězec k databázi Northwind a používá funkce v `System.Data.SqlServerCe` oboru názvů ke komunikaci s databází.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Přidání dat zaměstnanců do databáze bez použití ukládání do vyrovnávací paměti

Přidejte do `Program` `AddEmployees` třídy metody a. `PostRandomEmployees`

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

`AddEmployees` Metoda přidá náhodná data zaměstnanců do databáze pomocí toku dat. Vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který `InsertEmployees` volá metodu pro přidání záznamu zaměstnance do databáze. Metoda pak zavolá `Employee` metodu pro odeslání více objektů do objektu.<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> `PostRandomEmployees` `AddEmployees` `AddEmployees` Metoda pak počká na dokončení všech operací vložení.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Přidání dat zaměstnanců do databáze pomocí ukládání do vyrovnávací paměti

Přidejte do `Program` `AddEmployeesBatched` třídy metodu.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Tato metoda `AddEmployees`se podobá, s tím rozdílem, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> že také používá třídu `Employee` k ukládání více <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektů do vyrovnávací paměti předtím, než je pošle tyto objekty objektu. Vzhledem k tomu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> , že `Employee` Třídašířívíceprvkůjakokolekci,objektjeupraventak,abyfungoval<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> na poli objektů. Stejně jako v `AddEmployees` `AddEmployeesBatched` metodě volá `PostRandomEmployees` metodupro`Employee` odeslání více objektů; tyto objekty však tyto objekty <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>odešledo objektu. `AddEmployeesBatched` `AddEmployeesBatched` Metoda také čeká na dokončení všech operací vložení.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Čtení dat zaměstnanců z databáze pomocí připojení do vyrovnávací paměti

Přidejte do `Program` `GetRandomEmployees` třídy metodu.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Tato metoda vytiskne informace o náhodných zaměstnancích do konzoly. Vytvoří několik náhodných `Employee` objektů a `GetEmployeeID` zavolá metodu pro načtení jedinečného identifikátoru pro každý objekt. `Employee` `GetRandomEmployees` <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Vzhledem k tomu, že `GetEmployeeID` metoda vyvolá výjimku, pokud neexistuje žádný shodný zaměstnanec s danými křestními a posledními názvy, metoda používá třídu k ukládání objektů pro úspěšná volání do a `GetEmployeeID` <xref:System.Exception?displayProperty=nameWithType> objekty pro volání, která selžou. Objekt v tomto příkladu funguje <xref:System.Tuple%602> na objektu `Employee` , který obsahuje seznam objektů a seznam <xref:System.Exception> objektů. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt šíří tato data v případě, že součet přijatých `Employee` hodnot a <xref:System.Exception> počtu objektů se rovná velikosti dávky. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>

<a name="complete"></a>

## <a name="the-complete-example"></a>Kompletní příklad

Následující příklad ukazuje úplný kód. `Main` Metoda porovnává dobu potřebnou k provedení vkládání dávkových databází oproti době provádění nedávkových vkládání databází. Ukazuje také použití spojení ve vyrovnávací paměti pro čtení dat zaměstnanců z databáze a také hlášení chyb.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
