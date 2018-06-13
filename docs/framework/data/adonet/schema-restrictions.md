---
title: Omezení schématu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c62f934561fa4a6c352ff84b8c1201461c42de39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357254"
---
# <a name="schema-restrictions"></a><span data-ttu-id="f1524-102">Omezení schématu</span><span class="sxs-lookup"><span data-stu-id="f1524-102">Schema Restrictions</span></span>
<span data-ttu-id="f1524-103">Druhý parametr volitelný **GetSchema** je metoda vrátí omezení, které se používají k omezení množství informací o schématu, a je předán **GetSchema** metoda jako pole řetězců. .</span><span class="sxs-lookup"><span data-stu-id="f1524-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="f1524-104">Určuje pozici v poli hodnoty, které můžete předat a jde o ekvivalent číslo omezení.</span><span class="sxs-lookup"><span data-stu-id="f1524-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="f1524-105">Například následující tabulka popisuje omezení kolekcí schémat "Tabulky" pomocí zprostředkovatele dat .NET Framework pro SQL Server podporován.</span><span class="sxs-lookup"><span data-stu-id="f1524-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="f1524-106">Další omezení pro kolekce schématu systému SQL Server je uvedený na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f1524-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="f1524-107">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-107">Restriction Name</span></span>|<span data-ttu-id="f1524-108">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-108">Parameter Name</span></span>|<span data-ttu-id="f1524-109">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-109">Restriction Default</span></span>|<span data-ttu-id="f1524-110">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-111">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-111">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-112">TABLE_CATALOG</span></span>|<span data-ttu-id="f1524-113">1</span><span class="sxs-lookup"><span data-stu-id="f1524-113">1</span></span>|  
|<span data-ttu-id="f1524-114">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-114">Owner</span></span>|@Owner|<span data-ttu-id="f1524-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="f1524-116">2</span><span class="sxs-lookup"><span data-stu-id="f1524-116">2</span></span>|  
|<span data-ttu-id="f1524-117">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-117">Table</span></span>|@Name|<span data-ttu-id="f1524-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-118">TABLE_NAME</span></span>|<span data-ttu-id="f1524-119">3</span><span class="sxs-lookup"><span data-stu-id="f1524-119">3</span></span>|  
|<span data-ttu-id="f1524-120">TableType</span><span class="sxs-lookup"><span data-stu-id="f1524-120">TableType</span></span>|@TableType|<span data-ttu-id="f1524-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1524-121">TABLE_TYPE</span></span>|<span data-ttu-id="f1524-122">4</span><span class="sxs-lookup"><span data-stu-id="f1524-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="f1524-123">Zadání hodnoty omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="f1524-124">Použít jednu z omezení kolekce schémat "Tabulky", stačí vytvořit pole řetězců se čtyřmi prvky a pak umístit hodnotu elementu, který odpovídá číslu omezení.</span><span class="sxs-lookup"><span data-stu-id="f1524-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="f1524-125">Například k omezení tabulky vrácený **GetSchema** metodu pouze ty tabulky ve schématu "Prodej", nastavte druhý prvkem pole na "Prodej" před předáním na **GetSchema** metoda.</span><span class="sxs-lookup"><span data-stu-id="f1524-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1524-126">Omezení kolekce pro `SqlClient` a `OracleClient` mají další `ParameterName` sloupce.</span><span class="sxs-lookup"><span data-stu-id="f1524-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="f1524-127">Výchozí sloupec omezení je stále existuje pro zpětnou kompatibilitu, ale je aktuálně ignorována.</span><span class="sxs-lookup"><span data-stu-id="f1524-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="f1524-128">Parametrizované dotazy a nikoli náhradní řetězce se má použít k minimalizovat riziko útoku vkládání SQL při zadání hodnoty omezení.</span><span class="sxs-lookup"><span data-stu-id="f1524-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1524-129">Počet prvků v poli musí být menší než nebo rovna počtu omezení, která jsou podporována pro jiný určené schéma kolekce <xref:System.ArgumentException> bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f1524-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="f1524-130">Může být menší než maximální počet omezení.</span><span class="sxs-lookup"><span data-stu-id="f1524-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="f1524-131">Chybějící omezení se předpokládá, že mít hodnotu null (bez omezení).</span><span class="sxs-lookup"><span data-stu-id="f1524-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="f1524-132">Můžete zadat dotaz rozhraní .NET Framework spravovaného zprostředkovatele určit seznam podporovaných omezení voláním **GetSchema** metoda s názvem kolekce schémat omezení, což je "Omezení".</span><span class="sxs-lookup"><span data-stu-id="f1524-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="f1524-133">Tato možnost vrátí <xref:System.Data.DataTable> se seznamem názvů kolekcí, názvy omezení, výchozí hodnoty omezení a omezení čísla.</span><span class="sxs-lookup"><span data-stu-id="f1524-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f1524-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1524-134">Example</span></span>  
 <span data-ttu-id="f1524-135">Následující příklady ukazují, jak používat <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metoda zprostředkovatele dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> třída načíst informace o schématu o všechny tabulky obsažené v **AdventureWorks**ukázkové databáze, a omezit informace vrátí pouze ty tabulky "Prodeje" schématu:</span><span class="sxs-lookup"><span data-stu-id="f1524-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="f1524-136">SQL Server schématu omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="f1524-137">V následujících tabulkách najdete omezení pro kolekce schématu systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f1524-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="f1524-138">Uživatelé</span><span class="sxs-lookup"><span data-stu-id="f1524-138">Users</span></span>  
  
