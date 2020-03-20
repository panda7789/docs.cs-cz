---
title: Omezení schématu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149008"
---
# <a name="schema-restrictions"></a><span data-ttu-id="5ca59-102">Omezení schématu</span><span class="sxs-lookup"><span data-stu-id="5ca59-102">Schema Restrictions</span></span>
<span data-ttu-id="5ca59-103">Druhý volitelný parametr **Metody GetSchema** je omezení, které se používají k omezení množství informací o schématu vrácena a je předán **a GetSchema** metoda jako pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="5ca59-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="5ca59-104">Pozice v poli určuje hodnoty, které můžete předat, a to je ekvivalentní číslo omezení.</span><span class="sxs-lookup"><span data-stu-id="5ca59-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="5ca59-105">V následující tabulce jsou například popsána omezení podporovaná kolekcí schématu Tabulky pomocí zprostředkovatele dat rozhraní .NET Framework pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ca59-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="5ca59-106">Další omezení pro kolekce schématu sql serveru jsou uvedeny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="5ca59-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="5ca59-107">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-107">Restriction Name</span></span>|<span data-ttu-id="5ca59-108">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-108">Parameter Name</span></span>|<span data-ttu-id="5ca59-109">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-109">Restriction Default</span></span>|<span data-ttu-id="5ca59-110">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-111">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-112">TABLE_CATALOG</span></span>|<span data-ttu-id="5ca59-113">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-113">1</span></span>|  
|<span data-ttu-id="5ca59-114">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-114">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ca59-116">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-116">2</span></span>|  
|<span data-ttu-id="5ca59-117">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-117">Table</span></span>|@Name|<span data-ttu-id="5ca59-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-118">TABLE_NAME</span></span>|<span data-ttu-id="5ca59-119">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-119">3</span></span>|  
|<span data-ttu-id="5ca59-120">Typ tabulky</span><span class="sxs-lookup"><span data-stu-id="5ca59-120">TableType</span></span>|@TableType|<span data-ttu-id="5ca59-121">Table_type</span><span class="sxs-lookup"><span data-stu-id="5ca59-121">TABLE_TYPE</span></span>|<span data-ttu-id="5ca59-122">4</span><span class="sxs-lookup"><span data-stu-id="5ca59-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="5ca59-123">Určení hodnot omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="5ca59-124">Chcete-li použít jedno z omezení kolekce schématu "Tabulky", jednoduše vytvořte pole řetězců se čtyřmi prvky a umístěte hodnotu do prvku, který odpovídá číslu omezení.</span><span class="sxs-lookup"><span data-stu-id="5ca59-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="5ca59-125">Chcete-li například omezit tabulky vrácené metodou **GetSchema** pouze na ty tabulky ve schématu "Prodej", nastavte druhý prvek pole na "Prodej" před jeho předáním metodě **GetSchema.**</span><span class="sxs-lookup"><span data-stu-id="5ca59-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ca59-126">Kolekce omezení pro `SqlClient` `OracleClient` a mají `ParameterName` další sloupec.</span><span class="sxs-lookup"><span data-stu-id="5ca59-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="5ca59-127">Výchozí sloupec omezení je stále k dispozici pro zpětnou kompatibilitu, ale je aktuálně ignorován.</span><span class="sxs-lookup"><span data-stu-id="5ca59-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="5ca59-128">Parametrizované dotazy spíše než nahrazení řetězce by měly být použity k minimalizaci rizika útoku injektáže SQL při zadávání hodnot omezení.</span><span class="sxs-lookup"><span data-stu-id="5ca59-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ca59-129">Počet prvků v poli musí být menší nebo rovno počtu omezení podporovaných pro zadanou kolekci schématu, jinak <xref:System.ArgumentException> bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="5ca59-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="5ca59-130">Může být menší než maximální počet omezení.</span><span class="sxs-lookup"><span data-stu-id="5ca59-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="5ca59-131">Chybějící omezení jsou považovány za null (bez omezení).</span><span class="sxs-lookup"><span data-stu-id="5ca59-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="5ca59-132">Můžete dotaz zprostředkovatele spravovaného rozhraní .NET Framework určit seznam podporovaných omezení voláním **GetSchema** metoda s názvem kolekce schématu omezení, což je "Omezení".</span><span class="sxs-lookup"><span data-stu-id="5ca59-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="5ca59-133">Tím se <xref:System.Data.DataTable> vrátí seznam názvů kolekcí, názvy omezení, výchozí hodnoty omezení a čísla omezení.</span><span class="sxs-lookup"><span data-stu-id="5ca59-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="5ca59-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ca59-134">Example</span></span>  
 <span data-ttu-id="5ca59-135">Následující příklady ukazují, jak <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> použít metodu zprostředkovatele dat rozhraní <xref:System.Data.SqlClient.SqlConnection> .NET Framework pro třídu SQL Server k načtení informací o schématu o všech tabulkách obsažených v ukázkové databázi **AdventureWorks** a omezit informace vrácené pouze do těchto tabulek ve schématu Prodej:</span><span class="sxs-lookup"><span data-stu-id="5ca59-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="5ca59-136">Omezení schématu serveru SQL Server</span><span class="sxs-lookup"><span data-stu-id="5ca59-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="5ca59-137">V následujících tabulkách jsou uvedena omezení pro kolekce schématu serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ca59-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="5ca59-138">Uživatelé</span><span class="sxs-lookup"><span data-stu-id="5ca59-138">Users</span></span>  
  
