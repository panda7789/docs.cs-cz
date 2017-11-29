---
title: "Návod: Generování typů F# ze souboru schématu EDMX (F#)"
description: "Informace o vytvoření typů F # pro data reprezentované podle Data modelu Entity (EDM) v F # 3.0, kde je v souboru EDMX zadané schéma."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 5c59911f5f880493080ef1838bc015045ce4336a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a>Návod: Generování typů F# ze souboru schématu EDMX

> [!NOTE]
Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.  V tématu [FSharp.Data](http://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.

> [!NOTE]
Rozhraní API referenčních odkazů se dostanete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Tento návod pro jazyk F# 3.0 popisuje způsob vytváření typů pro data reprezentovaná modelem Entity Data Model (EDM), jehož schéma je zadáno v souboru .edmx. Tento návod znázorňuje také způsob používání poskytovatele typu EdmxFile. Než začnete, zvažte, zda není vhodnější poskytovatel typu SqlEntityConnection. Poskytovatel typu SqlEntityConnection funguje nejlépe v situacích, kdy je k dispozici online databáze, ke které se lze připojit během vývojové fáze projektu, a nevadí vám zadávání připojovacího řetězce v době kompilace. Tento poskytovatel typu je však omezen tím, že neposkytuje tolik funkcí databáze jako poskytovatel typu EdmxFile. Dále platí, že pokud pro projekt databáze, který používá model Entity Data Model, nemáte připojení k online databázi, můžete pro kód databáze použít soubor .edmx. Pokud použijete poskytovatele typu EdmxFile, kompilátor jazyka F# spustí program EdmGen.exe a vygeneruje poskytované typy.

Tento návod znázorňuje následující úkoly, které je nutné z důvodu správné funkčnosti provést v tomto pořadí:


- Vytvoření souboru EDMX
<br />

- Vytvoření projektu
<br />

- Hledání nebo vytváření entity data model připojovací řetězec
<br />

- Konfigurace poskytovatele typu
<br />

- Dotazování na data
<br />

- Volání uložené procedury
<br />


## <a name="prerequisites"></a>Požadavky

## <a name="creating-an-edmx-file"></a>Vytvoření souboru EDMX
Pokud již máte soubor EDMX, můžete tento krok přeskočit.


#### <a name="to-create-an-edmx-file"></a>Postup vytvoření souboru EDMX

- Pokud již nemáte souboru EDMX, můžete postupovat podle pokynů na konci tohoto názorného postupu v kroku [konfiguraci datového modelu Entity](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).
<br />

## <a name="creating-the-project"></a>Vytvoření projektu
V tomto kroku vytvoříte projekt a přidáte do něj příslušné odkazy, které jsou vyžadovány pro používání poskytovatele typu EDMX.


#### <a name="to-create-and-set-up-an-f-project"></a>Postup vytvoření a nastavení projektu jazyka F#

1. Ukončete předchozí projekt, vytvořte nový projekt a zadejte název SchoolEDM.
<br />

2. V **Průzkumníku řešení**, otevřete místní nabídku pro **odkazy**a potom zvolte **přidat odkaz na**.
<br />

3. V **sestavení** oblasti, vyberte **Framework** uzlu.
<br />

4. V seznamu dostupných sestavení, vyberte **System.Data.Entity** a **System.Data.Linq** sestavení a potom zvolte **přidat** tlačítko přidáte odkazy na tyto sestavení do projektu.
<br />

5. V **sestavení** oblasti, vyberte **rozšíření** uzlu.
<br />

6. V seznamu dostupných rozšíření přidejte odkaz na sestavení FSharp.Data.TypeProviders.
<br />

7. Otevřete příslušné obory názvů přidáním následujícího kódu.
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a>Vyhledání nebo vytvoření připojovacího řetězce pro model Entity Data Model
Připojovací řetězec modelu Entity Data Model (připojovací řetězec EDMX) zahrnuje nejen připojovací řetězec poskytovatele databáze, ale také další informace. Například připojovací řetězec EDMX pro jednotlivou databázi SQL Server připomíná následující kód.

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

Další informace o připojovacích řetězcích EDMX najdete v tématu [připojovací řetězce](https://msdn.microsoft.com/library/ms254494.aspx).


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a>Postup vyhledání nebo vytvoření připojovacího řetězce modelu Entity Data Model

1. Ruční generování připojovacích řetězců EDMX může být obtížné. Programovým generováním ušetříte čas. Pokud již připojovací řetězec EDMX znáte, můžete tento krok přeskočit a použít tento řetězec v následujícím kroku. Pokud řetězec neznáte, použijte následující kód pro vygenerování připojovacího řetězce EDMX z poskytovaného připojovacího řetězce databáze.
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a>Konfigurace poskytovatele typu
V tomto kroku vytvoříte a nakonfigurujete poskytovatele typu s připojovacím řetězcem EDMX a vygenerujete typy schématu, které je definováno v souboru .edmx.


#### <a name="to-configure-the-type-provider-and-generate-types"></a>Postup konfigurace poskytovatele typu a generování typů

1. Zkopírujte soubor .edmx vygenerovaný v prvním kroku tohoto návodu do složky projektu.
<br />

2. Zvolte otevřete místní nabídce uzlu projektu v projektu F # **přidat existující položku**a potom zvolte soubor EDMX ho přidejte do projektu.
<br />

3. Aktivujte poskytovatele typu pro soubor .edmx zadáním následujícího kódu. Nahraďte *Server*\*Instance * s názvem serveru, který používá SQL Server a název instance a použít název souboru EDMX z první krok v tomto průvodci.
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a>Dotazování na data
V tomto kroku použijete výrazy dotazů jazyka F# pro zadávání dotazů na databázi.


#### <a name="to-query-the-data"></a>Postup dotazování na data

- Chcete-li zadat dotaz na data v modelu Entity Data Model, použijte následující kód.
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a>Volání uložené procedury
Uložené procedury lze volat pomocí poskytovatele typu EDMX. V následujícím postupu školní databáze obsahuje uložené procedury, **UpdatePerson**, jaké aktualizace se záznam dané nové hodnoty pro sloupce. Tuto uloženou proceduru můžete použít, protože je vystavena jako metoda v typu DataContext.


#### <a name="to-call-a-stored-procedure"></a>Postup volání uložené procedury

- Aktualizujte záznamy přidáním následujícího kódu.
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

V případě úspěchu je výsledek 1. Všimněte si, že **exactlyOne** se používá ve výrazu dotazu k zajištění, že pouze jeden výsledek vrácený; jinak hodnota, je vyvolána výjimka. Navíc pokud chcete snadno pracovat s hodnotami Null, můžete použít jednoduchý **s možnou hodnotou Null** funkce, která je definována v tento kód vytvořit hodnotu Null mimo obyčejnou hodnotu.

<br />

## <a name="configuring-the-entity-data-model"></a>Konfigurace modelu Entity Data Model
Tento postup byste měli dokončit pouze v případě, že chcete vědět, jak lze vygenerovat úplný model Entity Data Model z databáze, není-li k dispozici databáze pro testování.


#### <a name="to-configure-the-entity-data-model"></a>Postup konfigurace modelu Entity Data Model

1. Na řádku nabídek zvolte **SQL**, **editoru jazyka Transact-SQL**, **nový dotaz** k vytvoření databáze. Budete-li k tomu vyzváni, zadejte server a instanci databáze.
<br />

2. Zkopírujte a vložte obsah skriptu databáze, který vytvoří databázi studenty, jak je popsáno v [dokumentaci k rozhraní Entity Framework](http://msdn.microsoft.com/data/JJ614587.aspx) v datovém centru pro vývojáře.
<br />

3. Výběr tlačítka panelu nástrojů symbolem trojúhelníček nebo výběrem položky klíče kombinace kláves Ctrl + Q spusťte skript SQL.
<br />

4. V **Průzkumníka serveru**, otevřete místní nabídku pro **připojení dat**, zvolte **přidat připojení**a potom zadejte název databázového serveru, název název instance a školní databáze.
<br />

5. Vytvoření projektu jazyka C# nebo Visual Basic konzolovou aplikaci, otevřete jeho místní nabídky, zvolte **přidat novou položku**a potom zvolte **ADO.NET Entity Data Model**.
<br />  Spustí se Průvodce datovým modelem entity. Pomocí tohoto průvodce můžete zvolit způsob vytvoření datového modelu entity.
<br />

6. V části **zvolte obsah modelu**, vyberte **generování z databáze** zaškrtávací políčko.
<br />

7. Na další stránce vyberte jako datové připojení nově vytvořenou databázi School.
<br />  Toto připojení by měla vypadat přibližně  **&lt;servername&gt;.&lt; INSTANCENAME&gt;. School.dbo**.
<br />

8. Zkopírujte připojovací řetězec entity do schránky, protože tento řetězec můžete později potřebovat.
<br />

9. Ujistěte se, zaškrtněte políčko pro uložení připojovací řetězec entity k **App.Config** je vybrán soubor a poznamenejte si hodnotu řetězce do textového pole, které by vám pomůžou najít připojovací řetězec později, v případě potřeby.
<br />

10. Na další stránce, zvolte **tabulky** a **uložené procedury a funkce**.
<br />  Pokud vyberete tyto uzly nejvyšší úrovně, zvolíte také všechny tabulky, uložené procedury a funkce. V případě potřeby je můžete zvolit také jednotlivě.
<br />

11. Ověřte, zda jste zvolili zaškrtávací políčka i pro ostatní nastavení.
<br />  První **množně nebo singularizovat generované názvy objektů** políčko označuje, zda se ke změně singulární forms množném čísle tak, aby odpovídaly názvů v názvy objektů, které představují databázových tabulek. **Zahrnout do modelu sloupce cizích klíčů** políčko určuje, zda pro zahrnutí polí, jejichž účelem je připojení k další pole v typy objektů, které jsou generovány pro schéma databáze. Třetí zaškrtávací políčko určuje, zda mají být do modelu zahrnuty uložené procedury a funkce.
<br />

12. Vyberte **Dokončit** pro vygenerování souboru .edmx, který obsahuje datový Model Entity, založený na databázi školy.
<br />  Soubor, **Model1.edmx**, se přidá do projektu, a zobrazí se diagramu databáze.
<br />

13. Na řádku nabídek zvolte **zobrazení**, **ostatní okna**, **Entity Data Model prohlížeče** zobrazíte všechny podrobnosti modelu nebo **podrobnosti mapování Entity Data Model**  otevřete okno, které ukazuje, jak mapuje generovaného objektový model do databáze tabulky a sloupce.
<br />


## <a name="next-steps"></a>Další kroky
Prozkoumejte jiné dotazy prohlížením operátory k dispozici dotazu uvedené v [výrazy dotazů](../../language-reference/query-expressions.md).


## <a name="see-also"></a>Viz také
[Zprostředkovatelé typů](index.md)

[Edmxfile – zprostředkovatel typu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů a entit](accessing-a-sql-database-entities.md)

[Entity Framework](http://msdn.microsoft.com/data/ef)

[Přehled souboru EDMX](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[Generátor EDM &#40; EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)