|<span data-ttu-id="f1524-139">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-139">Restriction Name</span></span>|<span data-ttu-id="f1524-140">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-140">Parameter Name</span></span>|<span data-ttu-id="f1524-141">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-141">Restriction Default</span></span>|<span data-ttu-id="f1524-142">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-143">Uživatelské_jméno</span><span class="sxs-lookup"><span data-stu-id="f1524-143">User_Name</span></span>|@Name|<span data-ttu-id="f1524-144">name</span><span class="sxs-lookup"><span data-stu-id="f1524-144">name</span></span>|<span data-ttu-id="f1524-145">1</span><span class="sxs-lookup"><span data-stu-id="f1524-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="f1524-146">Databáze</span><span class="sxs-lookup"><span data-stu-id="f1524-146">Databases</span></span>  
  
|<span data-ttu-id="f1524-147">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-147">Restriction Name</span></span>|<span data-ttu-id="f1524-148">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-148">Parameter Name</span></span>|<span data-ttu-id="f1524-149">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-149">Restriction Default</span></span>|<span data-ttu-id="f1524-150">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-151">Název</span><span class="sxs-lookup"><span data-stu-id="f1524-151">Name</span></span>|@Name|<span data-ttu-id="f1524-152">Název</span><span class="sxs-lookup"><span data-stu-id="f1524-152">Name</span></span>|<span data-ttu-id="f1524-153">1</span><span class="sxs-lookup"><span data-stu-id="f1524-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="f1524-154">Tabulky</span><span class="sxs-lookup"><span data-stu-id="f1524-154">Tables</span></span>  
  
|<span data-ttu-id="f1524-155">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-155">Restriction Name</span></span>|<span data-ttu-id="f1524-156">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-156">Parameter Name</span></span>|<span data-ttu-id="f1524-157">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-157">Restriction Default</span></span>|<span data-ttu-id="f1524-158">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-159">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-159">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-160">TABLE_CATALOG</span></span>|<span data-ttu-id="f1524-161">1</span><span class="sxs-lookup"><span data-stu-id="f1524-161">1</span></span>|  
|<span data-ttu-id="f1524-162">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-162">Owner</span></span>|@Owner|<span data-ttu-id="f1524-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="f1524-164">2</span><span class="sxs-lookup"><span data-stu-id="f1524-164">2</span></span>|  
|<span data-ttu-id="f1524-165">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-165">Table</span></span>|@Name|<span data-ttu-id="f1524-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-166">TABLE_NAME</span></span>|<span data-ttu-id="f1524-167">3</span><span class="sxs-lookup"><span data-stu-id="f1524-167">3</span></span>|  
|<span data-ttu-id="f1524-168">TableType</span><span class="sxs-lookup"><span data-stu-id="f1524-168">TableType</span></span>|@TableType|<span data-ttu-id="f1524-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1524-169">TABLE_TYPE</span></span>|<span data-ttu-id="f1524-170">4</span><span class="sxs-lookup"><span data-stu-id="f1524-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f1524-171">Sloupce</span><span class="sxs-lookup"><span data-stu-id="f1524-171">Columns</span></span>  
  
