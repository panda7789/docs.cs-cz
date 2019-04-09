---
title: Omezení schématu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: b5044d39d1dc5d2fa7d2ce691cdda7075fa0e32a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151200"
---
# <a name="schema-restrictions"></a><span data-ttu-id="04a63-102">Omezení schématu</span><span class="sxs-lookup"><span data-stu-id="04a63-102">Schema Restrictions</span></span>
<span data-ttu-id="04a63-103">Druhý volitelný parametr **GetSchema** metoda je vrácena omezení, které se používají a omezit tak množství informací o schématu, a je předán **GetSchema** metody jako pole řetězců .</span><span class="sxs-lookup"><span data-stu-id="04a63-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="04a63-104">Pozice v poli určuje hodnoty, které můžete předat, a to je ekvivalentní hodnotě parametru omezení.</span><span class="sxs-lookup"><span data-stu-id="04a63-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="04a63-105">Například následující tabulka popisuje omezení kolekcí schémat "Tabulky" pomocí zprostředkovatele dat .NET Framework pro SQL Server podporován.</span><span class="sxs-lookup"><span data-stu-id="04a63-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="04a63-106">Další omezení kolekce schémat SQL Server jsou uvedeny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="04a63-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="04a63-107">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-107">Restriction Name</span></span>|<span data-ttu-id="04a63-108">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-108">Parameter Name</span></span>|<span data-ttu-id="04a63-109">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-109">Restriction Default</span></span>|<span data-ttu-id="04a63-110">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-111">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-112">TABLE_CATALOG</span></span>|<span data-ttu-id="04a63-113">1</span><span class="sxs-lookup"><span data-stu-id="04a63-113">1</span></span>|  
|<span data-ttu-id="04a63-114">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-114">Owner</span></span>|@Owner|<span data-ttu-id="04a63-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="04a63-116">2</span><span class="sxs-lookup"><span data-stu-id="04a63-116">2</span></span>|  
|<span data-ttu-id="04a63-117">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-117">Table</span></span>|@Name|<span data-ttu-id="04a63-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-118">TABLE_NAME</span></span>|<span data-ttu-id="04a63-119">3</span><span class="sxs-lookup"><span data-stu-id="04a63-119">3</span></span>|  
|<span data-ttu-id="04a63-120">TableType</span><span class="sxs-lookup"><span data-stu-id="04a63-120">TableType</span></span>|@TableType|<span data-ttu-id="04a63-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="04a63-121">TABLE_TYPE</span></span>|<span data-ttu-id="04a63-122">4</span><span class="sxs-lookup"><span data-stu-id="04a63-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="04a63-123">Určení hodnoty omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="04a63-124">Použijte jednu z těchto omezení kolekce schémat "Tabulky", jednoduše vytvořit pole řetězců, které se čtyřmi prvky a potom umístili hodnotu v elementu, který se shoduje s počtem omezení.</span><span class="sxs-lookup"><span data-stu-id="04a63-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="04a63-125">Například k omezení tabulky vrácené **GetSchema** metodu pouze tabulky ve schématu "Prodeje" nastavit druhý prvek pole, které chcete "Prodeje" před předáním do **GetSchema** metody.</span><span class="sxs-lookup"><span data-stu-id="04a63-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04a63-126">Omezení kolekce pro `SqlClient` a `OracleClient` mají další `ParameterName` sloupce.</span><span class="sxs-lookup"><span data-stu-id="04a63-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="04a63-127">Výchozí sloupec omezení je stále pro zpětnou kompatibilitu, ale aktuálně je ignorována.</span><span class="sxs-lookup"><span data-stu-id="04a63-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="04a63-128">Chcete-li minimalizovat riziko útoků prostřednictvím injektáže SQL, při zadávání hodnoty omezení by měla sloužit parametrizovaných dotazů místo nahrazení řetězce.</span><span class="sxs-lookup"><span data-stu-id="04a63-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04a63-129">Počet prvků v poli musí být menší nebo rovna počtu omezení pro ostatní zadané schéma kolekce nepodporuje <xref:System.ArgumentException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="04a63-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="04a63-130">Může být méně než maximální počet omezení.</span><span class="sxs-lookup"><span data-stu-id="04a63-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="04a63-131">Chybí omezení jsou považován za hodnotu null (bez omezení).</span><span class="sxs-lookup"><span data-stu-id="04a63-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="04a63-132">Můžete dát dotaz na zprostředkovatele rozhraní .NET Framework spravované k určení seznamu podporovaných omezení voláním **GetSchema** metodu s názvem kolekce schémat omezení, což je "Omezení".</span><span class="sxs-lookup"><span data-stu-id="04a63-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="04a63-133">Vrátí <xref:System.Data.DataTable> seznam názvy kolekcí, omezení názvů, omezení výchozí hodnoty a omezení čísla.</span><span class="sxs-lookup"><span data-stu-id="04a63-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="04a63-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="04a63-134">Example</span></span>  
 <span data-ttu-id="04a63-135">Následující příklady ukazují, jak používat <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metoda zprostředkovatele dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> třídy pro načtení schématu informace o všech tabulek, které jsou součástí **AdventureWorks**ukázková databáze a omezit informace vrátí pouze ty tabulky ve schématu "Prodeje":</span><span class="sxs-lookup"><span data-stu-id="04a63-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="04a63-136">Omezení schématu SQL serveru</span><span class="sxs-lookup"><span data-stu-id="04a63-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="04a63-137">Omezení pro kolekce schémat SQL Server naleznete v následujících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="04a63-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="04a63-138">Uživatelé</span><span class="sxs-lookup"><span data-stu-id="04a63-138">Users</span></span>  
  
