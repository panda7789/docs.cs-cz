---
title: Vlastnost DataAdapter, datové tabulky a DataColumn mapování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6aaaa126a0b19300abc2c10b88b0e4ff39a3ad66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530428"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Vlastnost DataAdapter, datové tabulky a DataColumn mapování
A **DataAdapter** obsahuje kolekci nula nebo více <xref:System.Data.Common.DataTableMapping> objekty v jeho **TableMappings** vlastnost. A **DataTableMapping** poskytuje hlavní mapování mezi data vrácená z dotazu na zdroji dat a <xref:System.Data.DataTable>. **DataTableMapping** název mohou být předány místo **DataTable** název k **vyplnit** metodu **DataAdapter**. Následující příklad vytvoří **DataTableMapping** s názvem **AuthorsMapping** pro **autoři** tabulky.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping** vám umožní použít názvy sloupců **DataTable** , která se liší od těch, které v databázi. **DataAdapter** používá mapování tak, aby odpovídaly sloupce, když dojde k aktualizaci tabulky.  
  
 Pokud nezadáte **TableName** nebo **DataTableMapping** pojmenujte při volání **vyplnit** nebo **aktualizace** metodu  **Vlastnost DataAdapter**, **DataAdapter** vyhledá **DataTableMapping** s názvem "Table". Pokud to **DataTableMapping** buď neexistuje, **TableName** z **DataTable** je "Table". Můžete určit výchozí **DataTableMapping** tak, že vytvoříte **DataTableMapping** s názvem "Table".  
  
 Následující příklad kódu vytvoří **DataTableMapping** (z <xref:System.Data.Common> oboru názvů) a zpřístupňuje je výchozí mapování pro zadaný rozbočovač **DataAdapter** zadáním názvu "Table". V příkladu pak namapuje sloupce z první tabulky ve výsledku dotazu ( **zákazníkům** tabulku **Northwind** databáze) na sadu přívětivější názvy v **zákazníků Northwind**  v tabulku <xref:System.Data.DataSet>. Název sloupce ze zdroje dat se používá u sloupců, které nejsou namapované.  
  
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
  
 V rozšířené situacích může rozhodnout, který má stejný **DataAdapter** nepodporuje načtení různých tabulek s jinou mapování. K tomu jednoduše přidejte další **DataTableMapping** objekty.  
  
 Při **vyplnit** metodě je předána instance **datovou sadu** a **DataTableMapping** název, pokud se mapování s tímto názvem existuje, je použít jinak  **Objekt DataTable** s, který se používá název.  
  
 Následující příklady vytváří **DataTableMapping** s názvem **zákazníkům** a **DataTable** název **BizTalkSchema**. V příkladu pak namapuje řádky vrácené příkazu SELECT **BizTalkSchema** **DataTable**.  
  
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
>  Pokud není zadán název zdrojového sloupce pro mapování sloupců nebo není zadán název tabulky zdrojového mapování tabulky, budou automaticky generovány výchozími názvy. Pokud žádný zdrojový sloupec je zadán pro mapování sloupců, mapování sloupců je předána přírůstkové výchozí název **SourceColumn** *N,* počínaje **SourceColumn1**. Pokud název tabulky žádný zdroj není zadána pro mapování tabulky, mapování tabulek je předána přírůstkové výchozí název **SourceTable** *N*počínaje **SourceTable1**.  
  
> [!NOTE]
>  Doporučujeme vám, že byste se vyhnout zásadu vytváření názvů **SourceColumn** *N* pro mapování sloupců, nebo **SourceTable** *N* pro tabulku vzhledem k tomu, že zadáte název dojít ke konfliktu s existujícím názvem mapování výchozí sloupce v mapování **ColumnMappingCollection** nebo název mapování tabulky v **DataTableMappingCollection** . Pokud zadaný název již existuje, bude vyvolána výjimka.  
  
## <a name="handling-multiple-result-sets"></a>Zpracování více sad výsledků dotazu  
 Pokud vaše **SelectCommand** vrátí více tabulek, **vyplnit** automaticky vygeneruje názvy tabulek s přírůstkové hodnoty pro tabulky v **datovou sadu**počínaje Zadaný název tabulky a pokračuje na ve formě **TableName** *N*počínaje **TableName1**. Mapování tabulek můžete použít k mapování názvu automaticky vytvářené tabulky na název, který má zadané pro tabulku v **datovou sadu**. Třeba **SelectCommand** dvou tabulek, který vrací **zákazníkům** a **objednávky**, vydat následující volání do **vyplnit**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 Dvě tabulky vytvářejí **datovou sadu**: **Zákazníci** a **Customers1**. Mapování tabulek můžete použít k zajištění, že je v druhé tabulce s názvem **objednávky** místo **Customers1**. K tomuto účelu mapování zdrojové tabulky **Customers1** k **datovou sadu** tabulky **objednávky**, jak je znázorněno v následujícím příkladu.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>Viz také:
- [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
