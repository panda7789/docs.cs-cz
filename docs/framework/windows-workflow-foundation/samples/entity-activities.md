---
title: Entity aktivity
ms.date: 03/30/2017
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
ms.openlocfilehash: 96301c15b849749299e744a435068c3ec9be2e3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519133"
---
# <a name="entity-activities"></a>Entity aktivity
Tento příklad ukazuje použití ADO.NET Entity Framework pro zjednodušení přístupu k datům s Windows Workflow Foundation.  
  
 ADO.NET Entity Framework umožňuje vývojářům pracovat s daty v podobě objektů specifické pro doménu, vlastností a vztahů například zákazníky, objednávky, podrobnosti o pořadí a vztahy mezi tyto entity. ADO.NET Entity Framework tomu tím, že poskytuje úroveň abstrakce, která umožňuje programování s koncepční aplikační model místo programování přímo proti schématu relační úložiště. Další informace o ADO.NET Entity Framework najdete [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V tomto příkladu `Northwind` databáze a obsahuje skripty pro vytváření a odebrání `Northwind` databáze (Setup.cmd a Cleanup.cmd). Projekty v této ukázce obsahovat datový Model Entity na základě `Northwind` databáze. Model můžete najít tak, že otevřete `Northwind.edmx` soubor, který je zahrnutý v projektu. Toto je model, který definuje tvar objektů, které lze přistupovat pomocí ADO.NET Entity Framework.  
  
 Tyto aktivity jsou zahrnuty v této ukázce:  
  
-   `EntitySQLQuery`: `EntitySQLQuery` Aktivity umožňuje načíst objekty z databáze podle řetězce dotazu Entity SQL. Umožňuje zadat dotazy na základě konceptuálního modelu a entitami, které jsou součástí domény nebo model Entity SQL je úložiště nezávislé jazyk, který je podobný SQL. Další informace o jazyce SQL Entity najdete v tématu [jazyk SQL Entity](http://go.microsoft.com/fwlink/?LinkId=165646).  
  
-   `EntityLinqQuery`: Tato aktivita umožňuje načíst objekty z databáze na základě dotaz LINQ nebo predikátu.  
  
-   `EntityAdd`: `EntityAdd` Aktivity umožňuje přidat do databáze, entity nebo kolekci entit.  
  
-   `EntityDelete`: `EntityDelete` Aktivitu můžete z databáze odstranit entity nebo kolekci entit.  
  
-   `ObjectContextScope`: Výše uvedených aktivity lze použít pouze v rámci obsahujícího `ObjectContextScope` instance aktivity. `ObjectContextScope` Aktivita nastaví připojení k databázi. Vyžaduje připojovací řetězec (který je buď předaná nebo pomocí souboru nastavení konfigurace). `ObjectContextScope` Aktivity usnadňuje provádění skupinu související operací na entity. Vzhledem k tomuto oboru udržuje aktivního připojení, je obor zachovat ne. Kromě toho, když `ObjectContextScope` aktivity ukončí, veškeré změny, které jsou provedené na objektech pomocí Entity aktivity v rámci tohoto oboru automaticky načíst získat trvalá zpět do databáze a žádné explicitní nebo následné akce je potřeba uložit objekty zpět do databáze.  
  
## <a name="using-the-entity-activities"></a>Pomocí aktivity entity  
 Následující fragmenty kódu ukazují, jak používat aktivity entity uvedené v této ukázce.  
  
### <a name="entitysql"></a>EntitySql  
 Následující fragment kódu ukazuje, jak dotazovat všem zákazníkům v Londýně seřazené podle názvu a jak k iteraci v rámci seznamu zákazníků.  
  
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
 Následující fragment kódu ukazuje, jak dotazovat všem zákazníkům v Londýně a jak k iteraci v rámci výsledného seznamu zákazníků.  
  
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
 Následující fragment kódu ukazuje, jak přidat záznam OrderDetail do existujícího pořadí.  
  
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
 Následující fragment kódu ukazuje, jak k odstranění existujícího záznamu OrderDetail v pořadí (pokud existuje).  
  
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
 Je nutné vytvořit `Northwind` databáze ve vaší místní instanci serveru SQL Express před spuštěním této ukázce.  
  
#### <a name="to-set-up-the-northwind-database"></a>K nastavení databáze Northwind  
  
1.  Otevřete příkazový řádek.  
  
2.  V novém okně příkazového řádku přejděte do složky EntityActivities\CS.  
  
3.  Typ `setup.cmd` a stiskněte klávesu ENTER.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení EntityActivities.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
 Po spuštění této ukázce, můžete chtít odebrat `Northwind` databáze.  
  
#### <a name="to-uninstall-the-northwind-database"></a>Chcete-li odinstalovat databáze Northwind  
  
1.  Otevřete příkazový řádek.  
  
2.  V novém okně příkazového řádku přejděte do složky EntityActivities\CS.  
  
3.  Typ `cleanup.cmd` a stiskněte klávesu ENTER.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`