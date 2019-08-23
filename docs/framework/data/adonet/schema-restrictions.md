---
title: Omezení schématu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 1a2c32d133799ee5338c18d0f51bced49cb3dc4b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963185"
---
# <a name="schema-restrictions"></a><span data-ttu-id="d8603-102">Omezení schématu</span><span class="sxs-lookup"><span data-stu-id="d8603-102">Schema Restrictions</span></span>
<span data-ttu-id="d8603-103">Druhý volitelný parametr metody GetSchema je omezení, která slouží k omezení množství vrácených informací o schématu a je předána metodě GetSchema jako poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="d8603-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="d8603-104">Pozice v poli určuje hodnoty, které lze předat, a to je ekvivalentní k číslu omezení.</span><span class="sxs-lookup"><span data-stu-id="d8603-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="d8603-105">Například následující tabulka popisuje omezení podporovaná kolekcí schémat "Tables" pomocí Zprostředkovatel dat .NET Framework pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d8603-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="d8603-106">Další omezení pro kolekce schémat SQL Server jsou uvedena na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d8603-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="d8603-107">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-107">Restriction Name</span></span>|<span data-ttu-id="d8603-108">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-108">Parameter Name</span></span>|<span data-ttu-id="d8603-109">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-109">Restriction Default</span></span>|<span data-ttu-id="d8603-110">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-111">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-112">TABLE_CATALOG</span></span>|<span data-ttu-id="d8603-113">1</span><span class="sxs-lookup"><span data-stu-id="d8603-113">1</span></span>|  
|<span data-ttu-id="d8603-114">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-114">Owner</span></span>|@Owner|<span data-ttu-id="d8603-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8603-116">2</span><span class="sxs-lookup"><span data-stu-id="d8603-116">2</span></span>|  
|<span data-ttu-id="d8603-117">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-117">Table</span></span>|@Name|<span data-ttu-id="d8603-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-118">TABLE_NAME</span></span>|<span data-ttu-id="d8603-119">3</span><span class="sxs-lookup"><span data-stu-id="d8603-119">3</span></span>|  
|<span data-ttu-id="d8603-120">TableType</span><span class="sxs-lookup"><span data-stu-id="d8603-120">TableType</span></span>|@TableType|<span data-ttu-id="d8603-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8603-121">TABLE_TYPE</span></span>|<span data-ttu-id="d8603-122">4</span><span class="sxs-lookup"><span data-stu-id="d8603-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="d8603-123">Určení hodnot omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="d8603-124">Chcete-li použít jedno z omezení kolekce schématu "Tables", jednoduše vytvořte pole řetězců se čtyřmi prvky a potom umístěte hodnotu do prvku, který odpovídá číslu omezení.</span><span class="sxs-lookup"><span data-stu-id="d8603-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="d8603-125">Chcete-li například omezit tabulky vrácené metodou GetSchema pouze na tabulky ve schématu "Sales", nastavte druhý prvek pole na "Sales", než jej předáte metodě GetSchema.</span><span class="sxs-lookup"><span data-stu-id="d8603-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8603-126">Kolekce omezení pro `SqlClient` a `OracleClient` mají další `ParameterName` sloupec.</span><span class="sxs-lookup"><span data-stu-id="d8603-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="d8603-127">Výchozí sloupec omezení je stále pro zpětnou kompatibilitu, ale v současné době se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="d8603-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="d8603-128">Parametrizované dotazy místo nahrazení řetězců by měly být použity k minimalizaci rizika útoku prostřednictvím injektáže SQL při zadávání hodnot omezení.</span><span class="sxs-lookup"><span data-stu-id="d8603-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8603-129">Počet elementů v poli musí být menší nebo roven počtu omezení podporovaných pro zadanou kolekci schémat, jinak <xref:System.ArgumentException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d8603-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="d8603-130">Může jich být méně, než je maximální počet omezení.</span><span class="sxs-lookup"><span data-stu-id="d8603-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="d8603-131">U chybějících omezení se předpokládá, že mají hodnotu null (neomezeno).</span><span class="sxs-lookup"><span data-stu-id="d8603-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="d8603-132">Můžete zadat dotaz na .NET Framework spravovaného poskytovatele a určit seznam podporovaných omezení voláním metody **GetSchema** s názvem kolekce schématu omezení, což je "omezení".</span><span class="sxs-lookup"><span data-stu-id="d8603-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="d8603-133">Tato akce vrátí <xref:System.Data.DataTable> seznam názvů kolekcí, názvy omezení, výchozí hodnoty omezení a čísla omezení.</span><span class="sxs-lookup"><span data-stu-id="d8603-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d8603-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8603-134">Example</span></span>  
 <span data-ttu-id="d8603-135">Následující příklady ukazují, jak použít <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metodu .NET Framework Zprostředkovatel dat pro třídu SQL Server <xref:System.Data.SqlClient.SqlConnection> k načtení informací o schématu o všech tabulkách obsažených v ukázkové databázi **AdventureWorks** , a omezení vrácených informací pouze do tabulek ve schématu prodej:</span><span class="sxs-lookup"><span data-stu-id="d8603-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="d8603-136">SQL Server omezení schématu</span><span class="sxs-lookup"><span data-stu-id="d8603-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="d8603-137">V následujících tabulkách jsou uvedeny omezení pro SQL Server kolekcí schémat.</span><span class="sxs-lookup"><span data-stu-id="d8603-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="d8603-138">Uživatelé</span><span class="sxs-lookup"><span data-stu-id="d8603-138">Users</span></span>  
  
