---
title: "Omezení schématu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c254865800694af8eb754c3e8d4072688fd7e89a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="schema-restrictions"></a><span data-ttu-id="af63a-102">Omezení schématu</span><span class="sxs-lookup"><span data-stu-id="af63a-102">Schema Restrictions</span></span>
<span data-ttu-id="af63a-103">Druhý parametr volitelný **GetSchema** je metoda vrátí omezení, které se používají k omezení množství informací o schématu, a je předán **GetSchema** metoda jako pole řetězců. .</span><span class="sxs-lookup"><span data-stu-id="af63a-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="af63a-104">Určuje pozici v poli hodnoty, které můžete předat a jde o ekvivalent číslo omezení.</span><span class="sxs-lookup"><span data-stu-id="af63a-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="af63a-105">Například následující tabulka popisuje omezení kolekcí schémat "Tabulky" pomocí zprostředkovatele dat .NET Framework pro SQL Server podporován.</span><span class="sxs-lookup"><span data-stu-id="af63a-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="af63a-106">Další omezení pro kolekce schématu systému SQL Server je uvedený na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="af63a-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="af63a-107">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-107">Restriction Name</span></span>|<span data-ttu-id="af63a-108">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-108">Parameter Name</span></span>|<span data-ttu-id="af63a-109">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-109">Restriction Default</span></span>|<span data-ttu-id="af63a-110">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-111">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-111">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-112">TABLE_CATALOG</span></span>|<span data-ttu-id="af63a-113">1</span><span class="sxs-lookup"><span data-stu-id="af63a-113">1</span></span>|  
|<span data-ttu-id="af63a-114">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-114">Owner</span></span>|@Owner|<span data-ttu-id="af63a-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="af63a-116">2</span><span class="sxs-lookup"><span data-stu-id="af63a-116">2</span></span>|  
|<span data-ttu-id="af63a-117">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-117">Table</span></span>|@Name|<span data-ttu-id="af63a-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-118">TABLE_NAME</span></span>|<span data-ttu-id="af63a-119">3</span><span class="sxs-lookup"><span data-stu-id="af63a-119">3</span></span>|  
|<span data-ttu-id="af63a-120">TableType</span><span class="sxs-lookup"><span data-stu-id="af63a-120">TableType</span></span>|@TableType|<span data-ttu-id="af63a-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="af63a-121">TABLE_TYPE</span></span>|<span data-ttu-id="af63a-122">4</span><span class="sxs-lookup"><span data-stu-id="af63a-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="af63a-123">Zadání hodnoty omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="af63a-124">Použít jednu z omezení kolekce schémat "Tabulky", stačí vytvořit pole řetězců se čtyřmi prvky a pak umístit hodnotu elementu, který odpovídá číslu omezení.</span><span class="sxs-lookup"><span data-stu-id="af63a-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="af63a-125">Například k omezení tabulky vrácený **GetSchema** metodu pouze ty tabulky ve schématu "Prodej", nastavte druhý prvkem pole na "Prodej" před předáním na **GetSchema** metoda.</span><span class="sxs-lookup"><span data-stu-id="af63a-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af63a-126">Omezení kolekce pro `SqlClient` a `OracleClient` mají další `ParameterName` sloupce.</span><span class="sxs-lookup"><span data-stu-id="af63a-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="af63a-127">Výchozí sloupec omezení je stále existuje pro zpětnou kompatibilitu, ale je aktuálně ignorována.</span><span class="sxs-lookup"><span data-stu-id="af63a-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="af63a-128">Parametrizované dotazy a nikoli náhradní řetězce se má použít k minimalizovat riziko útoku vkládání SQL při zadání hodnoty omezení.</span><span class="sxs-lookup"><span data-stu-id="af63a-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af63a-129">Počet prvků v poli musí být menší než nebo rovna počtu omezení, která jsou podporována pro jiný určené schéma kolekce <xref:System.ArgumentException> bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="af63a-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="af63a-130">Může být menší než maximální počet omezení.</span><span class="sxs-lookup"><span data-stu-id="af63a-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="af63a-131">Chybějící omezení se předpokládá, že mít hodnotu null (bez omezení).</span><span class="sxs-lookup"><span data-stu-id="af63a-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="af63a-132">Můžete zadat dotaz rozhraní .NET Framework spravovaného zprostředkovatele určit seznam podporovaných omezení voláním **GetSchema** metoda s názvem kolekce schémat omezení, což je "Omezení".</span><span class="sxs-lookup"><span data-stu-id="af63a-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="af63a-133">Tato možnost vrátí <xref:System.Data.DataTable> se seznamem názvů kolekcí, názvy omezení, výchozí hodnoty omezení a omezení čísla.</span><span class="sxs-lookup"><span data-stu-id="af63a-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="af63a-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="af63a-134">Example</span></span>  
 <span data-ttu-id="af63a-135">Následující příklady ukazují, jak používat <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metoda zprostředkovatele dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> třída načíst informace o schématu o všechny tabulky obsažené v **AdventureWorks**ukázkové databáze, a omezit informace vrátí pouze ty tabulky "Prodeje" schématu:</span><span class="sxs-lookup"><span data-stu-id="af63a-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="af63a-136">SQL Server schématu omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="af63a-137">V následujících tabulkách najdete omezení pro kolekce schématu systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="af63a-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="af63a-138">Uživatelé</span><span class="sxs-lookup"><span data-stu-id="af63a-138">Users</span></span>  
  
