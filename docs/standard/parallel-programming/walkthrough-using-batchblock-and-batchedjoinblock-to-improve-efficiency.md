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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bcd12d5c3cfe341b22a5421930a22c272878006b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591843"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Postupy: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock
Knihovna toku dat TPL poskytuje <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> třídy, aby mohli přijímat a vyrovnávací paměť dat z jednoho nebo více zdrojů a potom rozšíří na tato data ve vyrovnávací paměti jako jedna kolekce. Tento mechanismus dávkování je užitečné, když shromažďovat data z jednoho nebo více zdrojů a potom zpracovat více datové prvky, jako dávku. Představte si třeba aplikaci, která používá toku dat vložení záznamů do databáze. Tato operace může být efektivnější, pokud jsou ve stejnou dobu namísto postupně postupně vkládána více položek. Tento dokument popisuje postup použití <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> operace vložení třída zlepšit efektivitu takovou databázi. Také popisuje způsob použití <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třída zaznamenat výsledky a všechny výjimky, které dojít, když program načte z databáze.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Požadavky  
  
1.  Najdete v části připojení bloky [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokumentu před spuštěním tohoto průvodce.  
  
2.  Ujistěte se, že máte kopii databáze Northwind, Northwind.sdf v počítači k dispozici. Tento soubor se obvykle nachází ve složce % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.  
  
    > [!IMPORTANT]
    >  V některých verzích systému Windows nemůže připojit k Northwind.sdf Pokud Visual Studio je spuštěna v režimu bez oprávnění správce. Připojit k Northwind.sdf, spusťte Visual Studio nebo příkazového řádku v sadě Visual Studio **spustit jako správce** režimu.  
  
 Tento názorný postup obsahuje následující části:  
  
-   [Vytvoření konzolové aplikace](#creating)  
  
-   [Definování zaměstnanec – třída](#employeeClass)  
  
-   [Definování zaměstnanec databázových operací](#operations)  
  
-   [Přidání dat zaměstnanců k databázi bez použití ukládání do vyrovnávací paměti](#nonBuffering)  
  
-   [Chcete-li přidat Data zaměstnanců k databázi pomocí ukládání do vyrovnávací paměti](#buffering)  
  
-   [Použití ve vyrovnávací paměti připojení číst zaměstnanec Data z databáze](#bufferedJoin)  
  
-   [Úplný příklad](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>Vytvoření konzolové aplikace  
  
<a name="consoleApp"></a>   
1.  V sadě Visual Studio vytvořit Visual C# nebo Visual Basic **konzolové aplikace** projektu. V tomto dokumentu je projekt s názvem `DataflowBatchDatabase`.  
  
2.  Ve vašem projektu přidejte odkaz na System.Data.SqlServerCe.dll a odkaz na System.Threading.Tasks.Dataflow.dll.  
  
3.  Ujistěte se, že Form1.cs (Form1.vb jazyka Visual Basic) obsahuje následující `using` (`Imports` v jazyce Visual Basic) příkazy.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  Přidejte následující členy dat tak, aby `Program` třídy.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>Definování zaměstnanec – třída  
 Přidejte do `Program` – třída `Employee` třídy.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 `Employee` Třída obsahuje tři vlastnosti `EmployeeID`, `LastName`, a `FirstName`. Tyto vlastnosti odpovídají `Employee ID`, `Last Name`, a `First Name` sloupců v `Employees` tabulky v databázi Northwind. Pro tento ukázkový `Employee` třída definuje také `Random` metodu, která vytvoří `Employee` objekt, který má náhodných hodnot vlastností.  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>Definování zaměstnanec databázových operací  
 Přidejte do `Program` – třída `InsertEmployees`, `GetEmployeeCount`, a `GetEmployeeID` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 `InsertEmployees` Metoda přidá nové záznamy zaměstnanců k databázi. `GetEmployeeCount` Metoda načte počet položek v `Employees` tabulky. `GetEmployeeID` Metoda načte identifikátor první zaměstnanec, který má zadaný název. Každá z těchto metod přebírá připojovací řetězec k databázi Northwind a používá funkce v `System.Data.SqlServerCe` obor názvů pro komunikaci s databází.  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Přidání dat zaměstnanců k databázi bez použití ukládání do vyrovnávací paměti  
 Přidejte do `Program` – třída `AddEmployees` a `PostRandomEmployees` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 `AddEmployees` Metoda pomocí toku dat přidá náhodných zaměstnanec data do databáze. Vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který volá `InsertEmployees` metody přidat položku zaměstnanců k databázi. `AddEmployees` Metoda pak zavolá `PostRandomEmployees` metodu ke zveřejnění více `Employee` objekty ke <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu. `AddEmployees` Metoda potom počká, než pro všechny operace ukončíte vložení.  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Chcete-li přidat Data zaměstnanců k databázi pomocí ukládání do vyrovnávací paměti  
 Přidejte do `Program` – třída `AddEmployeesBatched` metoda.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 Tato metoda se podobá `AddEmployees`kromě toho, že používá také <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídy mají do vyrovnávací paměti více `Employee` objekty před odesláním těchto objektů do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu. Protože <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třída šíří se víc elementů jako kolekce, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt je upraven tak, aby fungoval na pole `Employee` objekty. Jako v `AddEmployees` metody `AddEmployeesBatched` volání `PostRandomEmployees` metodu ke zveřejnění více `Employee` objekty; však `AddEmployeesBatched` odešle tyto objekty <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu. `AddEmployeesBatched` Metoda čeká také pro všechny operace ukončíte vložení.  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Použití ve vyrovnávací paměti připojení číst zaměstnanec Data z databáze  
 Přidejte do `Program` – třída `GetRandomEmployees` metoda.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 Tato metoda zobrazí informace o náhodné zaměstnanci ke konzole. Vytvoří několik náhodných `Employee` objekty a volání `GetEmployeeID` metoda pro načtení jedinečný identifikátor pro každý objekt. Protože `GetEmployeeID` metoda vyvolá výjimku, pokud neexistuje žádný odpovídající zaměstnanec s danou první a poslední názvy `GetRandomEmployees` metoda používá <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu pro ukládání `Employee` objekty pro úspěšné volání `GetEmployeeID` a <xref:System.Exception?displayProperty=nameWithType> objekty pro volání, které nesplní. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt v tomto příkladu funguje na <xref:System.Tuple%602> objekt, který obsahuje seznam `Employee` objekty a seznam <xref:System.Exception> objekty. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Objekt šíří se tato data při součet přijatého `Employee` a <xref:System.Exception> počty objekt rovná velikost dávky.  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kód dokončení. `Main` Metoda srovnává čas, který je potřeba provést vložení dávkové databáze a čas k vložení databáze není v dávce. Také ukazuje použití ve vyrovnávací paměti připojení ke čtení zaměstnanec dat z databáze a také zprávy o chybách.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>Viz také  
 [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