|<span data-ttu-id="f1524-172">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-172">Restriction Name</span></span>|<span data-ttu-id="f1524-173">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-173">Parameter Name</span></span>|<span data-ttu-id="f1524-174">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-174">Restriction Default</span></span>|<span data-ttu-id="f1524-175">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-176">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-176">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-177">TABLE_CATALOG</span></span>|<span data-ttu-id="f1524-178">1</span><span class="sxs-lookup"><span data-stu-id="f1524-178">1</span></span>|  
|<span data-ttu-id="f1524-179">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-179">Owner</span></span>|@Owner|<span data-ttu-id="f1524-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="f1524-181">2</span><span class="sxs-lookup"><span data-stu-id="f1524-181">2</span></span>|  
|<span data-ttu-id="f1524-182">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-182">Table</span></span>|@Table|<span data-ttu-id="f1524-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-183">TABLE_NAME</span></span>|<span data-ttu-id="f1524-184">3</span><span class="sxs-lookup"><span data-stu-id="f1524-184">3</span></span>|  
|<span data-ttu-id="f1524-185">Sloupec</span><span class="sxs-lookup"><span data-stu-id="f1524-185">Column</span></span>|@Column|<span data-ttu-id="f1524-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-186">COLUMN_NAME</span></span>|<span data-ttu-id="f1524-187">4</span><span class="sxs-lookup"><span data-stu-id="f1524-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="f1524-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="f1524-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="f1524-189">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-189">Restriction Name</span></span>|<span data-ttu-id="f1524-190">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-190">Parameter Name</span></span>|<span data-ttu-id="f1524-191">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-191">Restriction Default</span></span>|<span data-ttu-id="f1524-192">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-193">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-193">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-194">TABLE_CATALOG</span></span>|<span data-ttu-id="f1524-195">1</span><span class="sxs-lookup"><span data-stu-id="f1524-195">1</span></span>|  
|<span data-ttu-id="f1524-196">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-196">Owner</span></span>|@Owner|<span data-ttu-id="f1524-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="f1524-198">2</span><span class="sxs-lookup"><span data-stu-id="f1524-198">2</span></span>|  
|<span data-ttu-id="f1524-199">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-199">Table</span></span>|@Table|<span data-ttu-id="f1524-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-200">TABLE_NAME</span></span>|<span data-ttu-id="f1524-201">3</span><span class="sxs-lookup"><span data-stu-id="f1524-201">3</span></span>|  
|<span data-ttu-id="f1524-202">Sloupec</span><span class="sxs-lookup"><span data-stu-id="f1524-202">Column</span></span>|@Column|<span data-ttu-id="f1524-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-203">COLUMN_NAME</span></span>|<span data-ttu-id="f1524-204">4</span><span class="sxs-lookup"><span data-stu-id="f1524-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="f1524-205">zobrazení</span><span class="sxs-lookup"><span data-stu-id="f1524-205">Views</span></span>  
  
|<span data-ttu-id="f1524-206">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-206">Restriction Name</span></span>|<span data-ttu-id="f1524-207">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-207">Parameter Name</span></span>|<span data-ttu-id="f1524-208">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-208">Restriction Default</span></span>|<span data-ttu-id="f1524-209">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-210">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-210">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-211">TABLE_CATALOG</span></span>|<span data-ttu-id="f1524-212">1</span><span class="sxs-lookup"><span data-stu-id="f1524-212">1</span></span>|  
|<span data-ttu-id="f1524-213">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-213">Owner</span></span>|@Owner|<span data-ttu-id="f1524-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="f1524-215">2</span><span class="sxs-lookup"><span data-stu-id="f1524-215">2</span></span>|  
|<span data-ttu-id="f1524-216">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-216">Table</span></span>|@Table|<span data-ttu-id="f1524-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-217">TABLE_NAME</span></span>|<span data-ttu-id="f1524-218">3</span><span class="sxs-lookup"><span data-stu-id="f1524-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="f1524-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="f1524-219">ViewColumns</span></span>  
  