|<span data-ttu-id="d8603-139">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-139">Restriction Name</span></span>|<span data-ttu-id="d8603-140">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-140">Parameter Name</span></span>|<span data-ttu-id="d8603-141">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-141">Restriction Default</span></span>|<span data-ttu-id="d8603-142">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-143">Uživatelské jméno</span><span class="sxs-lookup"><span data-stu-id="d8603-143">User_Name</span></span>|@Name|<span data-ttu-id="d8603-144">name</span><span class="sxs-lookup"><span data-stu-id="d8603-144">name</span></span>|<span data-ttu-id="d8603-145">1</span><span class="sxs-lookup"><span data-stu-id="d8603-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="d8603-146">Databáze</span><span class="sxs-lookup"><span data-stu-id="d8603-146">Databases</span></span>  
  
|<span data-ttu-id="d8603-147">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-147">Restriction Name</span></span>|<span data-ttu-id="d8603-148">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-148">Parameter Name</span></span>|<span data-ttu-id="d8603-149">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-149">Restriction Default</span></span>|<span data-ttu-id="d8603-150">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-151">Name</span><span class="sxs-lookup"><span data-stu-id="d8603-151">Name</span></span>|@Name|<span data-ttu-id="d8603-152">Name</span><span class="sxs-lookup"><span data-stu-id="d8603-152">Name</span></span>|<span data-ttu-id="d8603-153">1</span><span class="sxs-lookup"><span data-stu-id="d8603-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="d8603-154">Tabulky</span><span class="sxs-lookup"><span data-stu-id="d8603-154">Tables</span></span>  
  
|<span data-ttu-id="d8603-155">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-155">Restriction Name</span></span>|<span data-ttu-id="d8603-156">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-156">Parameter Name</span></span>|<span data-ttu-id="d8603-157">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-157">Restriction Default</span></span>|<span data-ttu-id="d8603-158">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-159">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-160">TABLE_CATALOG</span></span>|<span data-ttu-id="d8603-161">1</span><span class="sxs-lookup"><span data-stu-id="d8603-161">1</span></span>|  
|<span data-ttu-id="d8603-162">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-162">Owner</span></span>|@Owner|<span data-ttu-id="d8603-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8603-164">2</span><span class="sxs-lookup"><span data-stu-id="d8603-164">2</span></span>|  
|<span data-ttu-id="d8603-165">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-165">Table</span></span>|@Name|<span data-ttu-id="d8603-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-166">TABLE_NAME</span></span>|<span data-ttu-id="d8603-167">3</span><span class="sxs-lookup"><span data-stu-id="d8603-167">3</span></span>|  
|<span data-ttu-id="d8603-168">TableType</span><span class="sxs-lookup"><span data-stu-id="d8603-168">TableType</span></span>|@TableType|<span data-ttu-id="d8603-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8603-169">TABLE_TYPE</span></span>|<span data-ttu-id="d8603-170">4</span><span class="sxs-lookup"><span data-stu-id="d8603-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d8603-171">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d8603-171">Columns</span></span>  
  
