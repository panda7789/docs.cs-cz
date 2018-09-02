---
title: Aktivity entit
ms.date: 03/30/2017
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
ms.openlocfilehash: 03bd0e42c70f1226558d492bcb3b2cfa5c7010f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385801"
---
# <a name="entity-activities"></a><span data-ttu-id="c86bd-102">Aktivity entit</span><span class="sxs-lookup"><span data-stu-id="c86bd-102">Entity Activities</span></span>
<span data-ttu-id="c86bd-103">Tento příklad ukazuje způsob použití rozhraní ADO.NET Entity Framework s Windows Workflow Foundation pro zjednodušení přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="c86bd-103">This sample shows how to use the ADO.NET Entity Framework with Windows Workflow Foundation to simplify data access.</span></span>  
  
 <span data-ttu-id="c86bd-104">ADO.NET Entity Framework umožňuje vývojářům pracovat s daty ve formě objektů specifického pro doménu, vlastnosti a vztahy, jako je například zákazníky, objednávky, podrobnostmi o objednávce a vztahy mezi těmito entitami.</span><span class="sxs-lookup"><span data-stu-id="c86bd-104">The ADO.NET Entity Framework enables developers to work with data in the form of domain-specific objects, properties and relationships such as Customers, Orders, Order Details and the relationships between these entities.</span></span> <span data-ttu-id="c86bd-105">ADO.NET Entity Framework to dělá tím, že poskytuje úroveň abstrakce, která umožňuje programování v modelu koncepční aplikace namísto programování přímo proti schématu relační úložiště.</span><span class="sxs-lookup"><span data-stu-id="c86bd-105">The ADO.NET Entity Framework does this by providing a level of abstraction that enables programming against a conceptual application model instead of programming directly against a relational storage schema.</span></span> <span data-ttu-id="c86bd-106">Další informace o rozhraní ADO.NET Entity Framework najdete v tématu [ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkId=165549).</span><span class="sxs-lookup"><span data-stu-id="c86bd-106">For more information about the ADO.NET Entity Framework see [ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkId=165549).</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="c86bd-107">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c86bd-107">Sample details</span></span>  
 <span data-ttu-id="c86bd-108">Tento příklad používá `Northwind` databáze a obsahuje skripty pro vytváření a odebírání `Northwind` databáze (Setup.cmd a Cleanup.cmd).</span><span class="sxs-lookup"><span data-stu-id="c86bd-108">This sample uses the `Northwind` database and includes scripts for creating and removing the `Northwind` database (Setup.cmd and Cleanup.cmd).</span></span> <span data-ttu-id="c86bd-109">Projekty v této ukázce zahrnovat na základě datového modelu Entity `Northwind` databáze.</span><span class="sxs-lookup"><span data-stu-id="c86bd-109">The projects in this sample include an Entity Data Model based on the `Northwind` database.</span></span> <span data-ttu-id="c86bd-110">Model lze najít otevřením `Northwind.edmx` souboru, který je součástí projektu.</span><span class="sxs-lookup"><span data-stu-id="c86bd-110">You can find the model by opening the `Northwind.edmx` file that is included in the project.</span></span> <span data-ttu-id="c86bd-111">Toto je model, který definuje tvar objektů, které lze přistupovat pomocí rozhraní ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c86bd-111">This is the model that defines the shape of the objects that can be accessed using the ADO.NET Entity Framework.</span></span>  
  
 <span data-ttu-id="c86bd-112">V této ukázce jsou zahrnuty následující činnosti:</span><span class="sxs-lookup"><span data-stu-id="c86bd-112">The following activities are included in this sample:</span></span>  
  