|<span data-ttu-id="5ca59-139">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-139">Restriction Name</span></span>|<span data-ttu-id="5ca59-140">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-140">Parameter Name</span></span>|<span data-ttu-id="5ca59-141">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-141">Restriction Default</span></span>|<span data-ttu-id="5ca59-142">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-143">User_name</span><span class="sxs-lookup"><span data-stu-id="5ca59-143">User_Name</span></span>|@Name|<span data-ttu-id="5ca59-144">jméno</span><span class="sxs-lookup"><span data-stu-id="5ca59-144">name</span></span>|<span data-ttu-id="5ca59-145">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="5ca59-146">Databáze</span><span class="sxs-lookup"><span data-stu-id="5ca59-146">Databases</span></span>  
  
|<span data-ttu-id="5ca59-147">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-147">Restriction Name</span></span>|<span data-ttu-id="5ca59-148">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-148">Parameter Name</span></span>|<span data-ttu-id="5ca59-149">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-149">Restriction Default</span></span>|<span data-ttu-id="5ca59-150">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-151">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="5ca59-151">Name</span></span>|@Name|<span data-ttu-id="5ca59-152">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="5ca59-152">Name</span></span>|<span data-ttu-id="5ca59-153">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="5ca59-154">Tabulky</span><span class="sxs-lookup"><span data-stu-id="5ca59-154">Tables</span></span>  
  
|<span data-ttu-id="5ca59-155">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-155">Restriction Name</span></span>|<span data-ttu-id="5ca59-156">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-156">Parameter Name</span></span>|<span data-ttu-id="5ca59-157">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-157">Restriction Default</span></span>|<span data-ttu-id="5ca59-158">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-159">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-160">TABLE_CATALOG</span></span>|<span data-ttu-id="5ca59-161">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-161">1</span></span>|  
|<span data-ttu-id="5ca59-162">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-162">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ca59-164">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-164">2</span></span>|  
|<span data-ttu-id="5ca59-165">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-165">Table</span></span>|@Name|<span data-ttu-id="5ca59-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-166">TABLE_NAME</span></span>|<span data-ttu-id="5ca59-167">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-167">3</span></span>|  
|<span data-ttu-id="5ca59-168">Typ tabulky</span><span class="sxs-lookup"><span data-stu-id="5ca59-168">TableType</span></span>|@TableType|<span data-ttu-id="5ca59-169">Table_type</span><span class="sxs-lookup"><span data-stu-id="5ca59-169">TABLE_TYPE</span></span>|<span data-ttu-id="5ca59-170">4</span><span class="sxs-lookup"><span data-stu-id="5ca59-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="5ca59-171">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5ca59-171">Columns</span></span>  
  
