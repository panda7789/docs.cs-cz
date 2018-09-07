---
title: Omezení schématu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 040ecd8a2ce223f89601de735b77ccc81638c7af
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079705"
---
# <a name="schema-restrictions"></a><span data-ttu-id="e149e-102">Omezení schématu</span><span class="sxs-lookup"><span data-stu-id="e149e-102">Schema Restrictions</span></span>
<span data-ttu-id="e149e-103">Druhý volitelný parametr **GetSchema** metoda je vrácena omezení, které se používají a omezit tak množství informací o schématu, a je předán **GetSchema** metody jako pole řetězců .</span><span class="sxs-lookup"><span data-stu-id="e149e-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="e149e-104">Pozice v poli určuje hodnoty, které můžete předat, a to je ekvivalentní hodnotě parametru omezení.</span><span class="sxs-lookup"><span data-stu-id="e149e-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="e149e-105">Například následující tabulka popisuje omezení kolekcí schémat "Tabulky" pomocí zprostředkovatele dat .NET Framework pro SQL Server podporován.</span><span class="sxs-lookup"><span data-stu-id="e149e-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="e149e-106">Další omezení kolekce schémat SQL Server jsou uvedeny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e149e-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="e149e-107">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-107">Restriction Name</span></span>|<span data-ttu-id="e149e-108">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-108">Parameter Name</span></span>|<span data-ttu-id="e149e-109">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-109">Restriction Default</span></span>|<span data-ttu-id="e149e-110">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-111">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-112">TABLE_CATALOG</span></span>|<span data-ttu-id="e149e-113">1</span><span class="sxs-lookup"><span data-stu-id="e149e-113">1</span></span>|  
|<span data-ttu-id="e149e-114">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-114">Owner</span></span>|@Owner|<span data-ttu-id="e149e-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="e149e-116">2</span><span class="sxs-lookup"><span data-stu-id="e149e-116">2</span></span>|  
|<span data-ttu-id="e149e-117">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-117">Table</span></span>|@Name|<span data-ttu-id="e149e-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-118">TABLE_NAME</span></span>|<span data-ttu-id="e149e-119">3</span><span class="sxs-lookup"><span data-stu-id="e149e-119">3</span></span>|  
|<span data-ttu-id="e149e-120">TableType</span><span class="sxs-lookup"><span data-stu-id="e149e-120">TableType</span></span>|@TableType|<span data-ttu-id="e149e-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e149e-121">TABLE_TYPE</span></span>|<span data-ttu-id="e149e-122">4</span><span class="sxs-lookup"><span data-stu-id="e149e-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="e149e-123">Určení hodnoty omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="e149e-124">Použijte jednu z těchto omezení kolekce schémat "Tabulky", jednoduše vytvořit pole řetězců, které se čtyřmi prvky a potom umístili hodnotu v elementu, který se shoduje s počtem omezení.</span><span class="sxs-lookup"><span data-stu-id="e149e-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="e149e-125">Například k omezení tabulky vrácené **GetSchema** metodu pouze tabulky ve schématu "Prodeje" nastavit druhý prvek pole, které chcete "Prodeje" před předáním do **GetSchema** metody.</span><span class="sxs-lookup"><span data-stu-id="e149e-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e149e-126">Omezení kolekce pro `SqlClient` a `OracleClient` mají další `ParameterName` sloupce.</span><span class="sxs-lookup"><span data-stu-id="e149e-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="e149e-127">Výchozí sloupec omezení je stále pro zpětnou kompatibilitu, ale aktuálně je ignorována.</span><span class="sxs-lookup"><span data-stu-id="e149e-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="e149e-128">Chcete-li minimalizovat riziko útoků prostřednictvím injektáže SQL, při zadávání hodnoty omezení by měla sloužit parametrizovaných dotazů místo nahrazení řetězce.</span><span class="sxs-lookup"><span data-stu-id="e149e-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e149e-129">Počet prvků v poli musí být menší nebo rovna počtu omezení pro ostatní zadané schéma kolekce nepodporuje <xref:System.ArgumentException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e149e-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="e149e-130">Může být méně než maximální počet omezení.</span><span class="sxs-lookup"><span data-stu-id="e149e-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="e149e-131">Chybí omezení jsou považován za hodnotu null (bez omezení).</span><span class="sxs-lookup"><span data-stu-id="e149e-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="e149e-132">Můžete dát dotaz na zprostředkovatele rozhraní .NET Framework spravované k určení seznamu podporovaných omezení voláním **GetSchema** metodu s názvem kolekce schémat omezení, což je "Omezení".</span><span class="sxs-lookup"><span data-stu-id="e149e-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="e149e-133">Vrátí <xref:System.Data.DataTable> seznam názvy kolekcí, omezení názvů, omezení výchozí hodnoty a omezení čísla.</span><span class="sxs-lookup"><span data-stu-id="e149e-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e149e-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="e149e-134">Example</span></span>  
 <span data-ttu-id="e149e-135">Následující příklady ukazují, jak používat <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metoda zprostředkovatele dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> třídy pro načtení schématu informace o všech tabulek, které jsou součástí **AdventureWorks**ukázková databáze a omezit informace vrátí pouze ty tabulky ve schématu "Prodeje":</span><span class="sxs-lookup"><span data-stu-id="e149e-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="e149e-136">Omezení schématu SQL serveru</span><span class="sxs-lookup"><span data-stu-id="e149e-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="e149e-137">Omezení pro kolekce schémat SQL Server naleznete v následujících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="e149e-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="e149e-138">Uživatelé</span><span class="sxs-lookup"><span data-stu-id="e149e-138">Users</span></span>  
  
