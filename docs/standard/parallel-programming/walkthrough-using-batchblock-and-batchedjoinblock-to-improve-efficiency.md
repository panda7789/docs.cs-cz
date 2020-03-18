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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091363"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Postupy: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock

Knihovna toku dat <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> TPL poskytuje a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> třídy, takže můžete přijímat a ukládání dat do vyrovnávací paměti z jednoho nebo více zdrojů a potom šířit data ve vyrovnávací paměti jako jednu kolekci. Tento mechanismus dávkování je užitečné při shromažďování dat z jednoho nebo více zdrojů a potom zpracovat více datových prvků jako dávka. Zvažte například aplikaci, která používá tok dat k vložení záznamů do databáze. Tato operace může být efektivnější, pokud více položek jsou vloženy současně namísto jednoho po druhém postupně. Tento dokument popisuje, jak <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> použít třídu ke zlepšení efektivity těchto operací vkládání databáze. Popisuje také, jak použít <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu k zachycení výsledků a všech výjimek, ke kterým dochází při čtení programu z databáze.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Požadavky

1. Než začnete s tímto návodem, přečtěte si oddíl Bloky spojení v dokumentu [Tok dat.](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

2. Ujistěte se, že máte v počítači k dispozici kopii databáze Northwind, Northwind.sdf. Tento soubor je obvykle umístěn ve složce %Program Files%\Microsoft SQL Server\\Compact Edition\v3.5\Samples .

    > [!IMPORTANT]
    > V některých verzích systému Windows se nelze připojit k souboru Northwind.sdf, pokud je sada Visual Studio spuštěna v režimu bez oprávnění správce. Chcete-li se připojit k souboru Northwind.sdf, spusťte visual studio nebo příkazový řádek pro vývojáře pro Visual Studio v režimu **Spustit jako správce.**

Tento návod obsahuje následující části:

- [Vytvoření konzolové aplikace](#creating)

- [Definování třídy zaměstnanců](#employeeClass)

- [Definování operací databáze zaměstnanců](#operations)

- [Přidání dat zaměstnance do databáze bez použití ukládání do vyrovnávací paměti](#nonBuffering)

- [Použití ukládání do vyrovnávací paměti k přidání dat zaměstnance do databáze](#buffering)

- [Použití spojení ve vyrovnávací paměti ke čtení dat zaměstnanců z databáze](#bufferedJoin)

- [Kompletní příklad](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a>Vytvoření konzolové aplikace

1. V sadě Visual Studio vytvořte projekt aplikace Visual C# nebo Visual Basic **Console.** V tomto dokumentu je `DataflowBatchDatabase`projekt pojmenován .

2. V projektu přidejte odkaz na soubor System.Data.SqlServerCe.dll a odkaz na soubor System.Threading.Tasks.Dataflow.dll.

3. Ujistěte se, že Form1.cs (Form1.vb `using` `Imports` pro visual basic) obsahuje následující příkazy ( v jazyce Visual Basic).

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Přidejte následující datové `Program` členy do třídy.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Definování třídy zaměstnanců

Přidejte `Program` do `Employee` třídy třídy.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

Třída `Employee` obsahuje tři `EmployeeID`vlastnosti , `LastName`, a `FirstName`. Tyto vlastnosti `Employee ID`odpovídají `Last Name`, `First Name` a `Employees` sloupce v tabulce v databázi Northwind. Pro tuto demonstraci `Employee` třída také `Random` definuje metodu, která vytvoří `Employee` objekt, který má náhodné hodnoty pro své vlastnosti.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Definování operací databáze zaměstnanců

Přidejte `Program` do `InsertEmployees`třídy `GetEmployeeCount` `GetEmployeeID` , a metody.

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

Metoda `InsertEmployees` přidá do databáze nové záznamy zaměstnanců. Metoda `GetEmployeeCount` načte počet položek v `Employees` tabulce. Metoda `GetEmployeeID` načte identifikátor prvního zaměstnance, který má zadaný název. Každá z těchto metod přebírá připojovací řetězec do `System.Data.SqlServerCe` databáze Northwind a používá funkce v oboru názvů ke komunikaci s databází.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Přidání dat zaměstnance do databáze bez použití ukládání do vyrovnávací paměti

Přidejte `Program` do `AddEmployees` třídy a `PostRandomEmployees` metody.

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

Metoda `AddEmployees` přidá do databáze náhodná data zaměstnanců pomocí toku dat. Vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který `InsertEmployees` volá metodu přidat položku zaměstnance do databáze. Metoda `AddEmployees` pak volá `PostRandomEmployees` metodu `Employee` zaúčtovat <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> více objektů do objektu. Metoda `AddEmployees` pak čeká na dokončení všech operací vložení.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Použití ukládání do vyrovnávací paměti k přidání dat zaměstnance do databáze

Přidejte `Program` do `AddEmployeesBatched` třídy metodu.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Tato metoda `AddEmployees`se podobá , s <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> tím rozdílem, že také používá třídu do vyrovnávací paměti více `Employee` objektů před odesláním těchto objektů do objektu. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Vzhledem <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> k tomu, že třída šíří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> více prvků jako kolekce, `Employee` objekt je upraven tak, aby působit na pole objektů. Stejně `AddEmployees` jako `AddEmployeesBatched` v `PostRandomEmployees` metodě volá `Employee` metodu zaúčtovat více objektů; však `AddEmployeesBatched` odešle tyto <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekty do objektu. Metoda `AddEmployeesBatched` také čeká na dokončení všech operací vložení.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Použití spojení ve vyrovnávací paměti ke čtení dat zaměstnanců z databáze

Přidejte `Program` do `GetRandomEmployees` třídy metodu.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Tato metoda vytiskne informace o náhodných zaměstnanců do konzoly. Vytvoří několik `Employee` náhodných objektů `GetEmployeeID` a zavolá metodu k načtení jedinečného identifikátoru pro každý objekt. Vzhledem `GetEmployeeID` k tomu, že metoda vyvolá výjimku, pokud neexistuje `GetRandomEmployees` žádný odpovídající <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> zaměstnanec `Employee` s daným `GetEmployeeID` křestním jménem a příjmení, metoda používá třídu k ukládání objektů pro úspěšná volání a <xref:System.Exception?displayProperty=nameWithType> objekty pro volání, které se nezdaří. Objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> v tomto příkladu <xref:System.Tuple%602> působí na objekt, který obsahuje seznam `Employee` objektů a seznam <xref:System.Exception> objektů. Objekt <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> rozšíří tato data, když se součet přijatých `Employee` a <xref:System.Exception> objektů počítá velikost dávky.

<a name="complete"></a>

## <a name="the-complete-example"></a>Kompletní příklad

Následující příklad ukazuje úplný kód. Metoda `Main` porovnává čas, který je nutný k provedení dávkových vložení databáze oproti době provádění nedávkových vložení databáze. Také ukazuje použití spojení ve vyrovnávací paměti ke čtení dat zaměstnanců z databáze a také sestavy chyb.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
