---
title: Omezení datových tabulek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 3f3055b11f0e682ae5a9578289e30dc2716343fe
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785399"
---
# <a name="datatable-constraints"></a>Omezení datových tabulek
Pomocí omezení můžete vynutit omezení pro data v <xref:System.Data.DataTable>nástroji, aby bylo možné zachovat integritu dat. Omezení je automatické pravidlo, které se použije u sloupce nebo souvisejících sloupců, které určuje průběh akce, když je hodnota řádku nějakým způsobem změněna. Omezení jsou vynutit, pokud `System.Data.DataSet.EnforceConstraints` vlastnost <xref:System.Data.DataSet> má **hodnotu true**. Příklad kódu, který ukazuje, jak nastavit `EnforceConstraints` vlastnost, <xref:System.Data.DataSet.EnforceConstraints%2A> naleznete v referenčním tématu.  
  
 Existují dva druhy omezení v ADO.NET: <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.UniqueConstraint>a. Ve výchozím nastavení se obě omezení vytvoří automaticky, když vytvoříte relaci mezi dvěma nebo více tabulkami přidáním <xref:System.Data.DataRelation> k **datové sadě**. Toto chování však můžete zakázat zadáním **createConstraints** = **false** při vytváření relace.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 **Objekt ForeignKeyConstraint** vynutila pravidla, jak se rozšíří aktualizace a odstraňování v souvisejících tabulkách. Například pokud je hodnota v řádku jedné tabulky aktualizována nebo odstraněna a tato hodnota se používá také v jedné nebo více souvisejících tabulkách, **Objekt ForeignKeyConstraint** určuje, co se stane v souvisejících tabulkách.  
  
 Vlastnosti <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> a <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> **Objekt ForeignKeyConstraint** definují akci, která má být provedena, když se uživatel pokusí odstranit nebo aktualizovat řádek v tabulce v relaci. Následující tabulka popisuje různá nastavení, která jsou k dispozici pro vlastnosti **DeleteRule** a **UpdateRule** **Objekt ForeignKeyConstraint**.  
  
|Nastavení pravidla|Popis|  
|------------------|-----------------|  
|**Nášejí**|Odstraní nebo aktualizuje související řádky.|  
|**SetNull**|Nastavte hodnoty v souvisejících řádcích na **DBNull**.|  
|**SetDefault**|Nastaví hodnoty v souvisejících řádcích na výchozí hodnotu.|  
|**Žádné**|Neprovádět žádnou akci na souvisejících řádcích. Toto nastavení je výchozí.|  
  
 **Objekt ForeignKeyConstraint** může omezit a rozšířit změny v souvisejících sloupcích. V závislosti na vlastnostech nastavených pro **Objekt ForeignKeyConstraint** sloupce platí, že pokud je vlastnost **EnforceConstraints** pro **datovou sadu** **true**, provádění určitých operací na nadřazeném řádku způsobí výjimku. Například pokud vlastnost **DeleteRule** třídy **Objekt ForeignKeyConstraint** je **none**, nadřazený řádek nelze odstranit, pokud má podřízené řádky.  
  
 Omezení cizího klíče můžete vytvořit mezi jednotlivými sloupci nebo mezi polem sloupců pomocí konstruktoru **Objekt ForeignKeyConstraint** . Výsledný objekt **Objekt ForeignKeyConstraint** předejte metodě **Add** vlastnosti **omezení** tabulky, což je objekt **ConstraintCollection**. Můžete také předat argumenty konstruktoru do několika přetížení metody **Add** třídy **ConstraintCollection** a vytvořit tak **Objekt ForeignKeyConstraint**.  
  
 Při vytváření **Objekt ForeignKeyConstraint**můžete do konstruktoru předat hodnoty **DeleteRule** a **UpdateRule** jako argumenty, nebo je můžete nastavit jako vlastnosti jako v následujícím příkladu (kde hodnota **DeleteRule** je nastavená na  **Žádný**).  
  
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
 Změny v řádcích lze přijmout pomocí metody **AcceptChanges** nebo zrušit pomocí metody **RejectChanges** **objektu DataSet**, **DataTable**nebo **DataRow**. Pokud **datová sada** obsahuje **ForeignKeyConstraints**, volání metod **AcceptChanges** nebo **RejectChanges** vynutila **AcceptRejectRule**. Vlastnost **AcceptRejectRule** třídy **Objekt ForeignKeyConstraint** určuje, která akce bude provedena na podřízených řádcích v případě, že je v nadřazeném řádku volána metoda **AcceptChanges** nebo **RejectChanges** .  
  
 V následující tabulce jsou uvedena dostupná nastavení pro **AcceptRejectRule**.  
  
|Nastavení pravidla|Popis|  
|------------------|-----------------|  
|**Nášejí**|Přijměte nebo odmítněte změny v podřízených řádcích.|  
|**Žádné**|Neprovádět žádnou akci s podřízenými řádky. Toto nastavení je výchozí.|  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.ForeignKeyConstraint>, nastaví několik vlastností, <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>včetně <xref:System.Data.ConstraintCollection> a, a přidá <xref:System.Data.DataTable> je do objektu.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 Objekt **UniqueConstraint** , který lze přiřadit buď k jednomu sloupci, nebo k poli sloupců v **objektu DataTable**, zajišťuje, aby všechna data v zadaném sloupci nebo sloupcích byla na řádku jedinečná. Můžete vytvořit jedinečné omezení pro sloupec nebo pole sloupců pomocí konstruktoru **UniqueConstraint** . Výsledný objekt **UniqueConstraint** předejte metodě **Add** vlastnosti **omezení** tabulky, což je objekt **ConstraintCollection**. Můžete také předat argumenty konstruktoru do několika přetížení metody **Add** třídy **ConstraintCollection** a vytvořit tak **UniqueConstraint**. Při vytváření **UniqueConstraint** pro sloupec nebo sloupce můžete volitelně zadat, zda se jedná o primární klíč sloupce nebo sloupce.  
  
 Můžete také vytvořit jedinečné omezení pro sloupec nastavením vlastnosti **Unique** sloupce na **hodnotu true**. Případně nastavení **jedinečné** vlastnosti jednoho sloupce na **hodnotu false** odebere všechna jedinečná omezení, která mohou existovat. Definování sloupce nebo sloupců jako primárního klíče pro tabulku vytvoří pro zadaný sloupec nebo sloupce automaticky jedinečné omezení. Odeberete-li sloupec z vlastnosti **PrimaryKey** objektu **DataTable**, dojde k odebrání **UniqueConstraint** .  
  
 Následující příklad vytvoří **UniqueConstraint** pro dva sloupce **objektu DataTable**.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [Definice schématu datové tabulky](datatable-schema-definition.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