|<span data-ttu-id="04a63-139">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-139">Restriction Name</span></span>|<span data-ttu-id="04a63-140">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-140">Parameter Name</span></span>|<span data-ttu-id="04a63-141">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-141">Restriction Default</span></span>|<span data-ttu-id="04a63-142">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-143">Uživatelské_jméno</span><span class="sxs-lookup"><span data-stu-id="04a63-143">User_Name</span></span>|@Name|<span data-ttu-id="04a63-144">name</span><span class="sxs-lookup"><span data-stu-id="04a63-144">name</span></span>|<span data-ttu-id="04a63-145">1</span><span class="sxs-lookup"><span data-stu-id="04a63-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="04a63-146">Databáze</span><span class="sxs-lookup"><span data-stu-id="04a63-146">Databases</span></span>  
  
|<span data-ttu-id="04a63-147">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-147">Restriction Name</span></span>|<span data-ttu-id="04a63-148">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-148">Parameter Name</span></span>|<span data-ttu-id="04a63-149">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-149">Restriction Default</span></span>|<span data-ttu-id="04a63-150">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-151">Name</span><span class="sxs-lookup"><span data-stu-id="04a63-151">Name</span></span>|@Name|<span data-ttu-id="04a63-152">Name</span><span class="sxs-lookup"><span data-stu-id="04a63-152">Name</span></span>|<span data-ttu-id="04a63-153">1</span><span class="sxs-lookup"><span data-stu-id="04a63-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="04a63-154">Tabulky</span><span class="sxs-lookup"><span data-stu-id="04a63-154">Tables</span></span>  
  
|<span data-ttu-id="04a63-155">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-155">Restriction Name</span></span>|<span data-ttu-id="04a63-156">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-156">Parameter Name</span></span>|<span data-ttu-id="04a63-157">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-157">Restriction Default</span></span>|<span data-ttu-id="04a63-158">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-159">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-160">TABLE_CATALOG</span></span>|<span data-ttu-id="04a63-161">1</span><span class="sxs-lookup"><span data-stu-id="04a63-161">1</span></span>|  
|<span data-ttu-id="04a63-162">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-162">Owner</span></span>|@Owner|<span data-ttu-id="04a63-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="04a63-164">2</span><span class="sxs-lookup"><span data-stu-id="04a63-164">2</span></span>|  
|<span data-ttu-id="04a63-165">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-165">Table</span></span>|@Name|<span data-ttu-id="04a63-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-166">TABLE_NAME</span></span>|<span data-ttu-id="04a63-167">3</span><span class="sxs-lookup"><span data-stu-id="04a63-167">3</span></span>|  
|<span data-ttu-id="04a63-168">TableType</span><span class="sxs-lookup"><span data-stu-id="04a63-168">TableType</span></span>|@TableType|<span data-ttu-id="04a63-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="04a63-169">TABLE_TYPE</span></span>|<span data-ttu-id="04a63-170">4</span><span class="sxs-lookup"><span data-stu-id="04a63-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="04a63-171">Sloupce</span><span class="sxs-lookup"><span data-stu-id="04a63-171">Columns</span></span>  
  