|<span data-ttu-id="e149e-139">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-139">Restriction Name</span></span>|<span data-ttu-id="e149e-140">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-140">Parameter Name</span></span>|<span data-ttu-id="e149e-141">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-141">Restriction Default</span></span>|<span data-ttu-id="e149e-142">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-143">Uživatelské_jméno</span><span class="sxs-lookup"><span data-stu-id="e149e-143">User_Name</span></span>|@Name|<span data-ttu-id="e149e-144">name</span><span class="sxs-lookup"><span data-stu-id="e149e-144">name</span></span>|<span data-ttu-id="e149e-145">1</span><span class="sxs-lookup"><span data-stu-id="e149e-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="e149e-146">Databáze</span><span class="sxs-lookup"><span data-stu-id="e149e-146">Databases</span></span>  
  
|<span data-ttu-id="e149e-147">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-147">Restriction Name</span></span>|<span data-ttu-id="e149e-148">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-148">Parameter Name</span></span>|<span data-ttu-id="e149e-149">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-149">Restriction Default</span></span>|<span data-ttu-id="e149e-150">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-151">Název</span><span class="sxs-lookup"><span data-stu-id="e149e-151">Name</span></span>|@Name|<span data-ttu-id="e149e-152">Název</span><span class="sxs-lookup"><span data-stu-id="e149e-152">Name</span></span>|<span data-ttu-id="e149e-153">1</span><span class="sxs-lookup"><span data-stu-id="e149e-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="e149e-154">Tabulky</span><span class="sxs-lookup"><span data-stu-id="e149e-154">Tables</span></span>  
  
|<span data-ttu-id="e149e-155">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-155">Restriction Name</span></span>|<span data-ttu-id="e149e-156">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-156">Parameter Name</span></span>|<span data-ttu-id="e149e-157">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-157">Restriction Default</span></span>|<span data-ttu-id="e149e-158">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-159">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-160">TABLE_CATALOG</span></span>|<span data-ttu-id="e149e-161">1</span><span class="sxs-lookup"><span data-stu-id="e149e-161">1</span></span>|  
|<span data-ttu-id="e149e-162">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-162">Owner</span></span>|@Owner|<span data-ttu-id="e149e-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="e149e-164">2</span><span class="sxs-lookup"><span data-stu-id="e149e-164">2</span></span>|  
|<span data-ttu-id="e149e-165">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-165">Table</span></span>|@Name|<span data-ttu-id="e149e-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-166">TABLE_NAME</span></span>|<span data-ttu-id="e149e-167">3</span><span class="sxs-lookup"><span data-stu-id="e149e-167">3</span></span>|  
|<span data-ttu-id="e149e-168">TableType</span><span class="sxs-lookup"><span data-stu-id="e149e-168">TableType</span></span>|@TableType|<span data-ttu-id="e149e-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e149e-169">TABLE_TYPE</span></span>|<span data-ttu-id="e149e-170">4</span><span class="sxs-lookup"><span data-stu-id="e149e-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e149e-171">Sloupce</span><span class="sxs-lookup"><span data-stu-id="e149e-171">Columns</span></span>  
  
