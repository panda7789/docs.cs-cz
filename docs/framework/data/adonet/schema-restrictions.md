---
title: Omezení schématu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: b5044d39d1dc5d2fa7d2ce691cdda7075fa0e32a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878407"
---
# <a name="schema-restrictions"></a><span data-ttu-id="e2705-102">Omezení schématu</span><span class="sxs-lookup"><span data-stu-id="e2705-102">Schema Restrictions</span></span>
<span data-ttu-id="e2705-103">Druhý volitelný parametr **GetSchema** metoda je vrácena omezení, které se používají a omezit tak množství informací o schématu, a je předán **GetSchema** metody jako pole řetězců .</span><span class="sxs-lookup"><span data-stu-id="e2705-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="e2705-104">Pozice v poli určuje hodnoty, které můžete předat, a to je ekvivalentní hodnotě parametru omezení.</span><span class="sxs-lookup"><span data-stu-id="e2705-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="e2705-105">Například následující tabulka popisuje omezení kolekcí schémat "Tabulky" pomocí zprostředkovatele dat .NET Framework pro SQL Server podporován.</span><span class="sxs-lookup"><span data-stu-id="e2705-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="e2705-106">Další omezení kolekce schémat SQL Server jsou uvedeny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e2705-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="e2705-107">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-107">Restriction Name</span></span>|<span data-ttu-id="e2705-108">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-108">Parameter Name</span></span>|<span data-ttu-id="e2705-109">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-109">Restriction Default</span></span>|<span data-ttu-id="e2705-110">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-111">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-112">TABLE_CATALOG</span></span>|<span data-ttu-id="e2705-113">1</span><span class="sxs-lookup"><span data-stu-id="e2705-113">1</span></span>|  
|<span data-ttu-id="e2705-114">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-114">Owner</span></span>|@Owner|<span data-ttu-id="e2705-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="e2705-116">2</span><span class="sxs-lookup"><span data-stu-id="e2705-116">2</span></span>|  
|<span data-ttu-id="e2705-117">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-117">Table</span></span>|@Name|<span data-ttu-id="e2705-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-118">TABLE_NAME</span></span>|<span data-ttu-id="e2705-119">3</span><span class="sxs-lookup"><span data-stu-id="e2705-119">3</span></span>|  
|<span data-ttu-id="e2705-120">TableType</span><span class="sxs-lookup"><span data-stu-id="e2705-120">TableType</span></span>|@TableType|<span data-ttu-id="e2705-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e2705-121">TABLE_TYPE</span></span>|<span data-ttu-id="e2705-122">4</span><span class="sxs-lookup"><span data-stu-id="e2705-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="e2705-123">Určení hodnoty omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="e2705-124">Použijte jednu z těchto omezení kolekce schémat "Tabulky", jednoduše vytvořit pole řetězců, které se čtyřmi prvky a potom umístili hodnotu v elementu, který se shoduje s počtem omezení.</span><span class="sxs-lookup"><span data-stu-id="e2705-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="e2705-125">Například k omezení tabulky vrácené **GetSchema** metodu pouze tabulky ve schématu "Prodeje" nastavit druhý prvek pole, které chcete "Prodeje" před předáním do **GetSchema** metody.</span><span class="sxs-lookup"><span data-stu-id="e2705-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2705-126">Omezení kolekce pro `SqlClient` a `OracleClient` mají další `ParameterName` sloupce.</span><span class="sxs-lookup"><span data-stu-id="e2705-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="e2705-127">Výchozí sloupec omezení je stále pro zpětnou kompatibilitu, ale aktuálně je ignorována.</span><span class="sxs-lookup"><span data-stu-id="e2705-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="e2705-128">Chcete-li minimalizovat riziko útoků prostřednictvím injektáže SQL, při zadávání hodnoty omezení by měla sloužit parametrizovaných dotazů místo nahrazení řetězce.</span><span class="sxs-lookup"><span data-stu-id="e2705-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2705-129">Počet prvků v poli musí být menší nebo rovna počtu omezení pro ostatní zadané schéma kolekce nepodporuje <xref:System.ArgumentException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e2705-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="e2705-130">Může být méně než maximální počet omezení.</span><span class="sxs-lookup"><span data-stu-id="e2705-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="e2705-131">Chybí omezení jsou považován za hodnotu null (bez omezení).</span><span class="sxs-lookup"><span data-stu-id="e2705-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="e2705-132">Můžete dát dotaz na zprostředkovatele rozhraní .NET Framework spravované k určení seznamu podporovaných omezení voláním **GetSchema** metodu s názvem kolekce schémat omezení, což je "Omezení".</span><span class="sxs-lookup"><span data-stu-id="e2705-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="e2705-133">Vrátí <xref:System.Data.DataTable> seznam názvy kolekcí, omezení názvů, omezení výchozí hodnoty a omezení čísla.</span><span class="sxs-lookup"><span data-stu-id="e2705-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e2705-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2705-134">Example</span></span>  
 <span data-ttu-id="e2705-135">Následující příklady ukazují, jak používat <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metoda zprostředkovatele dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> třídy pro načtení schématu informace o všech tabulek, které jsou součástí **AdventureWorks**ukázková databáze a omezit informace vrátí pouze ty tabulky ve schématu "Prodeje":</span><span class="sxs-lookup"><span data-stu-id="e2705-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="e2705-136">Omezení schématu SQL serveru</span><span class="sxs-lookup"><span data-stu-id="e2705-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="e2705-137">Omezení pro kolekce schémat SQL Server naleznete v následujících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="e2705-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="e2705-138">Uživatelé</span><span class="sxs-lookup"><span data-stu-id="e2705-138">Users</span></span>  
  