|<span data-ttu-id="af63a-139">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-139">Restriction Name</span></span>|<span data-ttu-id="af63a-140">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-140">Parameter Name</span></span>|<span data-ttu-id="af63a-141">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-141">Restriction Default</span></span>|<span data-ttu-id="af63a-142">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-143">Uživatelské_jméno</span><span class="sxs-lookup"><span data-stu-id="af63a-143">User_Name</span></span>|@Name|<span data-ttu-id="af63a-144">name</span><span class="sxs-lookup"><span data-stu-id="af63a-144">name</span></span>|<span data-ttu-id="af63a-145">1</span><span class="sxs-lookup"><span data-stu-id="af63a-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="af63a-146">Databáze</span><span class="sxs-lookup"><span data-stu-id="af63a-146">Databases</span></span>  
  
|<span data-ttu-id="af63a-147">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-147">Restriction Name</span></span>|<span data-ttu-id="af63a-148">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-148">Parameter Name</span></span>|<span data-ttu-id="af63a-149">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-149">Restriction Default</span></span>|<span data-ttu-id="af63a-150">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-151">Název</span><span class="sxs-lookup"><span data-stu-id="af63a-151">Name</span></span>|@Name|<span data-ttu-id="af63a-152">Název</span><span class="sxs-lookup"><span data-stu-id="af63a-152">Name</span></span>|<span data-ttu-id="af63a-153">1</span><span class="sxs-lookup"><span data-stu-id="af63a-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="af63a-154">Tabulky</span><span class="sxs-lookup"><span data-stu-id="af63a-154">Tables</span></span>  
  
|<span data-ttu-id="af63a-155">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-155">Restriction Name</span></span>|<span data-ttu-id="af63a-156">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-156">Parameter Name</span></span>|<span data-ttu-id="af63a-157">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-157">Restriction Default</span></span>|<span data-ttu-id="af63a-158">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-159">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-159">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-160">TABLE_CATALOG</span></span>|<span data-ttu-id="af63a-161">1</span><span class="sxs-lookup"><span data-stu-id="af63a-161">1</span></span>|  
|<span data-ttu-id="af63a-162">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-162">Owner</span></span>|@Owner|<span data-ttu-id="af63a-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="af63a-164">2</span><span class="sxs-lookup"><span data-stu-id="af63a-164">2</span></span>|  
|<span data-ttu-id="af63a-165">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-165">Table</span></span>|@Name|<span data-ttu-id="af63a-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-166">TABLE_NAME</span></span>|<span data-ttu-id="af63a-167">3</span><span class="sxs-lookup"><span data-stu-id="af63a-167">3</span></span>|  
|<span data-ttu-id="af63a-168">TableType</span><span class="sxs-lookup"><span data-stu-id="af63a-168">TableType</span></span>|@TableType|<span data-ttu-id="af63a-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="af63a-169">TABLE_TYPE</span></span>|<span data-ttu-id="af63a-170">4</span><span class="sxs-lookup"><span data-stu-id="af63a-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="af63a-171">Sloupce</span><span class="sxs-lookup"><span data-stu-id="af63a-171">Columns</span></span>  
  
