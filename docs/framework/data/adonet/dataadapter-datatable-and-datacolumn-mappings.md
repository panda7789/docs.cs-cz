---
title: Mapování adaptéru dat, datové tabulky a datového sloupce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6380dd0512bd7834f50b87f90f445cb01b7a8b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151556"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Mapování adaptéru dat, datové tabulky a datového sloupce
A **DataAdapter** obsahuje kolekci <xref:System.Data.Common.DataTableMapping> nula nebo více objektů v jeho **TableMappings** vlastnost. A **DataTableMapping** poskytuje hlavní mapování mezi daty vrácená z <xref:System.Data.DataTable>dotazu proti zdroji dat a . Název **DataTableMapping** může být předán místo názvu **DataTable** metodě **Fill** **dataadapter**. Následující příklad vytvoří **datatablemapping** s názvem **AuthorsMapping** pro tabulku **Autoři.**  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping** umožňuje používat názvy sloupců v **DataTable,** které se liší od těch v databázi. **DataAdapter** používá mapování tak, aby odpovídalo sloupcům při aktualizaci tabulky.  
  
 Pokud při volání metody **Fill** nebo **Update** **datového adaptéru**nezadáte název **TableName** nebo **DataTableMapping** , **hledá dataadapter** **datatablemapping** s názvem "Tabulka". Pokud **toto mapování DataTableMapping** neexistuje, **název_tabulky** **tabulka** je "Tabulka". Výchozí **mapování datatablemapping** můžete zadat vytvořením **datatablemappingu** s názvem "Tabulka".  
  
 Následující příklad kódu vytvoří **datatablemapping** <xref:System.Data.Common> (z oboru názvů) a znějí výchozím mapováním pro zadaný **adaptér DataAdapter** pojmenováním "Tabulka". Příklad pak mapuje sloupce z první tabulky ve výsledku dotazu (tabulka **Zákazníci** databáze **Northwind)** na sadu uživatelsky <xref:System.Data.DataSet>přívětivějších názvů v tabulce **Zákazníci Northwind** v tabulce . Pro sloupce, které nejsou mapovány, se používá název sloupce ze zdroje dat.  
  
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
  
 V pokročilejších situacích se můžete rozhodnout, že chcete, aby stejný **adaptér DataAdapter** podporoval načítání různých tabulek s různými mapováními. Chcete-li to provést, jednoduše přidejte další objekty **DataTableMapping.**  
  
 Když **fill** metoda je předána instance **DataSet** a **DataTableMapping** název, pokud mapování s tímto názvem existuje, že se používá; v opačném případě je **použita datatable** s tímto názvem.  
  
 Následující příklady vytvořit **DataTableMapping** s názvem **zákazníci** a **DataTable** název **BizTalkSchema**. Příklad pak mapuje řádky vrácené příkazem SELECT na **BizTalkSchema** **DataTable**.  
  
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
> Pokud pro mapování sloupců není zadán název zdrojového sloupce nebo není zadán název zdrojové tabulky pro mapování tabulky, budou automaticky generovány výchozí názvy. Pokud pro mapování sloupců není zadán žádný zdrojový sloupec, je mapování sloupců přidělen o zdrojový výchozí název **SourceColumn** *N,* počínaje **SourceColumn1**. Pokud pro mapování tabulky není zadán žádný název zdrojové tabulky, je mapování tabulky přidělen o zdrojový výchozí název **Table N** *N*, počínaje **SourceTable1**.  
  
> [!NOTE]
> Doporučujeme vyhnout se konvenci pojmenování **SourceColumn** *N* pro mapování sloupců nebo **SourceTable** *N* pro mapování tabulky, protože název, který zadáte, může být v konfliktu s existujícím výchozím názvem mapování sloupců v **kolekci ColumnMappingCollection** nebo název mapování tabulky v **datatablemappingcollectioncollection**. Pokud zadaný název již existuje, bude vyvolána výjimka.  
  
## <a name="handling-multiple-result-sets"></a>Zpracování více sad výsledků  
 Pokud příkaz **SelectCommand** vrátí více tabulek, **funkce Fill** automaticky vygeneruje názvy tabulek s přírůstkovými hodnotami pro tabulky v **datové sadě**, počínaje zadaným názvem tabulky a pokračováním ve formuláři **TableName** *N*, počínaje **názvem TableName1**. Mapování tabulek můžete použít k mapování automaticky generovaného názvu tabulky na název, který chcete zadat pro tabulku v **datové sadě**. Například pro **SelectCommand,** který vrací dvě tabulky, **Zákazníci** a **Objednávky**, vydat následující volání **Fill**.  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 Dvě tabulky jsou vytvořeny v **datové sadě**: **Zákazníci** a **Zákazníci1**. Mapování tabulek můžete použít k zajištění, že druhá tabulka je s názvem **Objednávky** místo **Zákazníci1**. Chcete-li to provést, namapujte zdrojovou tabulku **Zákazníci1** na **objednávky**tabulky **DataSet** , jak je znázorněno v následujícím příkladu.  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a>Viz také

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Přehled ADO.NET](ado-net-overview.md)