|<span data-ttu-id="f1524-220">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-220">Restriction Name</span></span>|<span data-ttu-id="f1524-221">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-221">Parameter Name</span></span>|<span data-ttu-id="f1524-222">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-222">Restriction Default</span></span>|<span data-ttu-id="f1524-223">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-224">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-224">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-225">VIEW_CATALOG</span></span>|<span data-ttu-id="f1524-226">1</span><span class="sxs-lookup"><span data-stu-id="f1524-226">1</span></span>|  
|<span data-ttu-id="f1524-227">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-227">Owner</span></span>|@Owner|<span data-ttu-id="f1524-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="f1524-229">2</span><span class="sxs-lookup"><span data-stu-id="f1524-229">2</span></span>|  
|<span data-ttu-id="f1524-230">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-230">Table</span></span>|@Table|<span data-ttu-id="f1524-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-231">VIEW_NAME</span></span>|<span data-ttu-id="f1524-232">3</span><span class="sxs-lookup"><span data-stu-id="f1524-232">3</span></span>|  
|<span data-ttu-id="f1524-233">Sloupec</span><span class="sxs-lookup"><span data-stu-id="f1524-233">Column</span></span>|@Column|<span data-ttu-id="f1524-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-234">COLUMN_NAME</span></span>|<span data-ttu-id="f1524-235">4</span><span class="sxs-lookup"><span data-stu-id="f1524-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f1524-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f1524-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f1524-237">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-237">Restriction Name</span></span>|<span data-ttu-id="f1524-238">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-238">Parameter Name</span></span>|<span data-ttu-id="f1524-239">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-239">Restriction Default</span></span>|<span data-ttu-id="f1524-240">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-241">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-241">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="f1524-243">1</span><span class="sxs-lookup"><span data-stu-id="f1524-243">1</span></span>|  
|<span data-ttu-id="f1524-244">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-244">Owner</span></span>|@Owner|<span data-ttu-id="f1524-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="f1524-246">2</span><span class="sxs-lookup"><span data-stu-id="f1524-246">2</span></span>|  
|<span data-ttu-id="f1524-247">Název</span><span class="sxs-lookup"><span data-stu-id="f1524-247">Name</span></span>|@Name|<span data-ttu-id="f1524-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="f1524-249">3</span><span class="sxs-lookup"><span data-stu-id="f1524-249">3</span></span>|  
|<span data-ttu-id="f1524-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="f1524-250">Parameter</span></span>|@Parameter|<span data-ttu-id="f1524-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-251">PARAMETER_NAME</span></span>|<span data-ttu-id="f1524-252">4</span><span class="sxs-lookup"><span data-stu-id="f1524-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f1524-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="f1524-253">Procedures</span></span>  
  
|<span data-ttu-id="f1524-254">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-254">Restriction Name</span></span>|<span data-ttu-id="f1524-255">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-255">Parameter Name</span></span>|<span data-ttu-id="f1524-256">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-256">Restriction Default</span></span>|<span data-ttu-id="f1524-257">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-258">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="f1524-260">1</span><span class="sxs-lookup"><span data-stu-id="f1524-260">1</span></span>|  
|<span data-ttu-id="f1524-261">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-261">Owner</span></span>|@Owner|<span data-ttu-id="f1524-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="f1524-263">2</span><span class="sxs-lookup"><span data-stu-id="f1524-263">2</span></span>|  
|<span data-ttu-id="f1524-264">Název</span><span class="sxs-lookup"><span data-stu-id="f1524-264">Name</span></span>|@Name|<span data-ttu-id="f1524-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="f1524-266">3</span><span class="sxs-lookup"><span data-stu-id="f1524-266">3</span></span>|  
|<span data-ttu-id="f1524-267">Typ</span><span class="sxs-lookup"><span data-stu-id="f1524-267">Type</span></span>|@Type|<span data-ttu-id="f1524-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1524-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="f1524-269">4</span><span class="sxs-lookup"><span data-stu-id="f1524-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="f1524-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="f1524-270">IndexColumns</span></span>  
  