-   <span data-ttu-id="c86bd-113">`EntitySQLQuery`: `EntitySQLQuery` Aktivity umožňuje načíst objekty z databáze na základě řetězce dotazu Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="c86bd-113">`EntitySQLQuery`: The `EntitySQLQuery` activity allows you to retrieve objects from the database based on an Entity SQL query string.</span></span> <span data-ttu-id="c86bd-114">Entita SQL je úložiště nezávislé jazyk podobný SQL a umožňuje zadat dotazy na základě Koncepční model a entity, které jsou součástí modelu nebo domény.</span><span class="sxs-lookup"><span data-stu-id="c86bd-114">Entity SQL is a store independent language that is similar to SQL and it allows you to specify queries based on the conceptual model and the entities that are a part of the model or domain.</span></span> <span data-ttu-id="c86bd-115">Další informace o jazyk Entity SQL najdete v tématu [jazyk Entity SQL](https://go.microsoft.com/fwlink/?LinkId=165646).</span><span class="sxs-lookup"><span data-stu-id="c86bd-115">For more information about Entity SQL Language, see [Entity SQL Language](https://go.microsoft.com/fwlink/?LinkId=165646).</span></span>  
  
-   <span data-ttu-id="c86bd-116">`EntityLinqQuery`: Tato aktivita umožňuje načíst objekty z databáze na základě dotazu LINQ nebo predikátu.</span><span class="sxs-lookup"><span data-stu-id="c86bd-116">`EntityLinqQuery`: This activity allows you to retrieve objects from the database based on a LINQ query or predicate.</span></span>  
  
-   <span data-ttu-id="c86bd-117">`EntityAdd`: `EntityAdd` Aktivity umožňuje přidat entitu nebo kolekci entit v databázi.</span><span class="sxs-lookup"><span data-stu-id="c86bd-117">`EntityAdd`: The `EntityAdd` activity allows you to add an entity or a collection of entities to the database.</span></span>  
  
-   <span data-ttu-id="c86bd-118">`EntityDelete`: `EntityDelete` Aktivity můžete z databáze odstranit entitu nebo kolekci entit.</span><span class="sxs-lookup"><span data-stu-id="c86bd-118">`EntityDelete`: The `EntityDelete` activity allows you to delete an entity or a collection of entities from the database.</span></span>  
  
-   <span data-ttu-id="c86bd-119">`ObjectContextScope`: Výše uvedené činnosti jde použít jenom v rámci `ObjectContextScope` instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="c86bd-119">`ObjectContextScope`: The previously mentioned activities can only be used within a containing `ObjectContextScope` activity instance.</span></span> <span data-ttu-id="c86bd-120">`ObjectContextScope` Aktivita nastaví připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="c86bd-120">The `ObjectContextScope` activity sets up the connection to the database.</span></span> <span data-ttu-id="c86bd-121">Vyžaduje připojovací řetězec (tj. buď je předán nebo načten pomocí možnosti nastavení konfiguračního souboru).</span><span class="sxs-lookup"><span data-stu-id="c86bd-121">It requires a connection string (that is either passed in or retrieved using a configuration file setting).</span></span> <span data-ttu-id="c86bd-122">`ObjectContextScope` Aktivity usnadňuje provádění skupina souvisejících operací s entitami.</span><span class="sxs-lookup"><span data-stu-id="c86bd-122">The `ObjectContextScope` activity makes it easy to perform a group of related operations on entities.</span></span> <span data-ttu-id="c86bd-123">Tento obor udržuje aktivní připojení, proto je rozsah uchování č.</span><span class="sxs-lookup"><span data-stu-id="c86bd-123">Because this scope maintains an active connection, it is a No Persist scope.</span></span> <span data-ttu-id="c86bd-124">Kromě toho, kdy `ObjectContextScope` výstupů aktivity, všechny změny provedené na objekty, které jsou načteny automaticky pomocí Entity aktivity v daném oboru získat trvalá zpět do databáze a explicitní nebo následné nic dělat. k uložení objektů zpět do databáze.</span><span class="sxs-lookup"><span data-stu-id="c86bd-124">In addition, when the `ObjectContextScope` activity exits, any changes that are made to objects retrieved using Entity Activities within that scope automatically get persisted back to the database, and no explicit or subsequent action is required to save objects back to the database.</span></span>  
  
## <a name="using-the-entity-activities"></a><span data-ttu-id="c86bd-125">Pomocí aktivity entit</span><span class="sxs-lookup"><span data-stu-id="c86bd-125">Using the entity activities</span></span>  
 <span data-ttu-id="c86bd-126">Následující fragmenty kódu ukazují, jak používat entity aktivity uvedené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="c86bd-126">The following code snippets demonstrate how to use the entity activities presented in this sample.</span></span>  
  
### <a name="entitysql"></a><span data-ttu-id="c86bd-127">EntitySql</span><span class="sxs-lookup"><span data-stu-id="c86bd-127">EntitySql</span></span>  
 <span data-ttu-id="c86bd-128">Následující fragment kódu ukazuje, jak zadávat dotazy na všechny zákazníky v Londýně, seřazené podle názvu a jak k iteraci v rámci seznam zákazníků.</span><span class="sxs-lookup"><span data-stu-id="c86bd-128">The code snippet below shows how to query all customers in London sorted by name and how to iterate through the list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>();  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>();  
  
// create and return the workflow  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
        {  
            Activities =   
                {               
                    new WriteLine { Text = "Executing query" },                            
                    // query for all customers that are in london   
                    new EntitySqlQuery<Customer>  
                    {  
                        EntitySql =  @"SELECT VALUE Customer   
                                        FROM NorthwindEntities.Customers AS Customer   
                                        WHERE Customer.City = 'London'   
                                        ORDER BY Customer.ContactName",  
                        Result = londonCustomers  
                    },  
  
                    // iterate through the list of customers and display them   
                    new ForEach<Customer>  
                    {                                      
                        Values = londonCustomers,  
                        Body = new ActivityAction<Customer>  
                        {  
                            Argument = iterationVariable,  
                            Handler = new WriteLine   
                            {   
                                  Text = new InArgument<String>(e =>    
                                              iterationVariable.Get(e).ContactName)   
                            }  
                        }  
                    }  
                }  
        }                 
};     
```  
  
### <a name="entitylinqquery"></a><span data-ttu-id="c86bd-129">EntityLinqQuery</span><span class="sxs-lookup"><span data-stu-id="c86bd-129">EntityLinqQuery</span></span>  
 <span data-ttu-id="c86bd-130">Následující fragment kódu ukazuje, jak zadávat dotazy na všechny zákazníky v Londýně a jak k iteraci v rámci výsledný seznam zákazníků.</span><span class="sxs-lookup"><span data-stu-id="c86bd-130">The code snippet below shows how to query all customers in London and how to iterate through the resulting list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>() { Name = "LondonCustomers" };  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>() { Name = "iterationVariable" };  
  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // return all the customers that match with the provided Linq predicate  
            new EntityLinqQuery<Customer>  
            {   
                Predicate = new LambdaValue<Func<Customer, bool>>(  
                          ctx => new Func<Customer, bool>(c => c.City.Equals("London"))),                              
                Result = londonCustomers  
            },  
  
            // iterate through the list of customers and display in the console  
            new ForEach<Customer>  
            {                                      
                Values = londonCustomers,  
                Body = new ActivityAction<Customer>  
                {  
                    Argument = iterationVariable,  
                    Handler = new WriteLine   
                    {   
                        Text = new InArgument<String>(e =>   
                                      iterationVariable.Get(e).ContactName)   
                    }  
                }  
            }  
        }  
    }  
};  
```  
  