|<span data-ttu-id="af63a-172">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-172">Restriction Name</span></span>|<span data-ttu-id="af63a-173">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-173">Parameter Name</span></span>|<span data-ttu-id="af63a-174">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-174">Restriction Default</span></span>|<span data-ttu-id="af63a-175">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-176">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-176">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-177">TABLE_CATALOG</span></span>|<span data-ttu-id="af63a-178">1</span><span class="sxs-lookup"><span data-stu-id="af63a-178">1</span></span>|  
|<span data-ttu-id="af63a-179">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-179">Owner</span></span>|@Owner|<span data-ttu-id="af63a-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="af63a-181">2</span><span class="sxs-lookup"><span data-stu-id="af63a-181">2</span></span>|  
|<span data-ttu-id="af63a-182">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-182">Table</span></span>|@Table|<span data-ttu-id="af63a-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-183">TABLE_NAME</span></span>|<span data-ttu-id="af63a-184">3</span><span class="sxs-lookup"><span data-stu-id="af63a-184">3</span></span>|  
|<span data-ttu-id="af63a-185">Sloupec</span><span class="sxs-lookup"><span data-stu-id="af63a-185">Column</span></span>|@Column|<span data-ttu-id="af63a-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-186">COLUMN_NAME</span></span>|<span data-ttu-id="af63a-187">4</span><span class="sxs-lookup"><span data-stu-id="af63a-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="af63a-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="af63a-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="af63a-189">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-189">Restriction Name</span></span>|<span data-ttu-id="af63a-190">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-190">Parameter Name</span></span>|<span data-ttu-id="af63a-191">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-191">Restriction Default</span></span>|<span data-ttu-id="af63a-192">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-193">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-193">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-194">TABLE_CATALOG</span></span>|<span data-ttu-id="af63a-195">1</span><span class="sxs-lookup"><span data-stu-id="af63a-195">1</span></span>|  
|<span data-ttu-id="af63a-196">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-196">Owner</span></span>|@Owner|<span data-ttu-id="af63a-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="af63a-198">2</span><span class="sxs-lookup"><span data-stu-id="af63a-198">2</span></span>|  
|<span data-ttu-id="af63a-199">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-199">Table</span></span>|@Table|<span data-ttu-id="af63a-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-200">TABLE_NAME</span></span>|<span data-ttu-id="af63a-201">3</span><span class="sxs-lookup"><span data-stu-id="af63a-201">3</span></span>|  
|<span data-ttu-id="af63a-202">Sloupec</span><span class="sxs-lookup"><span data-stu-id="af63a-202">Column</span></span>|@Column|<span data-ttu-id="af63a-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-203">COLUMN_NAME</span></span>|<span data-ttu-id="af63a-204">4</span><span class="sxs-lookup"><span data-stu-id="af63a-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="af63a-205">zobrazení</span><span class="sxs-lookup"><span data-stu-id="af63a-205">Views</span></span>  
  
|<span data-ttu-id="af63a-206">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-206">Restriction Name</span></span>|<span data-ttu-id="af63a-207">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-207">Parameter Name</span></span>|<span data-ttu-id="af63a-208">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-208">Restriction Default</span></span>|<span data-ttu-id="af63a-209">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-210">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-210">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-211">TABLE_CATALOG</span></span>|<span data-ttu-id="af63a-212">1</span><span class="sxs-lookup"><span data-stu-id="af63a-212">1</span></span>|  
|<span data-ttu-id="af63a-213">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-213">Owner</span></span>|@Owner|<span data-ttu-id="af63a-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="af63a-215">2</span><span class="sxs-lookup"><span data-stu-id="af63a-215">2</span></span>|  
|<span data-ttu-id="af63a-216">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-216">Table</span></span>|@Table|<span data-ttu-id="af63a-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-217">TABLE_NAME</span></span>|<span data-ttu-id="af63a-218">3</span><span class="sxs-lookup"><span data-stu-id="af63a-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="af63a-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="af63a-219">ViewColumns</span></span>  
  