|<span data-ttu-id="d8603-172">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-172">Restriction Name</span></span>|<span data-ttu-id="d8603-173">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-173">Parameter Name</span></span>|<span data-ttu-id="d8603-174">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-174">Restriction Default</span></span>|<span data-ttu-id="d8603-175">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-176">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-177">TABLE_CATALOG</span></span>|<span data-ttu-id="d8603-178">1</span><span class="sxs-lookup"><span data-stu-id="d8603-178">1</span></span>|  
|<span data-ttu-id="d8603-179">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-179">Owner</span></span>|@Owner|<span data-ttu-id="d8603-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8603-181">2</span><span class="sxs-lookup"><span data-stu-id="d8603-181">2</span></span>|  
|<span data-ttu-id="d8603-182">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-182">Table</span></span>|@Table|<span data-ttu-id="d8603-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-183">TABLE_NAME</span></span>|<span data-ttu-id="d8603-184">3</span><span class="sxs-lookup"><span data-stu-id="d8603-184">3</span></span>|  
|<span data-ttu-id="d8603-185">Sloupec</span><span class="sxs-lookup"><span data-stu-id="d8603-185">Column</span></span>|@Column|<span data-ttu-id="d8603-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-186">COLUMN_NAME</span></span>|<span data-ttu-id="d8603-187">4</span><span class="sxs-lookup"><span data-stu-id="d8603-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="d8603-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="d8603-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="d8603-189">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-189">Restriction Name</span></span>|<span data-ttu-id="d8603-190">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-190">Parameter Name</span></span>|<span data-ttu-id="d8603-191">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-191">Restriction Default</span></span>|<span data-ttu-id="d8603-192">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-193">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-194">TABLE_CATALOG</span></span>|<span data-ttu-id="d8603-195">1</span><span class="sxs-lookup"><span data-stu-id="d8603-195">1</span></span>|  
|<span data-ttu-id="d8603-196">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-196">Owner</span></span>|@Owner|<span data-ttu-id="d8603-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8603-198">2</span><span class="sxs-lookup"><span data-stu-id="d8603-198">2</span></span>|  
|<span data-ttu-id="d8603-199">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-199">Table</span></span>|@Table|<span data-ttu-id="d8603-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-200">TABLE_NAME</span></span>|<span data-ttu-id="d8603-201">3</span><span class="sxs-lookup"><span data-stu-id="d8603-201">3</span></span>|  
|<span data-ttu-id="d8603-202">Sloupec</span><span class="sxs-lookup"><span data-stu-id="d8603-202">Column</span></span>|@Column|<span data-ttu-id="d8603-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-203">COLUMN_NAME</span></span>|<span data-ttu-id="d8603-204">4</span><span class="sxs-lookup"><span data-stu-id="d8603-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="d8603-205">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="d8603-205">Views</span></span>  
  
|<span data-ttu-id="d8603-206">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-206">Restriction Name</span></span>|<span data-ttu-id="d8603-207">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-207">Parameter Name</span></span>|<span data-ttu-id="d8603-208">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-208">Restriction Default</span></span>|<span data-ttu-id="d8603-209">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-210">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-211">TABLE_CATALOG</span></span>|<span data-ttu-id="d8603-212">1</span><span class="sxs-lookup"><span data-stu-id="d8603-212">1</span></span>|  
|<span data-ttu-id="d8603-213">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-213">Owner</span></span>|@Owner|<span data-ttu-id="d8603-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8603-215">2</span><span class="sxs-lookup"><span data-stu-id="d8603-215">2</span></span>|  
|<span data-ttu-id="d8603-216">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-216">Table</span></span>|@Table|<span data-ttu-id="d8603-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-217">TABLE_NAME</span></span>|<span data-ttu-id="d8603-218">3</span><span class="sxs-lookup"><span data-stu-id="d8603-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="d8603-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="d8603-219">ViewColumns</span></span>  
  
