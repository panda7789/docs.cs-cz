---
title: "Omezení DataTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 500dad1699843bae04aea6d5c16a1ccf53bb102a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="datatable-constraints"></a>Omezení DataTable
Omezení můžete vynutit omezení na datech v <xref:System.Data.DataTable>, aby udržení integrity dat. Omezení je automatické pravidlo použít na sloupec nebo související sloupce, který určuje postup, když je nějakým způsobem změnit hodnotu v řádku. Vynutí se omezení při `System.Data.DataSet.EnforceConstraints` vlastnost <xref:System.Data.DataSet> je **true**. Příklad kódu, který ukazuje, jak nastavit `EnforceConstraints` vlastnost, najdete v článku <xref:System.Data.DataSet.EnforceConstraints%2A> referenční téma.  
  
 Existují dva typy omezení v ADO.NET: <xref:System.Data.ForeignKeyConstraint> a <xref:System.Data.UniqueConstraint>. Ve výchozím nastavení, obě omezení jsou vytvořeny automaticky při vytvoření vztahu mezi dvěma nebo více tabulek přidáním <xref:System.Data.DataRelation> k **datovou sadu**. Toto chování však můžete zakázat zadáním **createConstraints** = **false** při vytváření vztah.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 A **vlastnosti ForeignKeyConstraint** vynucuje pravidla o tom, jak rozšířit aktualizace a odstranění pro tabulky v relaci. Pokud hodnotu v řádku jedna tabulka je aktualizovat ani odstranit a stejné hodnoty se také používá v jednom nebo více souvisejících tabulek, například **vlastnosti ForeignKeyConstraint** Určuje, co se stane, že v související tabulky.  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> a <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> vlastnosti **vlastnosti ForeignKeyConstraint** definovat akce, které mají být provedeny, když se uživatel pokusí provést odstranění nebo aktualizaci řádku související tabulky. Následující tabulka popisuje různá nastavení, které jsou k dispozici pro **DeletRule** a **UpdateRule** vlastnosti **vlastnosti ForeignKeyConstraint**.  
  
|Nastavení pravidla|Popis|  
|------------------|-----------------|  
|**Cascade**|Odstranění nebo aktualizaci související řádky.|  
|**SetNull**|Nastavení hodnot v související řádky, které **DBNull**.|  
|**SetDefault**|Nastavte hodnoty v související řádky na výchozí hodnotu.|  
|**None**|Na související řádky provádět žádnou akci. Toto nastavení je výchozí.|  
  
 A **vlastnosti ForeignKeyConstraint** můžete omezit, a také rozšířit, změny související sloupce. V závislosti na vlastnosti nastavit pro **vlastnosti ForeignKeyConstraint** sloupce, pokud **EnforceConstraints** vlastnost **datovou sadu** je **true**, provádění některých operací na řádek nadřazené bude mít za následek výjimku. Například pokud **DeletRule** vlastnost **vlastnosti ForeignKeyConstraint** je **žádné**, nadřazený řádek nelze odstranit, pokud má všechny podřízené řádky.  
  
 Můžete vytvořit omezení cizího klíče mezi jednoho sloupce nebo pole sloupců pomocí **vlastnosti ForeignKeyConstraint** konstruktor. Předat výsledná **vlastnosti ForeignKeyConstraint** do objektu **přidat** metoda v tabulce **omezení** vlastnost, která je **objektu ConstraintCollection**. Můžete také předat argumenty konstruktoru několik přetížení **přidat** metodu **objektu ConstraintCollection** k vytvoření **vlastnosti ForeignKeyConstraint**.  
  
 Při vytváření **vlastnosti ForeignKeyConstraint**, můžete předat **DeletRule** a **UpdateRule** hodnoty do konstruktoru jako argumenty, nebo můžete nastavit jako vlastnosti jako Následující příklad (kde **DeletRule** nastavena na hodnotu **žádné**).  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a>AcceptRejectRule  
 Změny na řádky nelze přijmout pomocí **metoda AcceptChanges** metoda nebo zrušené pomocí **RejectChanges** metodu **datovou sadu**, **DataTable**, nebo **DataRow**. Když **datovou sadu** obsahuje **ForeignKeyConstraints**, volajícím **metoda AcceptChanges** nebo **RejectChanges** metody vynucuje  **AcceptRejectRule**. **AcceptRejectRule** vlastnost **vlastnosti ForeignKeyConstraint** Určuje akci, která bude provedena na podřízených řádků při **metoda AcceptChanges** nebo  **RejectChanges** se volá na řádek nadřazené.  
  
 Následující tabulka uvádí nastavení k dispozici pro **AcceptRejectRule**.  
  
|Nastavení pravidla|Popis|  
|------------------|-----------------|  
|**Cascade**|Přijmout nebo odmítnout změny na podřízené řádky.|  
|**None**|V řádcích podřízené provádět žádnou akci. Toto nastavení je výchozí.|  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.ForeignKeyConstraint>, nastaví některé jeho vlastnosti, včetně <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>a přidává ji k <xref:System.Data.ConstraintCollection> z <xref:System.Data.DataTable> objektu.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint** objekt, který lze přiřadit jeden sloupec nebo pole sloupců **DataTable**, zajistí, že všechna data v zadaný sloupec nebo sloupce, bude jedinečný pro každého řádku. Jedinečné omezení sloupce nebo pole sloupců můžete vytvořit pomocí **UniqueConstraint** konstruktor. Předat výsledná **UniqueConstraint** do objektu **přidat** metoda v tabulce **omezení** vlastnost, která je **objektu ConstraintCollection**. Můžete také předat argumenty konstruktoru několik přetížení **přidat** metodu **objektu ConstraintCollection** k vytvoření **UniqueConstraint**. Při vytváření **UniqueConstraint** pro sloupec nebo sloupce, můžete volitelně můžete určit, zda sloupec nebo sloupce, primární klíč.  
  
 Můžete také vytvořit jedinečné omezení pro sloupec nastavením **jedinečný** vlastnost sloupce, který se **true**. Můžete taky nastavení **jedinečný** vlastnost jediný sloupec pro **false** odebere všechny jedinečné omezení, která mohou existovat. Definování sloupec nebo sloupce jako primární klíč pro tabulku automaticky vytvoří jedinečné omezení pro zadaný sloupec nebo sloupce. Pokud odeberete sloupce z **PrimaryKey** vlastnost **DataTable**, **UniqueConstraint** se odebere.  
  
 Následující příklad vytvoří **UniqueConstraint** pro dva sloupce **DataTable**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [Definice schématu datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