|<span data-ttu-id="5ca59-172">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-172">Restriction Name</span></span>|<span data-ttu-id="5ca59-173">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-173">Parameter Name</span></span>|<span data-ttu-id="5ca59-174">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-174">Restriction Default</span></span>|<span data-ttu-id="5ca59-175">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-176">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-177">TABLE_CATALOG</span></span>|<span data-ttu-id="5ca59-178">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-178">1</span></span>|  
|<span data-ttu-id="5ca59-179">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-179">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ca59-181">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-181">2</span></span>|  
|<span data-ttu-id="5ca59-182">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-182">Table</span></span>|@Table|<span data-ttu-id="5ca59-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-183">TABLE_NAME</span></span>|<span data-ttu-id="5ca59-184">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-184">3</span></span>|  
|<span data-ttu-id="5ca59-185">Sloupec</span><span class="sxs-lookup"><span data-stu-id="5ca59-185">Column</span></span>|@Column|<span data-ttu-id="5ca59-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-186">COLUMN_NAME</span></span>|<span data-ttu-id="5ca59-187">4</span><span class="sxs-lookup"><span data-stu-id="5ca59-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="5ca59-188">Členové structuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="5ca59-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="5ca59-189">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-189">Restriction Name</span></span>|<span data-ttu-id="5ca59-190">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-190">Parameter Name</span></span>|<span data-ttu-id="5ca59-191">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-191">Restriction Default</span></span>|<span data-ttu-id="5ca59-192">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-193">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-194">TABLE_CATALOG</span></span>|<span data-ttu-id="5ca59-195">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-195">1</span></span>|  
|<span data-ttu-id="5ca59-196">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-196">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ca59-198">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-198">2</span></span>|  
|<span data-ttu-id="5ca59-199">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-199">Table</span></span>|@Table|<span data-ttu-id="5ca59-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-200">TABLE_NAME</span></span>|<span data-ttu-id="5ca59-201">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-201">3</span></span>|  
|<span data-ttu-id="5ca59-202">Sloupec</span><span class="sxs-lookup"><span data-stu-id="5ca59-202">Column</span></span>|@Column|<span data-ttu-id="5ca59-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-203">COLUMN_NAME</span></span>|<span data-ttu-id="5ca59-204">4</span><span class="sxs-lookup"><span data-stu-id="5ca59-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="5ca59-205">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="5ca59-205">Views</span></span>  
  
|<span data-ttu-id="5ca59-206">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-206">Restriction Name</span></span>|<span data-ttu-id="5ca59-207">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-207">Parameter Name</span></span>|<span data-ttu-id="5ca59-208">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-208">Restriction Default</span></span>|<span data-ttu-id="5ca59-209">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-210">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-211">TABLE_CATALOG</span></span>|<span data-ttu-id="5ca59-212">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-212">1</span></span>|  
|<span data-ttu-id="5ca59-213">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-213">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ca59-215">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-215">2</span></span>|  
|<span data-ttu-id="5ca59-216">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-216">Table</span></span>|@Table|<span data-ttu-id="5ca59-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-217">TABLE_NAME</span></span>|<span data-ttu-id="5ca59-218">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="5ca59-219">Zobrazit sloupce</span><span class="sxs-lookup"><span data-stu-id="5ca59-219">ViewColumns</span></span>  
  
|<span data-ttu-id="5ca59-220">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-220">Restriction Name</span></span>|<span data-ttu-id="5ca59-221">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-221">Parameter Name</span></span>|<span data-ttu-id="5ca59-222">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-222">Restriction Default</span></span>|<span data-ttu-id="5ca59-223">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-224">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-225">VIEW_CATALOG</span></span>|<span data-ttu-id="5ca59-226">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-226">1</span></span>|  
|<span data-ttu-id="5ca59-227">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-227">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="5ca59-229">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-229">2</span></span>|  
|<span data-ttu-id="5ca59-230">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-230">Table</span></span>|@Table|<span data-ttu-id="5ca59-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-231">VIEW_NAME</span></span>|<span data-ttu-id="5ca59-232">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-232">3</span></span>|  
|<span data-ttu-id="5ca59-233">Sloupec</span><span class="sxs-lookup"><span data-stu-id="5ca59-233">Column</span></span>|@Column|<span data-ttu-id="5ca59-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-234">COLUMN_NAME</span></span>|<span data-ttu-id="5ca59-235">4</span><span class="sxs-lookup"><span data-stu-id="5ca59-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="5ca59-236">Parametry procedury</span><span class="sxs-lookup"><span data-stu-id="5ca59-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="5ca59-237">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-237">Restriction Name</span></span>|<span data-ttu-id="5ca59-238">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-238">Parameter Name</span></span>|<span data-ttu-id="5ca59-239">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-239">Restriction Default</span></span>|<span data-ttu-id="5ca59-240">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-241">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="5ca59-243">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-243">1</span></span>|  
|<span data-ttu-id="5ca59-244">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-244">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="5ca59-246">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-246">2</span></span>|  
|<span data-ttu-id="5ca59-247">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="5ca59-247">Name</span></span>|@Name|<span data-ttu-id="5ca59-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="5ca59-249">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-249">3</span></span>|  
|<span data-ttu-id="5ca59-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="5ca59-250">Parameter</span></span>|@Parameter|<span data-ttu-id="5ca59-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-251">PARAMETER_NAME</span></span>|<span data-ttu-id="5ca59-252">4</span><span class="sxs-lookup"><span data-stu-id="5ca59-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="5ca59-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="5ca59-253">Procedures</span></span>  
  