|<span data-ttu-id="d8603-220">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-220">Restriction Name</span></span>|<span data-ttu-id="d8603-221">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-221">Parameter Name</span></span>|<span data-ttu-id="d8603-222">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-222">Restriction Default</span></span>|<span data-ttu-id="d8603-223">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-224">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-225">VIEW_CATALOG</span></span>|<span data-ttu-id="d8603-226">1</span><span class="sxs-lookup"><span data-stu-id="d8603-226">1</span></span>|  
|<span data-ttu-id="d8603-227">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-227">Owner</span></span>|@Owner|<span data-ttu-id="d8603-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="d8603-229">2</span><span class="sxs-lookup"><span data-stu-id="d8603-229">2</span></span>|  
|<span data-ttu-id="d8603-230">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-230">Table</span></span>|@Table|<span data-ttu-id="d8603-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-231">VIEW_NAME</span></span>|<span data-ttu-id="d8603-232">3</span><span class="sxs-lookup"><span data-stu-id="d8603-232">3</span></span>|  
|<span data-ttu-id="d8603-233">Sloupec</span><span class="sxs-lookup"><span data-stu-id="d8603-233">Column</span></span>|@Column|<span data-ttu-id="d8603-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-234">COLUMN_NAME</span></span>|<span data-ttu-id="d8603-235">4</span><span class="sxs-lookup"><span data-stu-id="d8603-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="d8603-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d8603-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="d8603-237">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-237">Restriction Name</span></span>|<span data-ttu-id="d8603-238">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-238">Parameter Name</span></span>|<span data-ttu-id="d8603-239">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-239">Restriction Default</span></span>|<span data-ttu-id="d8603-240">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-241">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="d8603-243">1</span><span class="sxs-lookup"><span data-stu-id="d8603-243">1</span></span>|  
|<span data-ttu-id="d8603-244">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-244">Owner</span></span>|@Owner|<span data-ttu-id="d8603-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="d8603-246">2</span><span class="sxs-lookup"><span data-stu-id="d8603-246">2</span></span>|  
|<span data-ttu-id="d8603-247">Name</span><span class="sxs-lookup"><span data-stu-id="d8603-247">Name</span></span>|@Name|<span data-ttu-id="d8603-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="d8603-249">3</span><span class="sxs-lookup"><span data-stu-id="d8603-249">3</span></span>|  
|<span data-ttu-id="d8603-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="d8603-250">Parameter</span></span>|@Parameter|<span data-ttu-id="d8603-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-251">PARAMETER_NAME</span></span>|<span data-ttu-id="d8603-252">4</span><span class="sxs-lookup"><span data-stu-id="d8603-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d8603-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="d8603-253">Procedures</span></span>  
  
|<span data-ttu-id="d8603-254">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-254">Restriction Name</span></span>|<span data-ttu-id="d8603-255">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-255">Parameter Name</span></span>|<span data-ttu-id="d8603-256">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-256">Restriction Default</span></span>|<span data-ttu-id="d8603-257">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-258">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="d8603-260">1</span><span class="sxs-lookup"><span data-stu-id="d8603-260">1</span></span>|  
|<span data-ttu-id="d8603-261">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-261">Owner</span></span>|@Owner|<span data-ttu-id="d8603-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="d8603-263">2</span><span class="sxs-lookup"><span data-stu-id="d8603-263">2</span></span>|  
|<span data-ttu-id="d8603-264">Name</span><span class="sxs-lookup"><span data-stu-id="d8603-264">Name</span></span>|@Name|<span data-ttu-id="d8603-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="d8603-266">3</span><span class="sxs-lookup"><span data-stu-id="d8603-266">3</span></span>|  
|<span data-ttu-id="d8603-267">type</span><span class="sxs-lookup"><span data-stu-id="d8603-267">Type</span></span>|@Type|<span data-ttu-id="d8603-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d8603-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="d8603-269">4</span><span class="sxs-lookup"><span data-stu-id="d8603-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="d8603-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="d8603-270">IndexColumns</span></span>  
  