|<span data-ttu-id="e2705-139">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-139">Restriction Name</span></span>|<span data-ttu-id="e2705-140">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-140">Parameter Name</span></span>|<span data-ttu-id="e2705-141">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-141">Restriction Default</span></span>|<span data-ttu-id="e2705-142">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-143">Uživatelské_jméno</span><span class="sxs-lookup"><span data-stu-id="e2705-143">User_Name</span></span>|@Name|<span data-ttu-id="e2705-144">name</span><span class="sxs-lookup"><span data-stu-id="e2705-144">name</span></span>|<span data-ttu-id="e2705-145">1</span><span class="sxs-lookup"><span data-stu-id="e2705-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="e2705-146">Databáze</span><span class="sxs-lookup"><span data-stu-id="e2705-146">Databases</span></span>  
  
|<span data-ttu-id="e2705-147">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-147">Restriction Name</span></span>|<span data-ttu-id="e2705-148">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-148">Parameter Name</span></span>|<span data-ttu-id="e2705-149">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-149">Restriction Default</span></span>|<span data-ttu-id="e2705-150">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-151">Název</span><span class="sxs-lookup"><span data-stu-id="e2705-151">Name</span></span>|@Name|<span data-ttu-id="e2705-152">Název</span><span class="sxs-lookup"><span data-stu-id="e2705-152">Name</span></span>|<span data-ttu-id="e2705-153">1</span><span class="sxs-lookup"><span data-stu-id="e2705-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="e2705-154">Tabulky</span><span class="sxs-lookup"><span data-stu-id="e2705-154">Tables</span></span>  
  
|<span data-ttu-id="e2705-155">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-155">Restriction Name</span></span>|<span data-ttu-id="e2705-156">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-156">Parameter Name</span></span>|<span data-ttu-id="e2705-157">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-157">Restriction Default</span></span>|<span data-ttu-id="e2705-158">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-159">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-160">TABLE_CATALOG</span></span>|<span data-ttu-id="e2705-161">1</span><span class="sxs-lookup"><span data-stu-id="e2705-161">1</span></span>|  
|<span data-ttu-id="e2705-162">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-162">Owner</span></span>|@Owner|<span data-ttu-id="e2705-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="e2705-164">2</span><span class="sxs-lookup"><span data-stu-id="e2705-164">2</span></span>|  
|<span data-ttu-id="e2705-165">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-165">Table</span></span>|@Name|<span data-ttu-id="e2705-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-166">TABLE_NAME</span></span>|<span data-ttu-id="e2705-167">3</span><span class="sxs-lookup"><span data-stu-id="e2705-167">3</span></span>|  
|<span data-ttu-id="e2705-168">TableType</span><span class="sxs-lookup"><span data-stu-id="e2705-168">TableType</span></span>|@TableType|<span data-ttu-id="e2705-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e2705-169">TABLE_TYPE</span></span>|<span data-ttu-id="e2705-170">4</span><span class="sxs-lookup"><span data-stu-id="e2705-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e2705-171">Sloupce</span><span class="sxs-lookup"><span data-stu-id="e2705-171">Columns</span></span>  
  
