---
title: DataAdapter DataTable a DataColumn mapování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 1b426dbcdc78ecfddeac003616993849ce60b89c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable a DataColumn mapování
A **DataAdapter** obsahuje kolekci nula nebo více <xref:System.Data.Common.DataTableMapping> objekty v jeho **vlastnosti TableMappings** vlastnost. A **DataTableMapping** poskytuje hlavní mapování mezi data vrácená z dotazu proti zdroji dat a <xref:System.Data.DataTable>. **DataTableMapping** název lze předat místě **DataTable** názvem k **vyplnění** metodu **DataAdapter**. Následující příklad vytvoří **DataTableMapping** s názvem **AuthorsMapping** pro **autoři** tabulky.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping** vám umožní použít názvy sloupců v **DataTable** , se liší od těch v databázi. **DataAdapter** používá mapování tak, aby odpovídaly sloupce při aktualizaci tabulky.  
  
 Pokud nezadáte **TableName** nebo **DataTableMapping** název při volání metody **vyplnění** nebo **aktualizace** metodu  **DataAdapter**, **DataAdapter** vyhledává **DataTableMapping** s názvem "Tabulka". Pokud tento **DataTableMapping** neexistuje, **TableName** z **DataTable** je "Tabulka". Můžete zadat výchozí **DataTableMapping** tak, že vytvoříte **DataTableMapping** s názvem "Tabulka".  
  
 Následující příklad kódu vytvoří **DataTableMapping** (z <xref:System.Data.Common> oboru názvů) a udělá z něj výchozí mapování pro zadaný **DataAdapter** zadáním názvu "Tabulky". V příkladu mapuje sloupce z tabulky první ve výsledku dotazu ( **zákazníci** tabulky **Northwind** databáze) na sadu více uživatelsky přívětivých názvů v **zákazníků Northwind**  tabulky v <xref:System.Data.DataSet>. Pro sloupce, které nejsou namapované je název sloupce ve zdroji dat použít.  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =   
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 V situacích, pokročilejší, můžete rozhodnout, který má stejné **DataAdapter** pro podporu načítání různých tabulek s jinou mapování. K tomu jednoduše přidejte další **DataTableMapping** objekty.  
  
 Když **vyplnění** metodě se předává instanci **datovou sadu** a **DataTableMapping** je název, pokud mapování se stejným názvem existuje, je použít; jinak hodnota  **DataTable** s, který se používá název.  
  
 Následující příklady vytváření **DataTableMapping** s názvem **zákazníci** a **DataTable** název **BizTalkSchema**. V příkladu mapuje řádky vrácené příkazem SELECT k **BizTalkSchema** **DataTable**.  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =   
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
>  Pokud není zadaný název zdrojového sloupce pro mapování sloupců nebo názvu zdrojové tabulky není součástí pro mapování tabulky, budou automaticky generovány výchozí názvy. Pokud je zdrojový sloupec zadaný pro mapování sloupců, mapování sloupců je zadána přírůstkové výchozí název **SourceColumn** *N,* počínaje **SourceColumn1**. Pokud je zadaný žádný parametr názvu zdrojové tabulky pro mapování tabulky, mapování tabulky, je zadána přírůstkové výchozí název **SourceTable** *N*, od verze **SourceTable1**.  
  
> [!NOTE]
>  Doporučujeme, abyste se zabránilo pojmenovávací konvenci **SourceColumn** *N* pro mapování sloupců, nebo **SourceTable** *N* pro tabulku mapování, protože název je zadat může dojít ke konfliktu s existujícím názvem mapování výchozí sloupec v **ColumnMappingCollection** nebo název tabulky mapování v **DataTableMappingCollection** . Pokud se zadaným názvem již existuje, bude vyvolána výjimka.  
  
## <a name="handling-multiple-result-sets"></a>Zpracování více sad výsledků dotazu  
 Pokud vaše **SelectCommand** vrátí více tabulek, **vyplnění** automaticky vygeneruje názvy tabulek s přírůstkové hodnoty pro tabulky v **datovou sadu**, od verze Zadaný název tabulky a budete pokračovat na ve formě **TableName** *N*, od verze **TableName1**. Mapování tabulky můžete použít k mapování názvu automaticky vytvářené tabulky název, který má zadaný pro tabulky **datovou sadu**. Například pro **SelectCommand** dvou tabulek, který vrací **zákazníci** a **objednávky**, vydávání následující volání **vyplnění**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 Dvě tabulky se vytváří v **datovou sadu**: **zákazníci** a **označena jako Zákazníci1**. Mapování tabulky můžete použít k zajištění, že je v druhé tabulce s názvem **objednávky** místo **označena jako Zákazníci1**. K tomuto účelu mapování zdrojové tabulky **označena jako Zákazníci1** k **datovou sadu** tabulky **objednávky**, jak je znázorněno v následujícím příkladu.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