|<span data-ttu-id="d8603-271">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-271">Restriction Name</span></span>|<span data-ttu-id="d8603-272">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-272">Parameter Name</span></span>|<span data-ttu-id="d8603-273">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-273">Restriction Default</span></span>|<span data-ttu-id="d8603-274">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-275">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="d8603-276">db_name()</span></span>|<span data-ttu-id="d8603-277">1</span><span class="sxs-lookup"><span data-stu-id="d8603-277">1</span></span>|  
|<span data-ttu-id="d8603-278">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-278">Owner</span></span>|@Owner|<span data-ttu-id="d8603-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="d8603-279">user_name()</span></span>|<span data-ttu-id="d8603-280">2</span><span class="sxs-lookup"><span data-stu-id="d8603-280">2</span></span>|  
|<span data-ttu-id="d8603-281">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-281">Table</span></span>|@Table|<span data-ttu-id="d8603-282">o.name</span><span class="sxs-lookup"><span data-stu-id="d8603-282">o.name</span></span>|<span data-ttu-id="d8603-283">3</span><span class="sxs-lookup"><span data-stu-id="d8603-283">3</span></span>|  
|<span data-ttu-id="d8603-284">Omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="d8603-285">x.name</span><span class="sxs-lookup"><span data-stu-id="d8603-285">x.name</span></span>|<span data-ttu-id="d8603-286">4</span><span class="sxs-lookup"><span data-stu-id="d8603-286">4</span></span>|  
|<span data-ttu-id="d8603-287">Sloupec</span><span class="sxs-lookup"><span data-stu-id="d8603-287">Column</span></span>|@Column|<span data-ttu-id="d8603-288">c.name</span><span class="sxs-lookup"><span data-stu-id="d8603-288">c.name</span></span>|<span data-ttu-id="d8603-289">5</span><span class="sxs-lookup"><span data-stu-id="d8603-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d8603-290">Indexy</span><span class="sxs-lookup"><span data-stu-id="d8603-290">Indexes</span></span>  
  
|<span data-ttu-id="d8603-291">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-291">Restriction Name</span></span>|<span data-ttu-id="d8603-292">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-292">Parameter Name</span></span>|<span data-ttu-id="d8603-293">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-293">Restriction Default</span></span>|<span data-ttu-id="d8603-294">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-295">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="d8603-296">db_name()</span></span>|<span data-ttu-id="d8603-297">1</span><span class="sxs-lookup"><span data-stu-id="d8603-297">1</span></span>|  
|<span data-ttu-id="d8603-298">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-298">Owner</span></span>|@Owner|<span data-ttu-id="d8603-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="d8603-299">user_name()</span></span>|<span data-ttu-id="d8603-300">2</span><span class="sxs-lookup"><span data-stu-id="d8603-300">2</span></span>|  
|<span data-ttu-id="d8603-301">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-301">Table</span></span>|@Table|<span data-ttu-id="d8603-302">o.name</span><span class="sxs-lookup"><span data-stu-id="d8603-302">o.name</span></span>|<span data-ttu-id="d8603-303">3</span><span class="sxs-lookup"><span data-stu-id="d8603-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="d8603-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="d8603-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="d8603-305">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-305">Restriction Name</span></span>|<span data-ttu-id="d8603-306">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-306">Parameter Name</span></span>|<span data-ttu-id="d8603-307">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-307">Restriction Default</span></span>|<span data-ttu-id="d8603-308">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="d8603-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="d8603-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="d8603-310">assemblies.name</span></span>|<span data-ttu-id="d8603-311">1</span><span class="sxs-lookup"><span data-stu-id="d8603-311">1</span></span>|  
|<span data-ttu-id="d8603-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="d8603-312">udt_name</span></span>|@UDTName|<span data-ttu-id="d8603-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="d8603-313">types.assembly_class</span></span>|<span data-ttu-id="d8603-314">2</span><span class="sxs-lookup"><span data-stu-id="d8603-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="d8603-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="d8603-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="d8603-316">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-316">Restriction Name</span></span>|<span data-ttu-id="d8603-317">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-317">Parameter Name</span></span>|<span data-ttu-id="d8603-318">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-318">Restriction Default</span></span>|<span data-ttu-id="d8603-319">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-320">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="d8603-322">1</span><span class="sxs-lookup"><span data-stu-id="d8603-322">1</span></span>|  
|<span data-ttu-id="d8603-323">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-323">Owner</span></span>|@Owner|<span data-ttu-id="d8603-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="d8603-325">2</span><span class="sxs-lookup"><span data-stu-id="d8603-325">2</span></span>|  
|<span data-ttu-id="d8603-326">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-326">Table</span></span>|@Table|<span data-ttu-id="d8603-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-327">TABLE_NAME</span></span>|<span data-ttu-id="d8603-328">3</span><span class="sxs-lookup"><span data-stu-id="d8603-328">3</span></span>|  
|<span data-ttu-id="d8603-329">Name</span><span class="sxs-lookup"><span data-stu-id="d8603-329">Name</span></span>|@Name|<span data-ttu-id="d8603-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="d8603-331">4</span><span class="sxs-lookup"><span data-stu-id="d8603-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="d8603-332">SQL Server 2008 Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="d8603-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="d8603-333">V následujících tabulkách jsou uvedeny omezení pro kolekce schémat SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="d8603-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="d8603-334">Tato omezení platí od verze 3,5 SP1 .NET Framework a SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="d8603-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="d8603-335">Nejsou podporované v dřívějších verzích .NET Framework a SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d8603-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="d8603-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="d8603-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="d8603-337">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-337">Restriction Name</span></span>|<span data-ttu-id="d8603-338">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-338">Parameter Name</span></span>|<span data-ttu-id="d8603-339">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-339">Restriction Default</span></span>|<span data-ttu-id="d8603-340">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-341">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-342">TABLE_CATALOG</span></span>|<span data-ttu-id="d8603-343">1</span><span class="sxs-lookup"><span data-stu-id="d8603-343">1</span></span>|  
|<span data-ttu-id="d8603-344">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-344">Owner</span></span>|@Owner|<span data-ttu-id="d8603-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8603-346">2</span><span class="sxs-lookup"><span data-stu-id="d8603-346">2</span></span>|  
|<span data-ttu-id="d8603-347">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-347">Table</span></span>|@Table|<span data-ttu-id="d8603-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-348">TABLE_NAME</span></span>|<span data-ttu-id="d8603-349">3</span><span class="sxs-lookup"><span data-stu-id="d8603-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="d8603-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="d8603-350">AllColumns</span></span>  
  