|<span data-ttu-id="e2705-172">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-172">Restriction Name</span></span>|<span data-ttu-id="e2705-173">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-173">Parameter Name</span></span>|<span data-ttu-id="e2705-174">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-174">Restriction Default</span></span>|<span data-ttu-id="e2705-175">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-176">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-177">TABLE_CATALOG</span></span>|<span data-ttu-id="e2705-178">1</span><span class="sxs-lookup"><span data-stu-id="e2705-178">1</span></span>|  
|<span data-ttu-id="e2705-179">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-179">Owner</span></span>|@Owner|<span data-ttu-id="e2705-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="e2705-181">2</span><span class="sxs-lookup"><span data-stu-id="e2705-181">2</span></span>|  
|<span data-ttu-id="e2705-182">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-182">Table</span></span>|@Table|<span data-ttu-id="e2705-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-183">TABLE_NAME</span></span>|<span data-ttu-id="e2705-184">3</span><span class="sxs-lookup"><span data-stu-id="e2705-184">3</span></span>|  
|<span data-ttu-id="e2705-185">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e2705-185">Column</span></span>|@Column|<span data-ttu-id="e2705-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-186">COLUMN_NAME</span></span>|<span data-ttu-id="e2705-187">4</span><span class="sxs-lookup"><span data-stu-id="e2705-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="e2705-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="e2705-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="e2705-189">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-189">Restriction Name</span></span>|<span data-ttu-id="e2705-190">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-190">Parameter Name</span></span>|<span data-ttu-id="e2705-191">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-191">Restriction Default</span></span>|<span data-ttu-id="e2705-192">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-193">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-194">TABLE_CATALOG</span></span>|<span data-ttu-id="e2705-195">1</span><span class="sxs-lookup"><span data-stu-id="e2705-195">1</span></span>|  
|<span data-ttu-id="e2705-196">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-196">Owner</span></span>|@Owner|<span data-ttu-id="e2705-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="e2705-198">2</span><span class="sxs-lookup"><span data-stu-id="e2705-198">2</span></span>|  
|<span data-ttu-id="e2705-199">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-199">Table</span></span>|@Table|<span data-ttu-id="e2705-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-200">TABLE_NAME</span></span>|<span data-ttu-id="e2705-201">3</span><span class="sxs-lookup"><span data-stu-id="e2705-201">3</span></span>|  
|<span data-ttu-id="e2705-202">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e2705-202">Column</span></span>|@Column|<span data-ttu-id="e2705-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-203">COLUMN_NAME</span></span>|<span data-ttu-id="e2705-204">4</span><span class="sxs-lookup"><span data-stu-id="e2705-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="e2705-205">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="e2705-205">Views</span></span>  
  
|<span data-ttu-id="e2705-206">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-206">Restriction Name</span></span>|<span data-ttu-id="e2705-207">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-207">Parameter Name</span></span>|<span data-ttu-id="e2705-208">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-208">Restriction Default</span></span>|<span data-ttu-id="e2705-209">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-210">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-211">TABLE_CATALOG</span></span>|<span data-ttu-id="e2705-212">1</span><span class="sxs-lookup"><span data-stu-id="e2705-212">1</span></span>|  
|<span data-ttu-id="e2705-213">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-213">Owner</span></span>|@Owner|<span data-ttu-id="e2705-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="e2705-215">2</span><span class="sxs-lookup"><span data-stu-id="e2705-215">2</span></span>|  
|<span data-ttu-id="e2705-216">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-216">Table</span></span>|@Table|<span data-ttu-id="e2705-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-217">TABLE_NAME</span></span>|<span data-ttu-id="e2705-218">3</span><span class="sxs-lookup"><span data-stu-id="e2705-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="e2705-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="e2705-219">ViewColumns</span></span>  
  
