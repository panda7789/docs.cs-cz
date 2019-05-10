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
ms.openlocfilehash: 91520b8967445a70a7775b99faef0cefc5e01cc2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654408"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Návod: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock
Knihovna TPL datového toku poskytuje <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> třídy tak, aby se zobrazí a uložit do vyrovnávací paměti dat z jednoho nebo více zdrojů a poté je šířit data ve vyrovnávací paměti jako jednu kolekci. Tento mechanismus dávkování je užitečný při shromažďování dat z jednoho nebo více zdrojů a následném zpracování více datových prvků v dávce. Zvažte například aplikaci, která používá tok dat pro vkládání záznamů do databáze. Tato operace může být efektivnější, pokud je vloženo více položek současně místo postupně sekvenčně. Tento dokument popisuje způsob použití <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> operací vložení třídy ke zvýšení účinnosti takových databáze. Také popisuje způsob použití <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídy pro zachycení výsledků i všech výjimek, ke kterým dochází, když program čte z databáze.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Požadavky  
  
1. Přečtěte si části propojit bloky v [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokument před zahájením tohoto návodu.  
  
2. Ujistěte se, že máte kopii databáze Northwind, Northwind.sdf, dostupný na vašem počítači. Tento soubor je obvykle umístěn ve složce % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.  
  
    > [!IMPORTANT]
    >  V některých verzích Windows se nelze připojit k Northwind.sdf Pokud Visual Studio běží v režimu bez oprávnění správce. Pokud chcete připojit k Northwind.sdf, spusťte Visual Studio nebo příkazový řádek vývojáře pro sadu Visual Studio v **spustit jako správce** režimu.  
  
 Tento návod obsahuje následující části:  
  
- [Vytvoření konzolové aplikace](#creating)  
  
- [Definování třídy zaměstnanců](#employeeClass)  
  
- [Definování operací databáze zaměstnanců](#operations)  
  
- [Přidání dat zaměstnance do databáze bez použití ukládání do vyrovnávací paměti](#nonBuffering)  
  
- [Použití ukládání do vyrovnávací paměti k přidání dat zaměstnance do databáze](#buffering)  
  
- [Použití spojení ve vyrovnávací paměti pro čtení dat zaměstnanců z databáze](#bufferedJoin)  
  
- [Kompletní příklad](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>Vytvoření konzolové aplikace  
  
<a name="consoleApp"></a>   
1. V sadě Visual Studio, vytvořit Visual C# nebo Visual Basic **konzolovou aplikaci** projektu. V tomto dokumentu má projekt název `DataflowBatchDatabase`.  
  
2. Ve vašem projektu přidejte odkaz na System.Data.SqlServerCe.dll a odkaz na System.Threading.Tasks.Dataflow.dll.  
  
3. Ujistěte se, že Form1.cs (Form1.vb pro jazyk Visual Basic) obsahuje následující `using` (`Imports` v jazyce Visual Basic) příkazy.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4. Přidejte následující datové členy do `Program` třídy.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>Definování třídy zaměstnanců  
 Přidat `Program` třídy `Employee` třídy.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 `Employee` Třída obsahuje tři vlastnosti `EmployeeID`, `LastName`, a `FirstName`. Tyto vlastnosti odpovídají `Employee ID`, `Last Name`, a `First Name` sloupců `Employees` tabulky v databázi Northwind. Pro tuto ukázku `Employee` také definuje třídu `Random` metodu, která vytvoří `Employee` objektu s náhodnými hodnotami vlastností.  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>Definování operací databáze zaměstnanců  
 Přidat `Program` třídy `InsertEmployees`, `GetEmployeeCount`, a `GetEmployeeID` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 `InsertEmployees` Metoda přidá nové záznamy zaměstnanců do databáze. `GetEmployeeCount` Metoda zjišťuje počet položek v `Employees` tabulky. `GetEmployeeID` Metoda načte identifikátor prvního zaměstnance, který má zadaný název. Každá z těchto metod má připojovací řetězec k databázi Northwind a používá funkce v `System.Data.SqlServerCe` obor názvů pro komunikaci s databází.  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Přidání dat zaměstnance do databáze bez použití ukládání do vyrovnávací paměti  
 Přidat `Program` třídy `AddEmployees` a `PostRandomEmployees` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 `AddEmployees` Metoda přidává náhodná data zaměstnanců do databáze pomocí datového toku. Vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který volá `InsertEmployees` metoda pro přidání položky zaměstnance do databáze. `AddEmployees` Pak zavolá metodu `PostRandomEmployees` metodu ke zveřejnění více `Employee` objektů <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu. `AddEmployees` Metoda pak čeká na dokončení všech operací vložení.  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Použití ukládání do vyrovnávací paměti k přidání dat zaměstnance do databáze  
 Přidat `Program` třídy `AddEmployeesBatched` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 Tento způsob se podobá `AddEmployees`, s tím rozdílem, že používá také <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídy do vyrovnávací paměti více `Employee` objekty před odesláním těchto objektů do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu. Protože <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídy šíří více prvků jako kolekci, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu je upravit tak, aby mohly reagovat na celou řadu `Employee` objekty. Stejně jako v `AddEmployees` metody `AddEmployeesBatched` volání `PostRandomEmployees` metodu ke zveřejnění více `Employee` objekty; však `AddEmployeesBatched` zveřejní tyto objekty do <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu. `AddEmployeesBatched` Metoda také čeká na dokončení všech operací vložení.  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Použití spojení ve vyrovnávací paměti pro čtení dat zaměstnanců z databáze  
 Přidat `Program` třídy `GetRandomEmployees` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 Tato metoda vytiskne informace o náhodných zaměstnancích do konzoly. Vytvoří několik náhodných `Employee` a volá `GetEmployeeID` metodu pro načtení jedinečného identifikátoru pro každý objekt. Protože `GetEmployeeID` metoda vyvolá výjimku, pokud neexistuje žádný odpovídající zaměstnanec s danou jména a příjmení `GetRandomEmployees` metoda používá <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu pro ukládání `Employee` objekty pro úspěšné volání `GetEmployeeID` a <xref:System.Exception?displayProperty=nameWithType> objekty pro volání, která selžou. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt v tomto příkladu zpracovává <xref:System.Tuple%602> objekt, který obsahuje seznam `Employee` objekty a seznam <xref:System.Exception> objekty. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Objekt rozšíří tato data ven při součet přijatého `Employee` a <xref:System.Exception> objekt rovná velikosti dávky.  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód. `Main` Metoda porovnává čas, který se vyžaduje k provedení dávkového vložení do databáze čas k provedení nedávkového vložení do jiné databáze. Ukazuje také použití spojení ve vyrovnávací paměti pro čtení dat zaměstnanců z databáze a také informuje o chybách.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