|<span data-ttu-id="d8603-351">Název omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-351">Restriction Name</span></span>|<span data-ttu-id="d8603-352">Název parametru</span><span class="sxs-lookup"><span data-stu-id="d8603-352">Parameter Name</span></span>|<span data-ttu-id="d8603-353">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-353">Restriction Default</span></span>|<span data-ttu-id="d8603-354">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="d8603-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d8603-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="d8603-355">Catalog</span></span>|@Catalog|<span data-ttu-id="d8603-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d8603-356">TABLE_CATALOG</span></span>|<span data-ttu-id="d8603-357">1</span><span class="sxs-lookup"><span data-stu-id="d8603-357">1</span></span>|  
|<span data-ttu-id="d8603-358">Owner</span><span class="sxs-lookup"><span data-stu-id="d8603-358">Owner</span></span>|@Owner|<span data-ttu-id="d8603-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d8603-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="d8603-360">2</span><span class="sxs-lookup"><span data-stu-id="d8603-360">2</span></span>|  
|<span data-ttu-id="d8603-361">Tabulka</span><span class="sxs-lookup"><span data-stu-id="d8603-361">Table</span></span>|@Table|<span data-ttu-id="d8603-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-362">TABLE_NAME</span></span>|<span data-ttu-id="d8603-363">3</span><span class="sxs-lookup"><span data-stu-id="d8603-363">3</span></span>|  
|<span data-ttu-id="d8603-364">Sloupec</span><span class="sxs-lookup"><span data-stu-id="d8603-364">Column</span></span>|@Column|<span data-ttu-id="d8603-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d8603-365">COLUMN_NAME</span></span>|<span data-ttu-id="d8603-366">4</span><span class="sxs-lookup"><span data-stu-id="d8603-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8603-367">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8603-367">See also</span></span>

- [<span data-ttu-id="d8603-368">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="d8603-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