|<span data-ttu-id="e2705-220">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-220">Restriction Name</span></span>|<span data-ttu-id="e2705-221">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-221">Parameter Name</span></span>|<span data-ttu-id="e2705-222">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-222">Restriction Default</span></span>|<span data-ttu-id="e2705-223">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-224">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-225">VIEW_CATALOG</span></span>|<span data-ttu-id="e2705-226">1</span><span class="sxs-lookup"><span data-stu-id="e2705-226">1</span></span>|  
|<span data-ttu-id="e2705-227">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-227">Owner</span></span>|@Owner|<span data-ttu-id="e2705-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="e2705-229">2</span><span class="sxs-lookup"><span data-stu-id="e2705-229">2</span></span>|  
|<span data-ttu-id="e2705-230">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-230">Table</span></span>|@Table|<span data-ttu-id="e2705-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-231">VIEW_NAME</span></span>|<span data-ttu-id="e2705-232">3</span><span class="sxs-lookup"><span data-stu-id="e2705-232">3</span></span>|  
|<span data-ttu-id="e2705-233">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e2705-233">Column</span></span>|@Column|<span data-ttu-id="e2705-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-234">COLUMN_NAME</span></span>|<span data-ttu-id="e2705-235">4</span><span class="sxs-lookup"><span data-stu-id="e2705-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e2705-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e2705-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e2705-237">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-237">Restriction Name</span></span>|<span data-ttu-id="e2705-238">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-238">Parameter Name</span></span>|<span data-ttu-id="e2705-239">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-239">Restriction Default</span></span>|<span data-ttu-id="e2705-240">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-241">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="e2705-243">1</span><span class="sxs-lookup"><span data-stu-id="e2705-243">1</span></span>|  
|<span data-ttu-id="e2705-244">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-244">Owner</span></span>|@Owner|<span data-ttu-id="e2705-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="e2705-246">2</span><span class="sxs-lookup"><span data-stu-id="e2705-246">2</span></span>|  
|<span data-ttu-id="e2705-247">Název</span><span class="sxs-lookup"><span data-stu-id="e2705-247">Name</span></span>|@Name|<span data-ttu-id="e2705-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="e2705-249">3</span><span class="sxs-lookup"><span data-stu-id="e2705-249">3</span></span>|  
|<span data-ttu-id="e2705-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="e2705-250">Parameter</span></span>|@Parameter|<span data-ttu-id="e2705-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-251">PARAMETER_NAME</span></span>|<span data-ttu-id="e2705-252">4</span><span class="sxs-lookup"><span data-stu-id="e2705-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e2705-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="e2705-253">Procedures</span></span>  
  
|<span data-ttu-id="e2705-254">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-254">Restriction Name</span></span>|<span data-ttu-id="e2705-255">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-255">Parameter Name</span></span>|<span data-ttu-id="e2705-256">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-256">Restriction Default</span></span>|<span data-ttu-id="e2705-257">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-258">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="e2705-260">1</span><span class="sxs-lookup"><span data-stu-id="e2705-260">1</span></span>|  
|<span data-ttu-id="e2705-261">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-261">Owner</span></span>|@Owner|<span data-ttu-id="e2705-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="e2705-263">2</span><span class="sxs-lookup"><span data-stu-id="e2705-263">2</span></span>|  
|<span data-ttu-id="e2705-264">Název</span><span class="sxs-lookup"><span data-stu-id="e2705-264">Name</span></span>|@Name|<span data-ttu-id="e2705-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="e2705-266">3</span><span class="sxs-lookup"><span data-stu-id="e2705-266">3</span></span>|  
|<span data-ttu-id="e2705-267">Type</span><span class="sxs-lookup"><span data-stu-id="e2705-267">Type</span></span>|@Type|<span data-ttu-id="e2705-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e2705-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="e2705-269">4</span><span class="sxs-lookup"><span data-stu-id="e2705-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="e2705-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="e2705-270">IndexColumns</span></span>  
  