|<span data-ttu-id="af63a-220">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-220">Restriction Name</span></span>|<span data-ttu-id="af63a-221">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-221">Parameter Name</span></span>|<span data-ttu-id="af63a-222">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-222">Restriction Default</span></span>|<span data-ttu-id="af63a-223">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-224">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-224">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-225">VIEW_CATALOG</span></span>|<span data-ttu-id="af63a-226">1</span><span class="sxs-lookup"><span data-stu-id="af63a-226">1</span></span>|  
|<span data-ttu-id="af63a-227">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-227">Owner</span></span>|@Owner|<span data-ttu-id="af63a-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="af63a-229">2</span><span class="sxs-lookup"><span data-stu-id="af63a-229">2</span></span>|  
|<span data-ttu-id="af63a-230">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-230">Table</span></span>|@Table|<span data-ttu-id="af63a-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-231">VIEW_NAME</span></span>|<span data-ttu-id="af63a-232">3</span><span class="sxs-lookup"><span data-stu-id="af63a-232">3</span></span>|  
|<span data-ttu-id="af63a-233">Sloupec</span><span class="sxs-lookup"><span data-stu-id="af63a-233">Column</span></span>|@Column|<span data-ttu-id="af63a-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-234">COLUMN_NAME</span></span>|<span data-ttu-id="af63a-235">4</span><span class="sxs-lookup"><span data-stu-id="af63a-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="af63a-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="af63a-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="af63a-237">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-237">Restriction Name</span></span>|<span data-ttu-id="af63a-238">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-238">Parameter Name</span></span>|<span data-ttu-id="af63a-239">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-239">Restriction Default</span></span>|<span data-ttu-id="af63a-240">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-241">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-241">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="af63a-243">1</span><span class="sxs-lookup"><span data-stu-id="af63a-243">1</span></span>|  
|<span data-ttu-id="af63a-244">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-244">Owner</span></span>|@Owner|<span data-ttu-id="af63a-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="af63a-246">2</span><span class="sxs-lookup"><span data-stu-id="af63a-246">2</span></span>|  
|<span data-ttu-id="af63a-247">Název</span><span class="sxs-lookup"><span data-stu-id="af63a-247">Name</span></span>|@Name|<span data-ttu-id="af63a-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="af63a-249">3</span><span class="sxs-lookup"><span data-stu-id="af63a-249">3</span></span>|  
|<span data-ttu-id="af63a-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="af63a-250">Parameter</span></span>|@Parameter|<span data-ttu-id="af63a-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-251">PARAMETER_NAME</span></span>|<span data-ttu-id="af63a-252">4</span><span class="sxs-lookup"><span data-stu-id="af63a-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="af63a-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="af63a-253">Procedures</span></span>  
  
|<span data-ttu-id="af63a-254">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-254">Restriction Name</span></span>|<span data-ttu-id="af63a-255">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-255">Parameter Name</span></span>|<span data-ttu-id="af63a-256">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-256">Restriction Default</span></span>|<span data-ttu-id="af63a-257">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-258">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="af63a-260">1</span><span class="sxs-lookup"><span data-stu-id="af63a-260">1</span></span>|  
|<span data-ttu-id="af63a-261">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-261">Owner</span></span>|@Owner|<span data-ttu-id="af63a-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="af63a-263">2</span><span class="sxs-lookup"><span data-stu-id="af63a-263">2</span></span>|  
|<span data-ttu-id="af63a-264">Název</span><span class="sxs-lookup"><span data-stu-id="af63a-264">Name</span></span>|@Name|<span data-ttu-id="af63a-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="af63a-266">3</span><span class="sxs-lookup"><span data-stu-id="af63a-266">3</span></span>|  
|<span data-ttu-id="af63a-267">Typ</span><span class="sxs-lookup"><span data-stu-id="af63a-267">Type</span></span>|@Type|<span data-ttu-id="af63a-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="af63a-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="af63a-269">4</span><span class="sxs-lookup"><span data-stu-id="af63a-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="af63a-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="af63a-270">IndexColumns</span></span>  
  
