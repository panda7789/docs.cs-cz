---
title: Vytvoření datové tabulky
description: Naučte se vytvářet DataTable v ADO.NET, která představuje jednu tabulku relačních dat v paměti pro použití nezávisle nebo jinými .NET Framework objekty.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 335137eeef02e590539c6d83e46cb39901a1e03f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286918"
---
# <a name="creating-a-datatable"></a>Vytvoření datové tabulky
<xref:System.Data.DataTable>, Který představuje jednu tabulku relačních dat v paměti, lze vytvořit a použít nezávisle, nebo mohou být použity jinými .NET Framework objekty, nejčastěji jako člen <xref:System.Data.DataSet> .  
  
 Objekt **DataTable** lze vytvořit pomocí příslušného konstruktoru **DataTable** . Můžete ji přidat do **datové sady** pomocí metody **Add** pro její přidání do kolekce **tabulek** objektu **DataTable** .  
  
 Můžete také vytvořit objekty **DataTable** v rámci **datové sady** pomocí metod **Fill** nebo **FillSchema** objektu **DataAdapter** nebo z předdefinovaného nebo odvozeného schématu XML pomocí metod **ReadXml**, **ReadXmlSchema**a **InferXmlSchema** objektu **DataSet**. Všimněte si, že poté, co jste přidali **DataTable** jako člena kolekce **Tables** jedné **datové sady**, nelze ji přidat do kolekce tabulek žádné jiné **datové sady**.  
  
 Při prvním vytvoření **objektu DataTable**nemá schéma (to znamená struktury). Chcete-li definovat schéma tabulky, je nutné vytvořit a přidat <xref:System.Data.DataColumn> objekty do kolekce **Columns** v tabulce. Můžete také definovat sloupec primárního klíče pro tabulku a vytvořit a přidat objekty **omezení** do kolekce **omezení** v tabulce. Po definování schématu pro **objekt DataTable**můžete do tabulky přidat řádky dat přidáním objektů **DataRow** do kolekce **řádků** tabulky.  
  
 <xref:System.Data.DataTable.TableName%2A>Při vytváření **objektu DataTable**není nutné zadávat hodnotu vlastnosti. vlastnost lze zadat v jinou dobu nebo ji můžete ponechat prázdnou. Pokud však přidáte tabulku bez hodnoty **TableName** do **datové sady**, bude se tabulce předávat přírůstkový výchozí název tabulky*N*, počínaje "Table" pro TABLE0.  
  
> [!NOTE]
> Doporučujeme vyhnout se konvenci pojmenování tabulky*N*při zadání hodnoty **TableName** , protože název, který zadáte, může být v konfliktu s existujícím názvem výchozí tabulky v **datové sadě**. Pokud zadaný název již existuje, je vyvolána výjimka.  
  
 Následující příklad vytvoří instanci objektu **DataTable** a přiřadí mu název "Customers".  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Následující příklad vytvoří instanci **objektu DataTable** přidáním do kolekce **Tables** **objektu DataSet**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [Datové tabulky](datatables.md)
- [Naplnění datové sady z adaptéru dat](../populating-a-dataset-from-a-dataadapter.md)
- [Načtení datové sady z XML](loading-a-dataset-from-xml.md)
- [Načtení informací o schématu datové sady z XML](loading-dataset-schema-information-from-xml.md)
- [Přehled ADO.NET](../ado-net-overview.md)