|<span data-ttu-id="e2705-271">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-271">Restriction Name</span></span>|<span data-ttu-id="e2705-272">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-272">Parameter Name</span></span>|<span data-ttu-id="e2705-273">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-273">Restriction Default</span></span>|<span data-ttu-id="e2705-274">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-275">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="e2705-276">db_name()</span></span>|<span data-ttu-id="e2705-277">1</span><span class="sxs-lookup"><span data-stu-id="e2705-277">1</span></span>|  
|<span data-ttu-id="e2705-278">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-278">Owner</span></span>|@Owner|<span data-ttu-id="e2705-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="e2705-279">user_name()</span></span>|<span data-ttu-id="e2705-280">2</span><span class="sxs-lookup"><span data-stu-id="e2705-280">2</span></span>|  
|<span data-ttu-id="e2705-281">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-281">Table</span></span>|@Table|<span data-ttu-id="e2705-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="e2705-282">o.name</span></span>|<span data-ttu-id="e2705-283">3</span><span class="sxs-lookup"><span data-stu-id="e2705-283">3</span></span>|  
|<span data-ttu-id="e2705-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="e2705-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="e2705-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="e2705-285">x.name</span></span>|<span data-ttu-id="e2705-286">4</span><span class="sxs-lookup"><span data-stu-id="e2705-286">4</span></span>|  
|<span data-ttu-id="e2705-287">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e2705-287">Column</span></span>|@Column|<span data-ttu-id="e2705-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="e2705-288">c.name</span></span>|<span data-ttu-id="e2705-289">5</span><span class="sxs-lookup"><span data-stu-id="e2705-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e2705-290">Indexy</span><span class="sxs-lookup"><span data-stu-id="e2705-290">Indexes</span></span>  
  