|<span data-ttu-id="e149e-172">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-172">Restriction Name</span></span>|<span data-ttu-id="e149e-173">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-173">Parameter Name</span></span>|<span data-ttu-id="e149e-174">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-174">Restriction Default</span></span>|<span data-ttu-id="e149e-175">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-176">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-177">TABLE_CATALOG</span></span>|<span data-ttu-id="e149e-178">1</span><span class="sxs-lookup"><span data-stu-id="e149e-178">1</span></span>|  
|<span data-ttu-id="e149e-179">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-179">Owner</span></span>|@Owner|<span data-ttu-id="e149e-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="e149e-181">2</span><span class="sxs-lookup"><span data-stu-id="e149e-181">2</span></span>|  
|<span data-ttu-id="e149e-182">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-182">Table</span></span>|@Table|<span data-ttu-id="e149e-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-183">TABLE_NAME</span></span>|<span data-ttu-id="e149e-184">3</span><span class="sxs-lookup"><span data-stu-id="e149e-184">3</span></span>|  
|<span data-ttu-id="e149e-185">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e149e-185">Column</span></span>|@Column|<span data-ttu-id="e149e-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-186">COLUMN_NAME</span></span>|<span data-ttu-id="e149e-187">4</span><span class="sxs-lookup"><span data-stu-id="e149e-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="e149e-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="e149e-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="e149e-189">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-189">Restriction Name</span></span>|<span data-ttu-id="e149e-190">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-190">Parameter Name</span></span>|<span data-ttu-id="e149e-191">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-191">Restriction Default</span></span>|<span data-ttu-id="e149e-192">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-193">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-194">TABLE_CATALOG</span></span>|<span data-ttu-id="e149e-195">1</span><span class="sxs-lookup"><span data-stu-id="e149e-195">1</span></span>|  
|<span data-ttu-id="e149e-196">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-196">Owner</span></span>|@Owner|<span data-ttu-id="e149e-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="e149e-198">2</span><span class="sxs-lookup"><span data-stu-id="e149e-198">2</span></span>|  
|<span data-ttu-id="e149e-199">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-199">Table</span></span>|@Table|<span data-ttu-id="e149e-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-200">TABLE_NAME</span></span>|<span data-ttu-id="e149e-201">3</span><span class="sxs-lookup"><span data-stu-id="e149e-201">3</span></span>|  
|<span data-ttu-id="e149e-202">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e149e-202">Column</span></span>|@Column|<span data-ttu-id="e149e-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-203">COLUMN_NAME</span></span>|<span data-ttu-id="e149e-204">4</span><span class="sxs-lookup"><span data-stu-id="e149e-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="e149e-205">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="e149e-205">Views</span></span>  
  
|<span data-ttu-id="e149e-206">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-206">Restriction Name</span></span>|<span data-ttu-id="e149e-207">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-207">Parameter Name</span></span>|<span data-ttu-id="e149e-208">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-208">Restriction Default</span></span>|<span data-ttu-id="e149e-209">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-210">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-211">TABLE_CATALOG</span></span>|<span data-ttu-id="e149e-212">1</span><span class="sxs-lookup"><span data-stu-id="e149e-212">1</span></span>|  
|<span data-ttu-id="e149e-213">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-213">Owner</span></span>|@Owner|<span data-ttu-id="e149e-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="e149e-215">2</span><span class="sxs-lookup"><span data-stu-id="e149e-215">2</span></span>|  
|<span data-ttu-id="e149e-216">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-216">Table</span></span>|@Table|<span data-ttu-id="e149e-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-217">TABLE_NAME</span></span>|<span data-ttu-id="e149e-218">3</span><span class="sxs-lookup"><span data-stu-id="e149e-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="e149e-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="e149e-219">ViewColumns</span></span>  
  