|<span data-ttu-id="f1524-271">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-271">Restriction Name</span></span>|<span data-ttu-id="f1524-272">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-272">Parameter Name</span></span>|<span data-ttu-id="f1524-273">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-273">Restriction Default</span></span>|<span data-ttu-id="f1524-274">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-275">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-275">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="f1524-276">db_name()</span></span>|<span data-ttu-id="f1524-277">1</span><span class="sxs-lookup"><span data-stu-id="f1524-277">1</span></span>|  
|<span data-ttu-id="f1524-278">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-278">Owner</span></span>|@Owner|<span data-ttu-id="f1524-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="f1524-279">user_name()</span></span>|<span data-ttu-id="f1524-280">2</span><span class="sxs-lookup"><span data-stu-id="f1524-280">2</span></span>|  
|<span data-ttu-id="f1524-281">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-281">Table</span></span>|@Table|<span data-ttu-id="f1524-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="f1524-282">o.name</span></span>|<span data-ttu-id="f1524-283">3</span><span class="sxs-lookup"><span data-stu-id="f1524-283">3</span></span>|  
|<span data-ttu-id="f1524-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="f1524-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="f1524-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="f1524-285">x.name</span></span>|<span data-ttu-id="f1524-286">4</span><span class="sxs-lookup"><span data-stu-id="f1524-286">4</span></span>|  
|<span data-ttu-id="f1524-287">Sloupec</span><span class="sxs-lookup"><span data-stu-id="f1524-287">Column</span></span>|@Column|<span data-ttu-id="f1524-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="f1524-288">c.name</span></span>|<span data-ttu-id="f1524-289">5</span><span class="sxs-lookup"><span data-stu-id="f1524-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f1524-290">Indexy</span><span class="sxs-lookup"><span data-stu-id="f1524-290">Indexes</span></span>  
  
|<span data-ttu-id="f1524-291">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-291">Restriction Name</span></span>|<span data-ttu-id="f1524-292">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-292">Parameter Name</span></span>|<span data-ttu-id="f1524-293">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-293">Restriction Default</span></span>|<span data-ttu-id="f1524-294">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-295">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-295">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="f1524-296">db_name()</span></span>|<span data-ttu-id="f1524-297">1</span><span class="sxs-lookup"><span data-stu-id="f1524-297">1</span></span>|  
|<span data-ttu-id="f1524-298">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-298">Owner</span></span>|@Owner|<span data-ttu-id="f1524-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="f1524-299">user_name()</span></span>|<span data-ttu-id="f1524-300">2</span><span class="sxs-lookup"><span data-stu-id="f1524-300">2</span></span>|  
|<span data-ttu-id="f1524-301">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-301">Table</span></span>|@Table|<span data-ttu-id="f1524-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="f1524-302">o.name</span></span>|<span data-ttu-id="f1524-303">3</span><span class="sxs-lookup"><span data-stu-id="f1524-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="f1524-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="f1524-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="f1524-305">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-305">Restriction Name</span></span>|<span data-ttu-id="f1524-306">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-306">Parameter Name</span></span>|<span data-ttu-id="f1524-307">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-307">Restriction Default</span></span>|<span data-ttu-id="f1524-308">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="f1524-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="f1524-310">Assemblies.Name</span><span class="sxs-lookup"><span data-stu-id="f1524-310">assemblies.name</span></span>|<span data-ttu-id="f1524-311">1</span><span class="sxs-lookup"><span data-stu-id="f1524-311">1</span></span>|  
|<span data-ttu-id="f1524-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="f1524-312">udt_name</span></span>|@UDTName|<span data-ttu-id="f1524-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="f1524-313">types.assembly_class</span></span>|<span data-ttu-id="f1524-314">2</span><span class="sxs-lookup"><span data-stu-id="f1524-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="f1524-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="f1524-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="f1524-316">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-316">Restriction Name</span></span>|<span data-ttu-id="f1524-317">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-317">Parameter Name</span></span>|<span data-ttu-id="f1524-318">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-318">Restriction Default</span></span>|<span data-ttu-id="f1524-319">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-320">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-320">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="f1524-322">1</span><span class="sxs-lookup"><span data-stu-id="f1524-322">1</span></span>|  
|<span data-ttu-id="f1524-323">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-323">Owner</span></span>|@Owner|<span data-ttu-id="f1524-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="f1524-325">2</span><span class="sxs-lookup"><span data-stu-id="f1524-325">2</span></span>|  
|<span data-ttu-id="f1524-326">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-326">Table</span></span>|@Table|<span data-ttu-id="f1524-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-327">TABLE_NAME</span></span>|<span data-ttu-id="f1524-328">3</span><span class="sxs-lookup"><span data-stu-id="f1524-328">3</span></span>|  
|<span data-ttu-id="f1524-329">Název</span><span class="sxs-lookup"><span data-stu-id="f1524-329">Name</span></span>|@Name|<span data-ttu-id="f1524-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="f1524-331">4</span><span class="sxs-lookup"><span data-stu-id="f1524-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="f1524-332">SQL Server 2008 Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="f1524-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="f1524-333">V následujících tabulkách najdete omezení pro SQL Server 2008 kolekcemi schémat.</span><span class="sxs-lookup"><span data-stu-id="f1524-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="f1524-334">Tato omezení jsou platné od verze verze systému SQL Server 2008 a rozhraní .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="f1524-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="f1524-335">Nejsou podporovány v dřívějších verzích rozhraní .NET Framework a SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f1524-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="f1524-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="f1524-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="f1524-337">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-337">Restriction Name</span></span>|<span data-ttu-id="f1524-338">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-338">Parameter Name</span></span>|<span data-ttu-id="f1524-339">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-339">Restriction Default</span></span>|<span data-ttu-id="f1524-340">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-341">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-341">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-342">TABLE_CATALOG</span></span>|<span data-ttu-id="f1524-343">1</span><span class="sxs-lookup"><span data-stu-id="f1524-343">1</span></span>|  
|<span data-ttu-id="f1524-344">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-344">Owner</span></span>|@Owner|<span data-ttu-id="f1524-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="f1524-346">2</span><span class="sxs-lookup"><span data-stu-id="f1524-346">2</span></span>|  
|<span data-ttu-id="f1524-347">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-347">Table</span></span>|@Table|<span data-ttu-id="f1524-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-348">TABLE_NAME</span></span>|<span data-ttu-id="f1524-349">3</span><span class="sxs-lookup"><span data-stu-id="f1524-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="f1524-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="f1524-350">AllColumns</span></span>  
  
