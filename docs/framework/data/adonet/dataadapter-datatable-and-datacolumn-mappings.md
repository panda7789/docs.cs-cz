---
title: Mapování adaptéru dat, datové tabulky a datového sloupce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: a9c81c8554c0fb393c10ed69f84c8b2d936ec1e6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040131"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Mapování adaptéru dat, datové tabulky a datového sloupce
Objekt **DataAdapter** obsahuje kolekci nula nebo více <xref:System.Data.Common.DataTableMapping> objektů ve vlastnosti **vlastnosti TableMappings** . **DataTableMapping** poskytuje mapování mezi daty vrácenými z dotazu na zdroj dat a <xref:System.Data.DataTable>. Název **DataTableMapping** může být předán namísto názvu **DataTable** do metody **Fill** objektu **DataAdapter**. Následující příklad vytvoří **DataTableMapping** s názvem **AuthorsMapping** pro tabulku **autoři** .  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 **DataTableMapping** umožňuje používat názvy sloupců v **objektu DataTable** , které se liší od těch v databázi. Objekt **DataAdapter** používá mapování, aby odpovídal sloupcům, když je tabulka aktualizována.  
  
 Pokud nezadáte **TableName** nebo **DataTableMapping** název při volání metody **Fill** nebo **Update** pro **Vlastnost DataAdapter**, modul **DataAdapter** vyhledá **DataTableMapping** s názvem "Table". Pokud tento **DataTableMapping** neexistuje, **TableName** **objektu DataTable** je "Table". Výchozí **DataTableMapping** můžete zadat tak, že vytvoříte **DataTableMapping** s názvem "Table".  
  
 Následující příklad kódu vytvoří **DataTableMapping** (z oboru názvů <xref:System.Data.Common>) a nastaví ho jako výchozí mapování pro zadaný objekt **DataAdapter** pojmenováním "Table". Příklad pak mapuje sloupce z první tabulky ve výsledku dotazu (tabulka **zákazníci** databáze **Northwind** ) na sadu více uživatelsky přívětivých názvů v tabulce **Northwind Customers** v <xref:System.Data.DataSet>. Pro sloupce, které nejsou namapované, se použije název sloupce ze zdroje dat.  
  
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
  
 V pokročilejších situacích se můžete rozhodnout, že chcete, aby stejný objekt **DataAdapter** podporoval načítání různých tabulek s různými mapováními. Uděláte to tak, že jednoduše přidáte další objekty **DataTableMapping** .  
  
 Když je metoda **Fill** předána instanci **datové sady** a názvu **DataTableMapping** , pokud se používá mapování s tímto názvem, je použito. v opačném případě se použije **DataTable** s tímto názvem.  
  
 V následujících příkladech je vytvořen **DataTableMapping** s názvem **Customers** a názvem **DataTable** **BizTalkSchema**. Příklad pak mapuje řádky vrácené příkazem SELECT do **objektu DataTable** **BizTalkSchema** .  
  
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
> Pokud není zadán název zdrojového sloupce pro mapování sloupce nebo není zadán název zdrojové tabulky pro mapování tabulky, budou automaticky generovány výchozí názvy. Pokud není zadán zdrojový sloupec pro mapování sloupce, mapování sloupce má přiřazený výchozí název **SourceColumn** *N,* počínaje **SourceColumn1**. Pokud se pro mapování tabulky nezadá žádný název zdrojové tabulky, mapování tabulky má podobu přírůstkového výchozího názvu **zdroje** *N*, počínaje **SourceTable1**.  
  
> [!NOTE]
> Doporučujeme vyhnout se konvenci pojmenování hodnoty **SourceColumn** *N* pro mapování sloupce nebo **zdrojovou** *N* pro mapování tabulky, protože název, který zadáte, může být v konfliktu s existujícím výchozím názvem mapování sloupce v  **Název parametru ColumnMappingcollection** nebo mapování tabulky v **DataTableMappingCollection**. Pokud zadaný název již existuje, bude vyvolána výjimka.  
  
## <a name="handling-multiple-result-sets"></a>Zpracování více sad výsledků  
 Pokud **vlastnost SelectCommand** vrátí více tabulek, **vyplní** automaticky názvy tabulek s přírůstkovým hodnotami pro tabulky v **datové sadě**počínaje zadaným názvem tabulky a pokračuje ve formuláři **TableName** . *N*, počínaje **TableName1**. Mapování tabulek můžete použít k mapování automaticky generovaného názvu tabulky na název, který chcete zadat pro tabulku v **datové sadě**. Například pro **vlastnost SelectCommand** , která vrací dvě tabulky, **zákazníky** a **objednávky**, vydejte následující volání k **vyplnění**.  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 V **datové sadě**jsou vytvořeny dvě tabulky: **Customers** a **Customers1**. Mapování tabulek můžete použít k zajištění toho, aby se druhá tabulka jmenovala **Orders** místo **Customers1**. Chcete-li to provést, namapujte zdrojovou tabulku **Customers1** na **objednávky**tabulky **DataSet** , jak je znázorněno v následujícím příkladu.  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a>Viz také:

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Přehled ADO.NET](ado-net-overview.md)