### <a name="entityadd"></a><span data-ttu-id="c86bd-131">EntityAdd</span><span class="sxs-lookup"><span data-stu-id="c86bd-131">EntityAdd</span></span>  
 <span data-ttu-id="c86bd-132">Následující fragment kódu ukazuje, jak přidat záznam OrderDetail do existující objednávky.</span><span class="sxs-lookup"><span data-stu-id="c86bd-132">The code snippet below shows how to add an OrderDetail record to an existing Order.</span></span>  
  
```  
Variable<IEnumerable<Order>> orders = new Variable<IEnumerable<Order>>();  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();  
Variable<Order> order = new Variable<Order>();  
Variable<OrderDetail> orderDetail = new Variable<OrderDetail>();              
  
return new ObjectContextScope  
{  
    Variables = { order, orders, orderDetail, orderDetails },  
    ContainerName = "NorthwindEntities",  
    ConnectionString = new InArgument<string>(connStr),                  
    Body = new Sequence  
    {                      
        Activities =   
        {                            
           // get the order where we want to add the detail  
           new EntitySqlQuery<Order>  
           {  
               EntitySql =    
                    @"SELECT VALUE [Order]  
                      FROM NorthwindEntities.Orders as [Order]  
                      WHERE Order.OrderID == 10249",  
               Result = orders  
           },  
  
           // store the order in a variable  
           new Assign<Order>   
           {  
               To = new OutArgument<Order>(order),  
               Value = new InArgument<Order>(c => orders.Get(c).First<Order>())  
           },  
  
           // add the detail to the order  
           new EntityAdd<OrderDetail>  
           {  
               Entity = new InArgument<OrderDetail>(c =>   
                                         new OrderDetail {   
                                                  OrderID=10249, ProductID=11,   
                                                  Quantity=1, UnitPrice = 15,   
                                                  Discount = 0, Order = order.Get(c) })  
           }  
        }  
    }  
};  
```  
  