|<span data-ttu-id="5ca59-254">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-254">Restriction Name</span></span>|<span data-ttu-id="5ca59-255">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-255">Parameter Name</span></span>|<span data-ttu-id="5ca59-256">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-256">Restriction Default</span></span>|<span data-ttu-id="5ca59-257">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-258">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="5ca59-260">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-260">1</span></span>|  
|<span data-ttu-id="5ca59-261">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-261">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="5ca59-263">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-263">2</span></span>|  
|<span data-ttu-id="5ca59-264">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="5ca59-264">Name</span></span>|@Name|<span data-ttu-id="5ca59-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="5ca59-266">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-266">3</span></span>|  
|<span data-ttu-id="5ca59-267">Typ</span><span class="sxs-lookup"><span data-stu-id="5ca59-267">Type</span></span>|@Type|<span data-ttu-id="5ca59-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5ca59-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="5ca59-269">4</span><span class="sxs-lookup"><span data-stu-id="5ca59-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="5ca59-270">IndexSloupce</span><span class="sxs-lookup"><span data-stu-id="5ca59-270">IndexColumns</span></span>  
  
|<span data-ttu-id="5ca59-271">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-271">Restriction Name</span></span>|<span data-ttu-id="5ca59-272">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-272">Parameter Name</span></span>|<span data-ttu-id="5ca59-273">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-273">Restriction Default</span></span>|<span data-ttu-id="5ca59-274">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-275">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="5ca59-276">db_name()</span></span>|<span data-ttu-id="5ca59-277">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-277">1</span></span>|  
|<span data-ttu-id="5ca59-278">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-278">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="5ca59-279">user_name()</span></span>|<span data-ttu-id="5ca59-280">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-280">2</span></span>|  
|<span data-ttu-id="5ca59-281">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-281">Table</span></span>|@Table|<span data-ttu-id="5ca59-282">o.name</span><span class="sxs-lookup"><span data-stu-id="5ca59-282">o.name</span></span>|<span data-ttu-id="5ca59-283">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-283">3</span></span>|  
|<span data-ttu-id="5ca59-284">Název_omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="5ca59-285">x.name</span><span class="sxs-lookup"><span data-stu-id="5ca59-285">x.name</span></span>|<span data-ttu-id="5ca59-286">4</span><span class="sxs-lookup"><span data-stu-id="5ca59-286">4</span></span>|  
|<span data-ttu-id="5ca59-287">Sloupec</span><span class="sxs-lookup"><span data-stu-id="5ca59-287">Column</span></span>|@Column|<span data-ttu-id="5ca59-288">c.name</span><span class="sxs-lookup"><span data-stu-id="5ca59-288">c.name</span></span>|<span data-ttu-id="5ca59-289">5</span><span class="sxs-lookup"><span data-stu-id="5ca59-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="5ca59-290">Indexy</span><span class="sxs-lookup"><span data-stu-id="5ca59-290">Indexes</span></span>  
  