|<span data-ttu-id="e2705-291">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-291">Restriction Name</span></span>|<span data-ttu-id="e2705-292">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-292">Parameter Name</span></span>|<span data-ttu-id="e2705-293">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-293">Restriction Default</span></span>|<span data-ttu-id="e2705-294">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-295">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="e2705-296">db_name()</span></span>|<span data-ttu-id="e2705-297">1</span><span class="sxs-lookup"><span data-stu-id="e2705-297">1</span></span>|  
|<span data-ttu-id="e2705-298">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-298">Owner</span></span>|@Owner|<span data-ttu-id="e2705-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="e2705-299">user_name()</span></span>|<span data-ttu-id="e2705-300">2</span><span class="sxs-lookup"><span data-stu-id="e2705-300">2</span></span>|  
|<span data-ttu-id="e2705-301">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-301">Table</span></span>|@Table|<span data-ttu-id="e2705-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="e2705-302">o.name</span></span>|<span data-ttu-id="e2705-303">3</span><span class="sxs-lookup"><span data-stu-id="e2705-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="e2705-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="e2705-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="e2705-305">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-305">Restriction Name</span></span>|<span data-ttu-id="e2705-306">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-306">Parameter Name</span></span>|<span data-ttu-id="e2705-307">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-307">Restriction Default</span></span>|<span data-ttu-id="e2705-308">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-309">název_sestavení</span><span class="sxs-lookup"><span data-stu-id="e2705-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="e2705-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="e2705-310">assemblies.name</span></span>|<span data-ttu-id="e2705-311">1</span><span class="sxs-lookup"><span data-stu-id="e2705-311">1</span></span>|  
|<span data-ttu-id="e2705-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="e2705-312">udt_name</span></span>|@UDTName|<span data-ttu-id="e2705-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="e2705-313">types.assembly_class</span></span>|<span data-ttu-id="e2705-314">2</span><span class="sxs-lookup"><span data-stu-id="e2705-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="e2705-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="e2705-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="e2705-316">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-316">Restriction Name</span></span>|<span data-ttu-id="e2705-317">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-317">Parameter Name</span></span>|<span data-ttu-id="e2705-318">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-318">Restriction Default</span></span>|<span data-ttu-id="e2705-319">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-320">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="e2705-322">1</span><span class="sxs-lookup"><span data-stu-id="e2705-322">1</span></span>|  
|<span data-ttu-id="e2705-323">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-323">Owner</span></span>|@Owner|<span data-ttu-id="e2705-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="e2705-325">2</span><span class="sxs-lookup"><span data-stu-id="e2705-325">2</span></span>|  
|<span data-ttu-id="e2705-326">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-326">Table</span></span>|@Table|<span data-ttu-id="e2705-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-327">TABLE_NAME</span></span>|<span data-ttu-id="e2705-328">3</span><span class="sxs-lookup"><span data-stu-id="e2705-328">3</span></span>|  
|<span data-ttu-id="e2705-329">Název</span><span class="sxs-lookup"><span data-stu-id="e2705-329">Name</span></span>|@Name|<span data-ttu-id="e2705-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="e2705-331">4</span><span class="sxs-lookup"><span data-stu-id="e2705-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="e2705-332">SQL Server 2008 Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="e2705-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="e2705-333">Omezení pro kolekce schémat SQL Server 2008 naleznete v následujících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="e2705-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="e2705-334">Tato omezení jsou platné od verze SQL Server 2008 a rozhraní .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="e2705-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="e2705-335">Nejsou podporovány v dřívějších verzích rozhraní .NET Framework a systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e2705-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="e2705-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="e2705-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="e2705-337">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-337">Restriction Name</span></span>|<span data-ttu-id="e2705-338">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-338">Parameter Name</span></span>|<span data-ttu-id="e2705-339">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-339">Restriction Default</span></span>|<span data-ttu-id="e2705-340">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-341">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-342">TABLE_CATALOG</span></span>|<span data-ttu-id="e2705-343">1</span><span class="sxs-lookup"><span data-stu-id="e2705-343">1</span></span>|  
|<span data-ttu-id="e2705-344">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-344">Owner</span></span>|@Owner|<span data-ttu-id="e2705-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="e2705-346">2</span><span class="sxs-lookup"><span data-stu-id="e2705-346">2</span></span>|  
|<span data-ttu-id="e2705-347">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-347">Table</span></span>|@Table|<span data-ttu-id="e2705-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-348">TABLE_NAME</span></span>|<span data-ttu-id="e2705-349">3</span><span class="sxs-lookup"><span data-stu-id="e2705-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="e2705-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="e2705-350">AllColumns</span></span>  
  
|<span data-ttu-id="e2705-351">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-351">Restriction Name</span></span>|<span data-ttu-id="e2705-352">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e2705-352">Parameter Name</span></span>|<span data-ttu-id="e2705-353">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-353">Restriction Default</span></span>|<span data-ttu-id="e2705-354">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e2705-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e2705-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="e2705-355">Catalog</span></span>|@Catalog|<span data-ttu-id="e2705-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e2705-356">TABLE_CATALOG</span></span>|<span data-ttu-id="e2705-357">1</span><span class="sxs-lookup"><span data-stu-id="e2705-357">1</span></span>|  
|<span data-ttu-id="e2705-358">Owner</span><span class="sxs-lookup"><span data-stu-id="e2705-358">Owner</span></span>|@Owner|<span data-ttu-id="e2705-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e2705-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="e2705-360">2</span><span class="sxs-lookup"><span data-stu-id="e2705-360">2</span></span>|  
|<span data-ttu-id="e2705-361">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e2705-361">Table</span></span>|@Table|<span data-ttu-id="e2705-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-362">TABLE_NAME</span></span>|<span data-ttu-id="e2705-363">3</span><span class="sxs-lookup"><span data-stu-id="e2705-363">3</span></span>|  
|<span data-ttu-id="e2705-364">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e2705-364">Column</span></span>|@Column|<span data-ttu-id="e2705-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e2705-365">COLUMN_NAME</span></span>|<span data-ttu-id="e2705-366">4</span><span class="sxs-lookup"><span data-stu-id="e2705-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2705-367">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2705-367">See also</span></span>

- [<span data-ttu-id="e2705-368">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="e2705-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