### <a name="entitydelete"></a><span data-ttu-id="c86bd-133">EntityDelete</span><span class="sxs-lookup"><span data-stu-id="c86bd-133">EntityDelete</span></span>  
 <span data-ttu-id="c86bd-134">Následující fragment kódu ukazuje, jak odstranit existující záznam OrderDetail v pořadí (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="c86bd-134">The code snippet below shows how to delete an existing OrderDetail record in an Order (if it exists).</span></span>  
  
```  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();              
  
return new ObjectContextScope  
{  
    Variables = { orderDetails },  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // find the entitiy to be deleted (order detail for product 11 in order 10249)  
            new EntitySqlQuery<OrderDetail>  
            {  
                EntitySql = @"SELECT VALUE OrderDetail  
                                FROM NorthwindEntities.OrderDetails as OrderDetail  
                               WHERE OrderDetail.OrderID == 10249   
                                 AND OrderDetail.ProductID == 11",  
                Result = orderDetails  
            },  
  
            // if the order detail is found, delete it, otherwise, display a message  
            new If  
            {  
                Condition = new InArgument<bool>(c=>orderDetails.Get(c).Count() > 0),  
                Then = new Sequence  
                {   
                    Activities =   
                    {                                      
                        new EntityDelete<OrderDetail>  
                        {  
                            Entity = new InArgument<OrderDetail>(c =>   
                                              orderDetails.Get(c).First<OrderDetail>())  
                        },  
                    }  
                },                              
                Else = new WriteLine { Text = "Order Detail for Deleting not found" }                              
            }                                                  
        }  
    }  
};  
```  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="c86bd-135">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="c86bd-135">To use this sample</span></span>  
 <span data-ttu-id="c86bd-136">Je nutné vytvořit `Northwind` databázi ve vaší místní instance serveru SQL Express před spuštěním této ukázky.</span><span class="sxs-lookup"><span data-stu-id="c86bd-136">You must create the `Northwind` database in your local SQL server Express instance before running this sample.</span></span>  
  
#### <a name="to-set-up-the-northwind-database"></a><span data-ttu-id="c86bd-137">K nastavení databáze Northwind</span><span class="sxs-lookup"><span data-stu-id="c86bd-137">To set up the Northwind database</span></span>  
  
1.  <span data-ttu-id="c86bd-138">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="c86bd-138">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="c86bd-139">V novém okně příkazovém řádku přejděte do složky EntityActivities\CS.</span><span class="sxs-lookup"><span data-stu-id="c86bd-139">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="c86bd-140">Typ `setup.cmd` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="c86bd-140">Type `setup.cmd` and press ENTER.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="c86bd-141">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="c86bd-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="c86bd-142">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení EntityActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="c86bd-142">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EntityActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="c86bd-143">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="c86bd-143">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c86bd-144">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="c86bd-144">To run the solution, press CTRL+F5.</span></span>  
  
 <span data-ttu-id="c86bd-145">Po spuštění této ukázky se můžete chtít odebrat `Northwind` databáze.</span><span class="sxs-lookup"><span data-stu-id="c86bd-145">After running this sample, you may want to remove the `Northwind` database.</span></span>  
  
#### <a name="to-uninstall-the-northwind-database"></a><span data-ttu-id="c86bd-146">Chcete-li odinstalovat databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="c86bd-146">To uninstall the Northwind database</span></span>  
  
1.  <span data-ttu-id="c86bd-147">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="c86bd-147">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="c86bd-148">V novém okně příkazovém řádku přejděte do složky EntityActivities\CS.</span><span class="sxs-lookup"><span data-stu-id="c86bd-148">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="c86bd-149">Typ `cleanup.cmd` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="c86bd-149">Type `cleanup.cmd` and press ENTER.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c86bd-150">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="c86bd-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c86bd-151">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c86bd-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c86bd-152">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c86bd-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c86bd-153">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c86bd-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`