|<span data-ttu-id="5ca59-291">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-291">Restriction Name</span></span>|<span data-ttu-id="5ca59-292">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-292">Parameter Name</span></span>|<span data-ttu-id="5ca59-293">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-293">Restriction Default</span></span>|<span data-ttu-id="5ca59-294">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-295">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="5ca59-296">db_name()</span></span>|<span data-ttu-id="5ca59-297">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-297">1</span></span>|  
|<span data-ttu-id="5ca59-298">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-298">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="5ca59-299">user_name()</span></span>|<span data-ttu-id="5ca59-300">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-300">2</span></span>|  
|<span data-ttu-id="5ca59-301">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-301">Table</span></span>|@Table|<span data-ttu-id="5ca59-302">o.name</span><span class="sxs-lookup"><span data-stu-id="5ca59-302">o.name</span></span>|<span data-ttu-id="5ca59-303">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="5ca59-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="5ca59-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="5ca59-305">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-305">Restriction Name</span></span>|<span data-ttu-id="5ca59-306">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-306">Parameter Name</span></span>|<span data-ttu-id="5ca59-307">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-307">Restriction Default</span></span>|<span data-ttu-id="5ca59-308">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="5ca59-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="5ca59-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="5ca59-310">assemblies.name</span></span>|<span data-ttu-id="5ca59-311">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-311">1</span></span>|  
|<span data-ttu-id="5ca59-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="5ca59-312">udt_name</span></span>|@UDTName|<span data-ttu-id="5ca59-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="5ca59-313">types.assembly_class</span></span>|<span data-ttu-id="5ca59-314">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="5ca59-315">Cizí klíče</span><span class="sxs-lookup"><span data-stu-id="5ca59-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="5ca59-316">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-316">Restriction Name</span></span>|<span data-ttu-id="5ca59-317">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-317">Parameter Name</span></span>|<span data-ttu-id="5ca59-318">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-318">Restriction Default</span></span>|<span data-ttu-id="5ca59-319">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-320">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="5ca59-322">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-322">1</span></span>|  
|<span data-ttu-id="5ca59-323">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-323">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="5ca59-325">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-325">2</span></span>|  
|<span data-ttu-id="5ca59-326">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-326">Table</span></span>|@Table|<span data-ttu-id="5ca59-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-327">TABLE_NAME</span></span>|<span data-ttu-id="5ca59-328">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-328">3</span></span>|  
|<span data-ttu-id="5ca59-329">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="5ca59-329">Name</span></span>|@Name|<span data-ttu-id="5ca59-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="5ca59-331">4</span><span class="sxs-lookup"><span data-stu-id="5ca59-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="5ca59-332">Omezení schématu serveru SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="5ca59-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="5ca59-333">V následujících tabulkách jsou uvedena omezení pro kolekce schématu serveru SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="5ca59-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="5ca59-334">Tato omezení jsou platná počínaje verzí 3.5 SP1 rozhraní .NET Framework a SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="5ca59-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="5ca59-335">Nejsou podporovány v dřívějších verzích rozhraní .NET Framework a SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ca59-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="5ca59-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="5ca59-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="5ca59-337">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-337">Restriction Name</span></span>|<span data-ttu-id="5ca59-338">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-338">Parameter Name</span></span>|<span data-ttu-id="5ca59-339">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-339">Restriction Default</span></span>|<span data-ttu-id="5ca59-340">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-341">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-342">TABLE_CATALOG</span></span>|<span data-ttu-id="5ca59-343">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-343">1</span></span>|  
|<span data-ttu-id="5ca59-344">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-344">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ca59-346">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-346">2</span></span>|  
|<span data-ttu-id="5ca59-347">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-347">Table</span></span>|@Table|<span data-ttu-id="5ca59-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-348">TABLE_NAME</span></span>|<span data-ttu-id="5ca59-349">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="5ca59-350">Všechny sloupce</span><span class="sxs-lookup"><span data-stu-id="5ca59-350">AllColumns</span></span>  
  
|<span data-ttu-id="5ca59-351">Název omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-351">Restriction Name</span></span>|<span data-ttu-id="5ca59-352">Název parametru</span><span class="sxs-lookup"><span data-stu-id="5ca59-352">Parameter Name</span></span>|<span data-ttu-id="5ca59-353">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-353">Restriction Default</span></span>|<span data-ttu-id="5ca59-354">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="5ca59-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="5ca59-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="5ca59-355">Catalog</span></span>|@Catalog|<span data-ttu-id="5ca59-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5ca59-356">TABLE_CATALOG</span></span>|<span data-ttu-id="5ca59-357">1</span><span class="sxs-lookup"><span data-stu-id="5ca59-357">1</span></span>|  
|<span data-ttu-id="5ca59-358">Vlastník</span><span class="sxs-lookup"><span data-stu-id="5ca59-358">Owner</span></span>|@Owner|<span data-ttu-id="5ca59-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5ca59-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="5ca59-360">2</span><span class="sxs-lookup"><span data-stu-id="5ca59-360">2</span></span>|  
|<span data-ttu-id="5ca59-361">Table</span><span class="sxs-lookup"><span data-stu-id="5ca59-361">Table</span></span>|@Table|<span data-ttu-id="5ca59-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-362">TABLE_NAME</span></span>|<span data-ttu-id="5ca59-363">3</span><span class="sxs-lookup"><span data-stu-id="5ca59-363">3</span></span>|  
|<span data-ttu-id="5ca59-364">Sloupec</span><span class="sxs-lookup"><span data-stu-id="5ca59-364">Column</span></span>|@Column|<span data-ttu-id="5ca59-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5ca59-365">COLUMN_NAME</span></span>|<span data-ttu-id="5ca59-366">4</span><span class="sxs-lookup"><span data-stu-id="5ca59-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ca59-367">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ca59-367">See also</span></span>

- [<span data-ttu-id="5ca59-368">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5ca59-368">ADO.NET Overview</span></span>](ado-net-overview.md)