|<span data-ttu-id="f1524-351">Název omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-351">Restriction Name</span></span>|<span data-ttu-id="f1524-352">Název parametru</span><span class="sxs-lookup"><span data-stu-id="f1524-352">Parameter Name</span></span>|<span data-ttu-id="f1524-353">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-353">Restriction Default</span></span>|<span data-ttu-id="f1524-354">Počet omezení</span><span class="sxs-lookup"><span data-stu-id="f1524-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f1524-355">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f1524-355">Catalog</span></span>|@Catalog|<span data-ttu-id="f1524-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1524-356">TABLE_CATALOG</span></span>|<span data-ttu-id="f1524-357">1</span><span class="sxs-lookup"><span data-stu-id="f1524-357">1</span></span>|  
|<span data-ttu-id="f1524-358">Vlastník</span><span class="sxs-lookup"><span data-stu-id="f1524-358">Owner</span></span>|@Owner|<span data-ttu-id="f1524-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1524-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="f1524-360">2</span><span class="sxs-lookup"><span data-stu-id="f1524-360">2</span></span>|  
|<span data-ttu-id="f1524-361">Tabulka</span><span class="sxs-lookup"><span data-stu-id="f1524-361">Table</span></span>|@Table|<span data-ttu-id="f1524-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-362">TABLE_NAME</span></span>|<span data-ttu-id="f1524-363">3</span><span class="sxs-lookup"><span data-stu-id="f1524-363">3</span></span>|  
|<span data-ttu-id="f1524-364">Sloupec</span><span class="sxs-lookup"><span data-stu-id="f1524-364">Column</span></span>|@Column|<span data-ttu-id="f1524-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1524-365">COLUMN_NAME</span></span>|<span data-ttu-id="f1524-366">4</span><span class="sxs-lookup"><span data-stu-id="f1524-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1524-367">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1524-367">See Also</span></span>  
 [<span data-ttu-id="f1524-368">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="f1524-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