|<span data-ttu-id="e149e-220">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-220">Restriction Name</span></span>|<span data-ttu-id="e149e-221">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-221">Parameter Name</span></span>|<span data-ttu-id="e149e-222">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-222">Restriction Default</span></span>|<span data-ttu-id="e149e-223">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-224">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-225">VIEW_CATALOG</span></span>|<span data-ttu-id="e149e-226">1</span><span class="sxs-lookup"><span data-stu-id="e149e-226">1</span></span>|  
|<span data-ttu-id="e149e-227">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-227">Owner</span></span>|@Owner|<span data-ttu-id="e149e-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="e149e-229">2</span><span class="sxs-lookup"><span data-stu-id="e149e-229">2</span></span>|  
|<span data-ttu-id="e149e-230">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-230">Table</span></span>|@Table|<span data-ttu-id="e149e-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-231">VIEW_NAME</span></span>|<span data-ttu-id="e149e-232">3</span><span class="sxs-lookup"><span data-stu-id="e149e-232">3</span></span>|  
|<span data-ttu-id="e149e-233">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e149e-233">Column</span></span>|@Column|<span data-ttu-id="e149e-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-234">COLUMN_NAME</span></span>|<span data-ttu-id="e149e-235">4</span><span class="sxs-lookup"><span data-stu-id="e149e-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e149e-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e149e-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e149e-237">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-237">Restriction Name</span></span>|<span data-ttu-id="e149e-238">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-238">Parameter Name</span></span>|<span data-ttu-id="e149e-239">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-239">Restriction Default</span></span>|<span data-ttu-id="e149e-240">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-241">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="e149e-243">1</span><span class="sxs-lookup"><span data-stu-id="e149e-243">1</span></span>|  
|<span data-ttu-id="e149e-244">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-244">Owner</span></span>|@Owner|<span data-ttu-id="e149e-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="e149e-246">2</span><span class="sxs-lookup"><span data-stu-id="e149e-246">2</span></span>|  
|<span data-ttu-id="e149e-247">Název</span><span class="sxs-lookup"><span data-stu-id="e149e-247">Name</span></span>|@Name|<span data-ttu-id="e149e-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="e149e-249">3</span><span class="sxs-lookup"><span data-stu-id="e149e-249">3</span></span>|  
|<span data-ttu-id="e149e-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="e149e-250">Parameter</span></span>|@Parameter|<span data-ttu-id="e149e-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-251">PARAMETER_NAME</span></span>|<span data-ttu-id="e149e-252">4</span><span class="sxs-lookup"><span data-stu-id="e149e-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e149e-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="e149e-253">Procedures</span></span>  
  
|<span data-ttu-id="e149e-254">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-254">Restriction Name</span></span>|<span data-ttu-id="e149e-255">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-255">Parameter Name</span></span>|<span data-ttu-id="e149e-256">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-256">Restriction Default</span></span>|<span data-ttu-id="e149e-257">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-258">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="e149e-260">1</span><span class="sxs-lookup"><span data-stu-id="e149e-260">1</span></span>|  
|<span data-ttu-id="e149e-261">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-261">Owner</span></span>|@Owner|<span data-ttu-id="e149e-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="e149e-263">2</span><span class="sxs-lookup"><span data-stu-id="e149e-263">2</span></span>|  
|<span data-ttu-id="e149e-264">Název</span><span class="sxs-lookup"><span data-stu-id="e149e-264">Name</span></span>|@Name|<span data-ttu-id="e149e-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="e149e-266">3</span><span class="sxs-lookup"><span data-stu-id="e149e-266">3</span></span>|  
|<span data-ttu-id="e149e-267">Typ</span><span class="sxs-lookup"><span data-stu-id="e149e-267">Type</span></span>|@Type|<span data-ttu-id="e149e-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e149e-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="e149e-269">4</span><span class="sxs-lookup"><span data-stu-id="e149e-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="e149e-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="e149e-270">IndexColumns</span></span>  
  
