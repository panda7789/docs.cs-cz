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
# <a name="entity-activities"></a>Aktivity entit
Tento příklad ukazuje způsob použití rozhraní ADO.NET Entity Framework s Windows Workflow Foundation pro zjednodušení přístupu k datům.  
  
 ADO.NET Entity Framework umožňuje vývojářům pracovat s daty ve formě objektů specifického pro doménu, vlastnosti a vztahy, jako je například zákazníky, objednávky, podrobnostmi o objednávce a vztahy mezi těmito entitami. ADO.NET Entity Framework to dělá tím, že poskytuje úroveň abstrakce, která umožňuje programování v modelu koncepční aplikace namísto programování přímo proti schématu relační úložiště. Další informace o rozhraní ADO.NET Entity Framework najdete v tématu [ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkId=165549).  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Tento příklad používá `Northwind` databáze a obsahuje skripty pro vytváření a odebírání `Northwind` databáze (Setup.cmd a Cleanup.cmd). Projekty v této ukázce zahrnovat na základě datového modelu Entity `Northwind` databáze. Model lze najít otevřením `Northwind.edmx` souboru, který je součástí projektu. Toto je model, který definuje tvar objektů, které lze přistupovat pomocí rozhraní ADO.NET Entity Framework.  
  
 V této ukázce jsou zahrnuty následující činnosti:  
  
-   `EntitySQLQuery`: `EntitySQLQuery` Aktivity umožňuje načíst objekty z databáze na základě řetězce dotazu Entity SQL. Entita SQL je úložiště nezávislé jazyk podobný SQL a umožňuje zadat dotazy na základě Koncepční model a entity, které jsou součástí modelu nebo domény. Další informace o jazyk Entity SQL najdete v tématu [jazyk Entity SQL](https://go.microsoft.com/fwlink/?LinkId=165646).  
  
-   `EntityLinqQuery`: Tato aktivita umožňuje načíst objekty z databáze na základě dotazu LINQ nebo predikátu.  
  
-   `EntityAdd`: `EntityAdd` Aktivity umožňuje přidat entitu nebo kolekci entit v databázi.  
  
-   `EntityDelete`: `EntityDelete` Aktivity můžete z databáze odstranit entitu nebo kolekci entit.  
  
-   `ObjectContextScope`: Výše uvedené činnosti jde použít jenom v rámci `ObjectContextScope` instance aktivity. `ObjectContextScope` Aktivita nastaví připojení k databázi. Vyžaduje připojovací řetězec (tj. buď je předán nebo načten pomocí možnosti nastavení konfiguračního souboru). `ObjectContextScope` Aktivity usnadňuje provádění skupina souvisejících operací s entitami. Tento obor udržuje aktivní připojení, proto je rozsah uchování č. Kromě toho, kdy `ObjectContextScope` výstupů aktivity, všechny změny provedené na objekty, které jsou načteny automaticky pomocí Entity aktivity v daném oboru získat trvalá zpět do databáze a explicitní nebo následné nic dělat. k uložení objektů zpět do databáze.  
  
## <a name="using-the-entity-activities"></a>Pomocí aktivity entit  
 Následující fragmenty kódu ukazují, jak používat entity aktivity uvedené v této ukázce.  
  
### <a name="entitysql"></a>EntitySql  
 Následující fragment kódu ukazuje, jak zadávat dotazy na všechny zákazníky v Londýně, seřazené podle názvu a jak k iteraci v rámci seznam zákazníků.  
  
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
  
### <a name="entitylinqquery"></a>EntityLinqQuery  
 Následující fragment kódu ukazuje, jak zadávat dotazy na všechny zákazníky v Londýně a jak k iteraci v rámci výsledný seznam zákazníků.  
  
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
  
### <a name="entityadd"></a>EntityAdd  
 Následující fragment kódu ukazuje, jak přidat záznam OrderDetail do existující objednávky.  
  
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
  
### <a name="entitydelete"></a>EntityDelete  
 Následující fragment kódu ukazuje, jak odstranit existující záznam OrderDetail v pořadí (pokud existuje).  
  
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
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
 Je nutné vytvořit `Northwind` databázi ve vaší místní instance serveru SQL Express před spuštěním této ukázky.  
  
#### <a name="to-set-up-the-northwind-database"></a>K nastavení databáze Northwind  
  
1.  Otevřete příkazový řádek.  
  
2.  V novém okně příkazovém řádku přejděte do složky EntityActivities\CS.  
  
3.  Typ `setup.cmd` a stiskněte klávesu ENTER.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení EntityActivities.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
 Po spuštění této ukázky se můžete chtít odebrat `Northwind` databáze.  
  
#### <a name="to-uninstall-the-northwind-database"></a>Chcete-li odinstalovat databázi Northwind  
  
1.  Otevřete příkazový řádek.  
  
2.  V novém okně příkazovém řádku přejděte do složky EntityActivities\CS.  
  
3.  Typ `cleanup.cmd` a stiskněte klávesu ENTER.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`