|<span data-ttu-id="af63a-271">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-271">Restriction Name</span></span>|<span data-ttu-id="af63a-272">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-272">Parameter Name</span></span>|<span data-ttu-id="af63a-273">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-273">Restriction Default</span></span>|<span data-ttu-id="af63a-274">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-275">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-275">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="af63a-276">db_name()</span></span>|<span data-ttu-id="af63a-277">1</span><span class="sxs-lookup"><span data-stu-id="af63a-277">1</span></span>|  
|<span data-ttu-id="af63a-278">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-278">Owner</span></span>|@Owner|<span data-ttu-id="af63a-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="af63a-279">user_name()</span></span>|<span data-ttu-id="af63a-280">2</span><span class="sxs-lookup"><span data-stu-id="af63a-280">2</span></span>|  
|<span data-ttu-id="af63a-281">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-281">Table</span></span>|@Table|<span data-ttu-id="af63a-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="af63a-282">o.name</span></span>|<span data-ttu-id="af63a-283">3</span><span class="sxs-lookup"><span data-stu-id="af63a-283">3</span></span>|  
|<span data-ttu-id="af63a-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="af63a-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="af63a-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="af63a-285">x.name</span></span>|<span data-ttu-id="af63a-286">4</span><span class="sxs-lookup"><span data-stu-id="af63a-286">4</span></span>|  
|<span data-ttu-id="af63a-287">Sloupec</span><span class="sxs-lookup"><span data-stu-id="af63a-287">Column</span></span>|@Column|<span data-ttu-id="af63a-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="af63a-288">c.name</span></span>|<span data-ttu-id="af63a-289">5</span><span class="sxs-lookup"><span data-stu-id="af63a-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="af63a-290">Indexy</span><span class="sxs-lookup"><span data-stu-id="af63a-290">Indexes</span></span>  
  
|<span data-ttu-id="af63a-291">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-291">Restriction Name</span></span>|<span data-ttu-id="af63a-292">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-292">Parameter Name</span></span>|<span data-ttu-id="af63a-293">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-293">Restriction Default</span></span>|<span data-ttu-id="af63a-294">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-295">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-295">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="af63a-296">db_name()</span></span>|<span data-ttu-id="af63a-297">1</span><span class="sxs-lookup"><span data-stu-id="af63a-297">1</span></span>|  
|<span data-ttu-id="af63a-298">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-298">Owner</span></span>|@Owner|<span data-ttu-id="af63a-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="af63a-299">user_name()</span></span>|<span data-ttu-id="af63a-300">2</span><span class="sxs-lookup"><span data-stu-id="af63a-300">2</span></span>|  
|<span data-ttu-id="af63a-301">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-301">Table</span></span>|@Table|<span data-ttu-id="af63a-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="af63a-302">o.name</span></span>|<span data-ttu-id="af63a-303">3</span><span class="sxs-lookup"><span data-stu-id="af63a-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="af63a-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="af63a-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="af63a-305">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-305">Restriction Name</span></span>|<span data-ttu-id="af63a-306">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-306">Parameter Name</span></span>|<span data-ttu-id="af63a-307">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-307">Restriction Default</span></span>|<span data-ttu-id="af63a-308">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="af63a-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="af63a-310">Assemblies.Name</span><span class="sxs-lookup"><span data-stu-id="af63a-310">assemblies.name</span></span>|<span data-ttu-id="af63a-311">1</span><span class="sxs-lookup"><span data-stu-id="af63a-311">1</span></span>|  
|<span data-ttu-id="af63a-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="af63a-312">udt_name</span></span>|@UDTName|<span data-ttu-id="af63a-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="af63a-313">types.assembly_class</span></span>|<span data-ttu-id="af63a-314">2</span><span class="sxs-lookup"><span data-stu-id="af63a-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="af63a-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="af63a-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="af63a-316">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-316">Restriction Name</span></span>|<span data-ttu-id="af63a-317">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-317">Parameter Name</span></span>|<span data-ttu-id="af63a-318">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-318">Restriction Default</span></span>|<span data-ttu-id="af63a-319">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-320">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-320">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="af63a-322">1</span><span class="sxs-lookup"><span data-stu-id="af63a-322">1</span></span>|  
|<span data-ttu-id="af63a-323">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-323">Owner</span></span>|@Owner|<span data-ttu-id="af63a-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="af63a-325">2</span><span class="sxs-lookup"><span data-stu-id="af63a-325">2</span></span>|  
|<span data-ttu-id="af63a-326">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-326">Table</span></span>|@Table|<span data-ttu-id="af63a-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-327">TABLE_NAME</span></span>|<span data-ttu-id="af63a-328">3</span><span class="sxs-lookup"><span data-stu-id="af63a-328">3</span></span>|  
|<span data-ttu-id="af63a-329">Název</span><span class="sxs-lookup"><span data-stu-id="af63a-329">Name</span></span>|@Name|<span data-ttu-id="af63a-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="af63a-331">4</span><span class="sxs-lookup"><span data-stu-id="af63a-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="af63a-332">SQL Server 2008 schématu omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="af63a-333">V následujících tabulkách najdete omezení pro SQL Server 2008 kolekcemi schémat.</span><span class="sxs-lookup"><span data-stu-id="af63a-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="af63a-334">Tato omezení jsou platné od verze verze systému SQL Server 2008 a rozhraní .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="af63a-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="af63a-335">Nejsou podporovány v dřívějších verzích rozhraní .NET Framework a SQL Server.</span><span class="sxs-lookup"><span data-stu-id="af63a-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="af63a-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="af63a-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="af63a-337">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-337">Restriction Name</span></span>|<span data-ttu-id="af63a-338">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-338">Parameter Name</span></span>|<span data-ttu-id="af63a-339">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-339">Restriction Default</span></span>|<span data-ttu-id="af63a-340">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-341">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-341">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-342">TABLE_CATALOG</span></span>|<span data-ttu-id="af63a-343">1</span><span class="sxs-lookup"><span data-stu-id="af63a-343">1</span></span>|  
|<span data-ttu-id="af63a-344">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-344">Owner</span></span>|@Owner|<span data-ttu-id="af63a-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="af63a-346">2</span><span class="sxs-lookup"><span data-stu-id="af63a-346">2</span></span>|  
|<span data-ttu-id="af63a-347">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-347">Table</span></span>|@Table|<span data-ttu-id="af63a-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-348">TABLE_NAME</span></span>|<span data-ttu-id="af63a-349">3</span><span class="sxs-lookup"><span data-stu-id="af63a-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="af63a-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="af63a-350">AllColumns</span></span>  
  
