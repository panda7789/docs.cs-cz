---
title: Omezení datových tabulek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: fa70af311d6b4fa4e17bb3ba6110e4cea420c34c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44200285"
---
# <a name="datatable-constraints"></a>Omezení datových tabulek
Můžete vynutit omezení na datech z tohoto omezení <xref:System.Data.DataTable>, aby bylo možné udržovat tak integritu dat. Omezení je automatické pravidlo použít na sloupec nebo souvisejících sloupců, která určuje kurz akce při hodnota řádku je nějakým způsobem změněna. Jsou vynucena omezení při `System.Data.DataSet.EnforceConstraints` vlastnost <xref:System.Data.DataSet> je **true**. Příklad kódu, který ukazuje, jak nastavit `EnforceConstraints` vlastnost, najdete v článku <xref:System.Data.DataSet.EnforceConstraints%2A> téma referenčních informací.  
  
 Existují dva typy omezení v ADO.NET: <xref:System.Data.ForeignKeyConstraint> a <xref:System.Data.UniqueConstraint>. Ve výchozím nastavení, obě omezení se vytvoří automaticky při vytvoření vztahu mezi dvěma nebo více tabulek tak, že přidáte <xref:System.Data.DataRelation> k **datovou sadu**. Toto chování však můžete zakázat tak, že zadáte **createConstraints** = **false** při vytváření vztahu.  
  
## <a name="foreignkeyconstraint"></a>Objekt ForeignKeyConstraint  
 A **Objekt ForeignKeyConstraint** vynucuje pravidla týkající se aktualizací a odstraňování souvisejících tabulkách jak nerozšíří. Pokud hodnotu v řádku jednu tabulku je aktualizovat ani odstranit a stejnou hodnotu se také používá v jednom nebo více souvisejících tabulek, například **Objekt ForeignKeyConstraint** Určuje, co se stane v souvisejících tabulkách.  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> a <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> vlastnosti **Objekt ForeignKeyConstraint** definujete akce, jež mají být provedeny, když se uživatel pokusí odstranit nebo aktualizovat řádek v související tabulce. Následující tabulka popisuje různá nastavení, které jsou k dispozici pro **DeletRule** a **UpdateRule** vlastnosti **Objekt ForeignKeyConstraint**.  
  
|Nastavení pravidla|Popis|  
|------------------|-----------------|  
|**Kaskádové**|Odstranit nebo aktualizovat související řádky.|  
|**SetNull**|Nastavení hodnot v související řádky **DBNull**.|  
|**SetDefault**|Nastavení hodnot v související řádky na výchozí hodnotu.|  
|**None**|Neprovádět žádnou akci na související řádky. Toto nastavení je výchozí.|  
  
 A **Objekt ForeignKeyConstraint** můžete omezit, stejně jako rozšíření, změny související sloupce. V závislosti na vlastnosti nastavené pro **Objekt ForeignKeyConstraint** sloupce, pokud **EnforceConstraints** vlastnost **datovou sadu** je **true**, provádění některých operací na nadřazený řádek bude mít za následek výjimku. Například pokud **DeletRule** vlastnost **Objekt ForeignKeyConstraint** je **žádný**, nadřazený řádek nelze odstranit, pokud má všechny podřízené řádky.  
  
 Můžete vytvořit omezení cizího klíče mezi jednoho sloupce nebo pole s použitím sloupců **Objekt ForeignKeyConstraint** konstruktoru. Předání výsledných **Objekt ForeignKeyConstraint** objektu **přidat** metoda v tabulce **omezení** vlastnost, která je **objektu ConstraintCollection**. Můžete také předat argumenty konstruktoru několik přetížení **přidat** metodu **objektu ConstraintCollection** k vytvoření **Objekt ForeignKeyConstraint**.  
  
 Při vytváření **Objekt ForeignKeyConstraint**, můžete předat **DeletRule** a **UpdateRule** hodnoty do konstruktoru jako argumenty, nebo můžete nastavit jako vlastnosti jako v následujícím příkladu (kde **DeletRule** nastavena na hodnotu **žádný**).  
  
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
 Jdou přijmout změny řádky pomocí **metoda AcceptChanges** metody nebo zrušené pomocí **RejectChanges** metodu **datovou sadu**, **DataTable**, nebo **DataRow**. Když **datovou sadu** obsahuje **ForeignKeyConstraints**, vyvolání **metoda AcceptChanges** nebo **RejectChanges** metody vynucuje  **AcceptRejectRule**. **AcceptRejectRule** vlastnost **Objekt ForeignKeyConstraint** Určuje akci, která se mají provést na podřízené řádky, kdy **metoda AcceptChanges** nebo  **RejectChanges** je volán na nadřazený řádek.  
  
 V následující tabulce jsou uvedeny dostupná nastavení **AcceptRejectRule**.  
  
|Nastavení pravidla|Popis|  
|------------------|-----------------|  
|**Kaskádové**|Přijmout nebo odmítnout změny podřízených řádků.|  
|**None**|Neprovádět žádnou akci na podřízených řádků. Toto nastavení je výchozí.|  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.ForeignKeyConstraint>, nastaví některé jeho vlastnosti, včetně <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>a přidá jej do <xref:System.Data.ConstraintCollection> z <xref:System.Data.DataTable> objektu.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint** objektu, který je možné přiřadit do jednoho sloupce nebo na pole sloupce ve **DataTable**, zajišťuje, že všechna data v zadaném sloupci nebo sloupcích jedinečná na každém řádku. Jedinečné omezení sloupce nebo pole sloupce můžete vytvořit pomocí **UniqueConstraint** konstruktoru. Předání výsledných **UniqueConstraint** objektu **přidat** metoda v tabulce **omezení** vlastnost, která je **objektu ConstraintCollection**. Můžete také předat argumenty konstruktoru několik přetížení **přidat** metodu **objektu ConstraintCollection** k vytvoření **UniqueConstraint**. Při vytváření **UniqueConstraint** pro sloupec nebo sloupce, Volitelně můžete zadat, zda sloupec nebo sloupce jsou primární klíč.  
  
 Omezení unique pro sloupec můžete vytvořit také tak, že nastavíte **jedinečné** vlastnost sloupec, který se **true**. Další možností nastavení **jedinečné** vlastnost jediný sloupec pro **false** odebere jedinečné omezení, která mohou existovat. Definice sloupce nebo sloupců jako primární klíč pro tabulku automaticky vytvoří jedinečné omezení pro zadaný sloupec nebo sloupce. Pokud odeberete sloupec z **PrimaryKey** vlastnost **DataTable**, **UniqueConstraint** se odebere.  
  
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
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