|<span data-ttu-id="04a63-172">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-172">Restriction Name</span></span>|<span data-ttu-id="04a63-173">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-173">Parameter Name</span></span>|<span data-ttu-id="04a63-174">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-174">Restriction Default</span></span>|<span data-ttu-id="04a63-175">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-176">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-177">TABLE_CATALOG</span></span>|<span data-ttu-id="04a63-178">1</span><span class="sxs-lookup"><span data-stu-id="04a63-178">1</span></span>|  
|<span data-ttu-id="04a63-179">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-179">Owner</span></span>|@Owner|<span data-ttu-id="04a63-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="04a63-181">2</span><span class="sxs-lookup"><span data-stu-id="04a63-181">2</span></span>|  
|<span data-ttu-id="04a63-182">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-182">Table</span></span>|@Table|<span data-ttu-id="04a63-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-183">TABLE_NAME</span></span>|<span data-ttu-id="04a63-184">3</span><span class="sxs-lookup"><span data-stu-id="04a63-184">3</span></span>|  
|<span data-ttu-id="04a63-185">Sloupec</span><span class="sxs-lookup"><span data-stu-id="04a63-185">Column</span></span>|@Column|<span data-ttu-id="04a63-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-186">COLUMN_NAME</span></span>|<span data-ttu-id="04a63-187">4</span><span class="sxs-lookup"><span data-stu-id="04a63-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="04a63-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="04a63-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="04a63-189">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-189">Restriction Name</span></span>|<span data-ttu-id="04a63-190">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-190">Parameter Name</span></span>|<span data-ttu-id="04a63-191">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-191">Restriction Default</span></span>|<span data-ttu-id="04a63-192">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-193">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-194">TABLE_CATALOG</span></span>|<span data-ttu-id="04a63-195">1</span><span class="sxs-lookup"><span data-stu-id="04a63-195">1</span></span>|  
|<span data-ttu-id="04a63-196">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-196">Owner</span></span>|@Owner|<span data-ttu-id="04a63-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="04a63-198">2</span><span class="sxs-lookup"><span data-stu-id="04a63-198">2</span></span>|  
|<span data-ttu-id="04a63-199">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-199">Table</span></span>|@Table|<span data-ttu-id="04a63-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-200">TABLE_NAME</span></span>|<span data-ttu-id="04a63-201">3</span><span class="sxs-lookup"><span data-stu-id="04a63-201">3</span></span>|  
|<span data-ttu-id="04a63-202">Sloupec</span><span class="sxs-lookup"><span data-stu-id="04a63-202">Column</span></span>|@Column|<span data-ttu-id="04a63-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-203">COLUMN_NAME</span></span>|<span data-ttu-id="04a63-204">4</span><span class="sxs-lookup"><span data-stu-id="04a63-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="04a63-205">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="04a63-205">Views</span></span>  
  
|<span data-ttu-id="04a63-206">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-206">Restriction Name</span></span>|<span data-ttu-id="04a63-207">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-207">Parameter Name</span></span>|<span data-ttu-id="04a63-208">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-208">Restriction Default</span></span>|<span data-ttu-id="04a63-209">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-210">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-211">TABLE_CATALOG</span></span>|<span data-ttu-id="04a63-212">1</span><span class="sxs-lookup"><span data-stu-id="04a63-212">1</span></span>|  
|<span data-ttu-id="04a63-213">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-213">Owner</span></span>|@Owner|<span data-ttu-id="04a63-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="04a63-215">2</span><span class="sxs-lookup"><span data-stu-id="04a63-215">2</span></span>|  
|<span data-ttu-id="04a63-216">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-216">Table</span></span>|@Table|<span data-ttu-id="04a63-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-217">TABLE_NAME</span></span>|<span data-ttu-id="04a63-218">3</span><span class="sxs-lookup"><span data-stu-id="04a63-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="04a63-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="04a63-219">ViewColumns</span></span>  
  