|<span data-ttu-id="e149e-271">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-271">Restriction Name</span></span>|<span data-ttu-id="e149e-272">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-272">Parameter Name</span></span>|<span data-ttu-id="e149e-273">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-273">Restriction Default</span></span>|<span data-ttu-id="e149e-274">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-275">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="e149e-276">db_name()</span></span>|<span data-ttu-id="e149e-277">1</span><span class="sxs-lookup"><span data-stu-id="e149e-277">1</span></span>|  
|<span data-ttu-id="e149e-278">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-278">Owner</span></span>|@Owner|<span data-ttu-id="e149e-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="e149e-279">user_name()</span></span>|<span data-ttu-id="e149e-280">2</span><span class="sxs-lookup"><span data-stu-id="e149e-280">2</span></span>|  
|<span data-ttu-id="e149e-281">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-281">Table</span></span>|@Table|<span data-ttu-id="e149e-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="e149e-282">o.name</span></span>|<span data-ttu-id="e149e-283">3</span><span class="sxs-lookup"><span data-stu-id="e149e-283">3</span></span>|  
|<span data-ttu-id="e149e-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="e149e-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="e149e-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="e149e-285">x.name</span></span>|<span data-ttu-id="e149e-286">4</span><span class="sxs-lookup"><span data-stu-id="e149e-286">4</span></span>|  
|<span data-ttu-id="e149e-287">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e149e-287">Column</span></span>|@Column|<span data-ttu-id="e149e-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="e149e-288">c.name</span></span>|<span data-ttu-id="e149e-289">5</span><span class="sxs-lookup"><span data-stu-id="e149e-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e149e-290">Indexy</span><span class="sxs-lookup"><span data-stu-id="e149e-290">Indexes</span></span>  
  
|<span data-ttu-id="e149e-291">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-291">Restriction Name</span></span>|<span data-ttu-id="e149e-292">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-292">Parameter Name</span></span>|<span data-ttu-id="e149e-293">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-293">Restriction Default</span></span>|<span data-ttu-id="e149e-294">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-295">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="e149e-296">db_name()</span></span>|<span data-ttu-id="e149e-297">1</span><span class="sxs-lookup"><span data-stu-id="e149e-297">1</span></span>|  
|<span data-ttu-id="e149e-298">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-298">Owner</span></span>|@Owner|<span data-ttu-id="e149e-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="e149e-299">user_name()</span></span>|<span data-ttu-id="e149e-300">2</span><span class="sxs-lookup"><span data-stu-id="e149e-300">2</span></span>|  
|<span data-ttu-id="e149e-301">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-301">Table</span></span>|@Table|<span data-ttu-id="e149e-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="e149e-302">o.name</span></span>|<span data-ttu-id="e149e-303">3</span><span class="sxs-lookup"><span data-stu-id="e149e-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="e149e-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="e149e-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="e149e-305">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-305">Restriction Name</span></span>|<span data-ttu-id="e149e-306">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-306">Parameter Name</span></span>|<span data-ttu-id="e149e-307">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-307">Restriction Default</span></span>|<span data-ttu-id="e149e-308">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-309">název_sestavení</span><span class="sxs-lookup"><span data-stu-id="e149e-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="e149e-310">Assemblies.Name</span><span class="sxs-lookup"><span data-stu-id="e149e-310">assemblies.name</span></span>|<span data-ttu-id="e149e-311">1</span><span class="sxs-lookup"><span data-stu-id="e149e-311">1</span></span>|  
|<span data-ttu-id="e149e-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="e149e-312">udt_name</span></span>|@UDTName|<span data-ttu-id="e149e-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="e149e-313">types.assembly_class</span></span>|<span data-ttu-id="e149e-314">2</span><span class="sxs-lookup"><span data-stu-id="e149e-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="e149e-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="e149e-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="e149e-316">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-316">Restriction Name</span></span>|<span data-ttu-id="e149e-317">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-317">Parameter Name</span></span>|<span data-ttu-id="e149e-318">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-318">Restriction Default</span></span>|<span data-ttu-id="e149e-319">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-320">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="e149e-322">1</span><span class="sxs-lookup"><span data-stu-id="e149e-322">1</span></span>|  
|<span data-ttu-id="e149e-323">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-323">Owner</span></span>|@Owner|<span data-ttu-id="e149e-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="e149e-325">2</span><span class="sxs-lookup"><span data-stu-id="e149e-325">2</span></span>|  
|<span data-ttu-id="e149e-326">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-326">Table</span></span>|@Table|<span data-ttu-id="e149e-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-327">TABLE_NAME</span></span>|<span data-ttu-id="e149e-328">3</span><span class="sxs-lookup"><span data-stu-id="e149e-328">3</span></span>|  
|<span data-ttu-id="e149e-329">Název</span><span class="sxs-lookup"><span data-stu-id="e149e-329">Name</span></span>|@Name|<span data-ttu-id="e149e-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="e149e-331">4</span><span class="sxs-lookup"><span data-stu-id="e149e-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="e149e-332">SQL Server 2008 Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="e149e-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="e149e-333">Omezení pro kolekce schémat SQL Server 2008 naleznete v následujících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="e149e-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="e149e-334">Tato omezení jsou platné od verze SQL Server 2008 a rozhraní .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="e149e-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="e149e-335">Nejsou podporovány v dřívějších verzích rozhraní .NET Framework a systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e149e-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="e149e-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="e149e-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="e149e-337">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-337">Restriction Name</span></span>|<span data-ttu-id="e149e-338">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-338">Parameter Name</span></span>|<span data-ttu-id="e149e-339">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-339">Restriction Default</span></span>|<span data-ttu-id="e149e-340">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-341">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-342">TABLE_CATALOG</span></span>|<span data-ttu-id="e149e-343">1</span><span class="sxs-lookup"><span data-stu-id="e149e-343">1</span></span>|  
|<span data-ttu-id="e149e-344">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-344">Owner</span></span>|@Owner|<span data-ttu-id="e149e-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="e149e-346">2</span><span class="sxs-lookup"><span data-stu-id="e149e-346">2</span></span>|  
|<span data-ttu-id="e149e-347">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-347">Table</span></span>|@Table|<span data-ttu-id="e149e-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-348">TABLE_NAME</span></span>|<span data-ttu-id="e149e-349">3</span><span class="sxs-lookup"><span data-stu-id="e149e-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="e149e-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="e149e-350">AllColumns</span></span>  
  