|<span data-ttu-id="af63a-351">Název omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-351">Restriction Name</span></span>|<span data-ttu-id="af63a-352">Název parametru</span><span class="sxs-lookup"><span data-stu-id="af63a-352">Parameter Name</span></span>|<span data-ttu-id="af63a-353">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-353">Restriction Default</span></span>|<span data-ttu-id="af63a-354">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="af63a-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="af63a-355">Katalogu</span><span class="sxs-lookup"><span data-stu-id="af63a-355">Catalog</span></span>|@Catalog|<span data-ttu-id="af63a-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="af63a-356">TABLE_CATALOG</span></span>|<span data-ttu-id="af63a-357">1</span><span class="sxs-lookup"><span data-stu-id="af63a-357">1</span></span>|  
|<span data-ttu-id="af63a-358">Vlastník</span><span class="sxs-lookup"><span data-stu-id="af63a-358">Owner</span></span>|@Owner|<span data-ttu-id="af63a-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="af63a-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="af63a-360">2</span><span class="sxs-lookup"><span data-stu-id="af63a-360">2</span></span>|  
|<span data-ttu-id="af63a-361">Tabulka</span><span class="sxs-lookup"><span data-stu-id="af63a-361">Table</span></span>|@Table|<span data-ttu-id="af63a-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-362">TABLE_NAME</span></span>|<span data-ttu-id="af63a-363">3</span><span class="sxs-lookup"><span data-stu-id="af63a-363">3</span></span>|  
|<span data-ttu-id="af63a-364">Sloupec</span><span class="sxs-lookup"><span data-stu-id="af63a-364">Column</span></span>|@Column|<span data-ttu-id="af63a-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="af63a-365">COLUMN_NAME</span></span>|<span data-ttu-id="af63a-366">4</span><span class="sxs-lookup"><span data-stu-id="af63a-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af63a-367">Viz také</span><span class="sxs-lookup"><span data-stu-id="af63a-367">See Also</span></span>  
 [<span data-ttu-id="af63a-368">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="af63a-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