|<span data-ttu-id="04a63-220">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-220">Restriction Name</span></span>|<span data-ttu-id="04a63-221">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-221">Parameter Name</span></span>|<span data-ttu-id="04a63-222">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-222">Restriction Default</span></span>|<span data-ttu-id="04a63-223">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-224">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-225">VIEW_CATALOG</span></span>|<span data-ttu-id="04a63-226">1</span><span class="sxs-lookup"><span data-stu-id="04a63-226">1</span></span>|  
|<span data-ttu-id="04a63-227">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-227">Owner</span></span>|@Owner|<span data-ttu-id="04a63-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="04a63-229">2</span><span class="sxs-lookup"><span data-stu-id="04a63-229">2</span></span>|  
|<span data-ttu-id="04a63-230">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-230">Table</span></span>|@Table|<span data-ttu-id="04a63-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-231">VIEW_NAME</span></span>|<span data-ttu-id="04a63-232">3</span><span class="sxs-lookup"><span data-stu-id="04a63-232">3</span></span>|  
|<span data-ttu-id="04a63-233">Sloupec</span><span class="sxs-lookup"><span data-stu-id="04a63-233">Column</span></span>|@Column|<span data-ttu-id="04a63-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-234">COLUMN_NAME</span></span>|<span data-ttu-id="04a63-235">4</span><span class="sxs-lookup"><span data-stu-id="04a63-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="04a63-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="04a63-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="04a63-237">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-237">Restriction Name</span></span>|<span data-ttu-id="04a63-238">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-238">Parameter Name</span></span>|<span data-ttu-id="04a63-239">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-239">Restriction Default</span></span>|<span data-ttu-id="04a63-240">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-241">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="04a63-243">1</span><span class="sxs-lookup"><span data-stu-id="04a63-243">1</span></span>|  
|<span data-ttu-id="04a63-244">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-244">Owner</span></span>|@Owner|<span data-ttu-id="04a63-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="04a63-246">2</span><span class="sxs-lookup"><span data-stu-id="04a63-246">2</span></span>|  
|<span data-ttu-id="04a63-247">Name</span><span class="sxs-lookup"><span data-stu-id="04a63-247">Name</span></span>|@Name|<span data-ttu-id="04a63-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="04a63-249">3</span><span class="sxs-lookup"><span data-stu-id="04a63-249">3</span></span>|  
|<span data-ttu-id="04a63-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="04a63-250">Parameter</span></span>|@Parameter|<span data-ttu-id="04a63-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-251">PARAMETER_NAME</span></span>|<span data-ttu-id="04a63-252">4</span><span class="sxs-lookup"><span data-stu-id="04a63-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="04a63-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="04a63-253">Procedures</span></span>  
  
|<span data-ttu-id="04a63-254">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-254">Restriction Name</span></span>|<span data-ttu-id="04a63-255">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-255">Parameter Name</span></span>|<span data-ttu-id="04a63-256">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-256">Restriction Default</span></span>|<span data-ttu-id="04a63-257">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-258">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="04a63-260">1</span><span class="sxs-lookup"><span data-stu-id="04a63-260">1</span></span>|  
|<span data-ttu-id="04a63-261">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-261">Owner</span></span>|@Owner|<span data-ttu-id="04a63-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="04a63-263">2</span><span class="sxs-lookup"><span data-stu-id="04a63-263">2</span></span>|  
|<span data-ttu-id="04a63-264">Name</span><span class="sxs-lookup"><span data-stu-id="04a63-264">Name</span></span>|@Name|<span data-ttu-id="04a63-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="04a63-266">3</span><span class="sxs-lookup"><span data-stu-id="04a63-266">3</span></span>|  
|<span data-ttu-id="04a63-267">Type</span><span class="sxs-lookup"><span data-stu-id="04a63-267">Type</span></span>|@Type|<span data-ttu-id="04a63-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="04a63-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="04a63-269">4</span><span class="sxs-lookup"><span data-stu-id="04a63-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="04a63-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="04a63-270">IndexColumns</span></span>  
  