|<span data-ttu-id="e149e-351">Název omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-351">Restriction Name</span></span>|<span data-ttu-id="e149e-352">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e149e-352">Parameter Name</span></span>|<span data-ttu-id="e149e-353">Výchozí omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-353">Restriction Default</span></span>|<span data-ttu-id="e149e-354">Číslo omezení</span><span class="sxs-lookup"><span data-stu-id="e149e-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e149e-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="e149e-355">Catalog</span></span>|@Catalog|<span data-ttu-id="e149e-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e149e-356">TABLE_CATALOG</span></span>|<span data-ttu-id="e149e-357">1</span><span class="sxs-lookup"><span data-stu-id="e149e-357">1</span></span>|  
|<span data-ttu-id="e149e-358">Vlastník</span><span class="sxs-lookup"><span data-stu-id="e149e-358">Owner</span></span>|@Owner|<span data-ttu-id="e149e-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e149e-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="e149e-360">2</span><span class="sxs-lookup"><span data-stu-id="e149e-360">2</span></span>|  
|<span data-ttu-id="e149e-361">Tabulka</span><span class="sxs-lookup"><span data-stu-id="e149e-361">Table</span></span>|@Table|<span data-ttu-id="e149e-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-362">TABLE_NAME</span></span>|<span data-ttu-id="e149e-363">3</span><span class="sxs-lookup"><span data-stu-id="e149e-363">3</span></span>|  
|<span data-ttu-id="e149e-364">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e149e-364">Column</span></span>|@Column|<span data-ttu-id="e149e-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e149e-365">COLUMN_NAME</span></span>|<span data-ttu-id="e149e-366">4</span><span class="sxs-lookup"><span data-stu-id="e149e-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e149e-367">Viz také</span><span class="sxs-lookup"><span data-stu-id="e149e-367">See Also</span></span>  
 [<span data-ttu-id="e149e-368">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="e149e-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