|<span data-ttu-id="04a63-271">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-271">Restriction Name</span></span>|<span data-ttu-id="04a63-272">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-272">Parameter Name</span></span>|<span data-ttu-id="04a63-273">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-273">Restriction Default</span></span>|<span data-ttu-id="04a63-274">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-275">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="04a63-276">db_name()</span></span>|<span data-ttu-id="04a63-277">1</span><span class="sxs-lookup"><span data-stu-id="04a63-277">1</span></span>|  
|<span data-ttu-id="04a63-278">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-278">Owner</span></span>|@Owner|<span data-ttu-id="04a63-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="04a63-279">user_name()</span></span>|<span data-ttu-id="04a63-280">2</span><span class="sxs-lookup"><span data-stu-id="04a63-280">2</span></span>|  
|<span data-ttu-id="04a63-281">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-281">Table</span></span>|@Table|<span data-ttu-id="04a63-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="04a63-282">o.name</span></span>|<span data-ttu-id="04a63-283">3</span><span class="sxs-lookup"><span data-stu-id="04a63-283">3</span></span>|  
|<span data-ttu-id="04a63-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="04a63-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="04a63-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="04a63-285">x.name</span></span>|<span data-ttu-id="04a63-286">4</span><span class="sxs-lookup"><span data-stu-id="04a63-286">4</span></span>|  
|<span data-ttu-id="04a63-287">Sloupec</span><span class="sxs-lookup"><span data-stu-id="04a63-287">Column</span></span>|@Column|<span data-ttu-id="04a63-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="04a63-288">c.name</span></span>|<span data-ttu-id="04a63-289">5</span><span class="sxs-lookup"><span data-stu-id="04a63-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="04a63-290">Indexy</span><span class="sxs-lookup"><span data-stu-id="04a63-290">Indexes</span></span>  
  
|<span data-ttu-id="04a63-291">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-291">Restriction Name</span></span>|<span data-ttu-id="04a63-292">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-292">Parameter Name</span></span>|<span data-ttu-id="04a63-293">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-293">Restriction Default</span></span>|<span data-ttu-id="04a63-294">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-295">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="04a63-296">db_name()</span></span>|<span data-ttu-id="04a63-297">1</span><span class="sxs-lookup"><span data-stu-id="04a63-297">1</span></span>|  
|<span data-ttu-id="04a63-298">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-298">Owner</span></span>|@Owner|<span data-ttu-id="04a63-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="04a63-299">user_name()</span></span>|<span data-ttu-id="04a63-300">2</span><span class="sxs-lookup"><span data-stu-id="04a63-300">2</span></span>|  
|<span data-ttu-id="04a63-301">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-301">Table</span></span>|@Table|<span data-ttu-id="04a63-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="04a63-302">o.name</span></span>|<span data-ttu-id="04a63-303">3</span><span class="sxs-lookup"><span data-stu-id="04a63-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="04a63-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="04a63-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="04a63-305">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-305">Restriction Name</span></span>|<span data-ttu-id="04a63-306">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-306">Parameter Name</span></span>|<span data-ttu-id="04a63-307">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-307">Restriction Default</span></span>|<span data-ttu-id="04a63-308">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-309">název_sestavení</span><span class="sxs-lookup"><span data-stu-id="04a63-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="04a63-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="04a63-310">assemblies.name</span></span>|<span data-ttu-id="04a63-311">1</span><span class="sxs-lookup"><span data-stu-id="04a63-311">1</span></span>|  
|<span data-ttu-id="04a63-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="04a63-312">udt_name</span></span>|@UDTName|<span data-ttu-id="04a63-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="04a63-313">types.assembly_class</span></span>|<span data-ttu-id="04a63-314">2</span><span class="sxs-lookup"><span data-stu-id="04a63-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="04a63-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="04a63-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="04a63-316">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-316">Restriction Name</span></span>|<span data-ttu-id="04a63-317">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-317">Parameter Name</span></span>|<span data-ttu-id="04a63-318">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-318">Restriction Default</span></span>|<span data-ttu-id="04a63-319">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-320">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="04a63-322">1</span><span class="sxs-lookup"><span data-stu-id="04a63-322">1</span></span>|  
|<span data-ttu-id="04a63-323">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-323">Owner</span></span>|@Owner|<span data-ttu-id="04a63-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="04a63-325">2</span><span class="sxs-lookup"><span data-stu-id="04a63-325">2</span></span>|  
|<span data-ttu-id="04a63-326">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-326">Table</span></span>|@Table|<span data-ttu-id="04a63-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-327">TABLE_NAME</span></span>|<span data-ttu-id="04a63-328">3</span><span class="sxs-lookup"><span data-stu-id="04a63-328">3</span></span>|  
|<span data-ttu-id="04a63-329">Name</span><span class="sxs-lookup"><span data-stu-id="04a63-329">Name</span></span>|@Name|<span data-ttu-id="04a63-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="04a63-331">4</span><span class="sxs-lookup"><span data-stu-id="04a63-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="04a63-332">SQL Server 2008 Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="04a63-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="04a63-333">Omezení pro kolekce schémat SQL Server 2008 naleznete v následujících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="04a63-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="04a63-334">Tato omezení jsou platné od verze SQL Server 2008 a rozhraní .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="04a63-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="04a63-335">Nejsou podporovány v dřívějších verzích rozhraní .NET Framework a systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04a63-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="04a63-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="04a63-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="04a63-337">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-337">Restriction Name</span></span>|<span data-ttu-id="04a63-338">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-338">Parameter Name</span></span>|<span data-ttu-id="04a63-339">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-339">Restriction Default</span></span>|<span data-ttu-id="04a63-340">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-341">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-342">TABLE_CATALOG</span></span>|<span data-ttu-id="04a63-343">1</span><span class="sxs-lookup"><span data-stu-id="04a63-343">1</span></span>|  
|<span data-ttu-id="04a63-344">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-344">Owner</span></span>|@Owner|<span data-ttu-id="04a63-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="04a63-346">2</span><span class="sxs-lookup"><span data-stu-id="04a63-346">2</span></span>|  
|<span data-ttu-id="04a63-347">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-347">Table</span></span>|@Table|<span data-ttu-id="04a63-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-348">TABLE_NAME</span></span>|<span data-ttu-id="04a63-349">3</span><span class="sxs-lookup"><span data-stu-id="04a63-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="04a63-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="04a63-350">AllColumns</span></span>  
  
|<span data-ttu-id="04a63-351">Název omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-351">Restriction Name</span></span>|<span data-ttu-id="04a63-352">Název parametru</span><span class="sxs-lookup"><span data-stu-id="04a63-352">Parameter Name</span></span>|<span data-ttu-id="04a63-353">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-353">Restriction Default</span></span>|<span data-ttu-id="04a63-354">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="04a63-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="04a63-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="04a63-355">Catalog</span></span>|@Catalog|<span data-ttu-id="04a63-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="04a63-356">TABLE_CATALOG</span></span>|<span data-ttu-id="04a63-357">1</span><span class="sxs-lookup"><span data-stu-id="04a63-357">1</span></span>|  
|<span data-ttu-id="04a63-358">Owner</span><span class="sxs-lookup"><span data-stu-id="04a63-358">Owner</span></span>|@Owner|<span data-ttu-id="04a63-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="04a63-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="04a63-360">2</span><span class="sxs-lookup"><span data-stu-id="04a63-360">2</span></span>|  
|<span data-ttu-id="04a63-361">Tabulka</span><span class="sxs-lookup"><span data-stu-id="04a63-361">Table</span></span>|@Table|<span data-ttu-id="04a63-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-362">TABLE_NAME</span></span>|<span data-ttu-id="04a63-363">3</span><span class="sxs-lookup"><span data-stu-id="04a63-363">3</span></span>|  
|<span data-ttu-id="04a63-364">Sloupec</span><span class="sxs-lookup"><span data-stu-id="04a63-364">Column</span></span>|@Column|<span data-ttu-id="04a63-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="04a63-365">COLUMN_NAME</span></span>|<span data-ttu-id="04a63-366">4</span><span class="sxs-lookup"><span data-stu-id="04a63-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04a63-367">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04a63-367">See also</span></span>

- [<span data-ttu-id="04a63-368">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="04a63-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
