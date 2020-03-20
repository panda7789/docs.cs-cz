---
title: Omezení datových tabulek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151283"
---
# <a name="datatable-constraints"></a>Omezení datových tabulek
Omezení můžete použít k vynucení omezení <xref:System.Data.DataTable>dat v , za účelem zachování integrity dat. Omezení je automatické pravidlo použité na sloupec nebo související sloupce, které určuje průběh akce při změně hodnoty řádku. Omezení jsou vynucena, `System.Data.DataSet.EnforceConstraints` pokud <xref:System.Data.DataSet> je **vlastnost true**. Příklad kódu, který ukazuje, `EnforceConstraints` jak nastavit <xref:System.Data.DataSet.EnforceConstraints%2A> vlastnost, naleznete v tématu odkazu.  
  
 Existují dva druhy omezení v ADO.NET: <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.UniqueConstraint>a . Ve výchozím nastavení jsou obě omezení vytvořena automaticky při vytváření relace <xref:System.Data.DataRelation> mezi dvěma nebo více tabulkami přidáním a do **datové sady**. Toto chování však můžete zakázat zadáním **funkce createConstraints** = **false** při vytváření vztahu.  
  
## <a name="foreignkeyconstraint"></a>Foreignkeyconstraint  
 A **ForeignKeyConstraint** vynucuje pravidla o tom, jak jsou rozšířeny aktualizace a odstranění do souvisejících tabulek. Například pokud hodnota v řádku jedné tabulky je aktualizován nebo odstraněn a že stejná hodnota se používá také v jedné nebo více souvisejících tabulek, **ForeignKeyConstraint** určuje, co se stane v souvisejících tabulkách.  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> Vlastnosti <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> a **ForeignKeyConstraint** definovat akci, která má být provedena, když se uživatel pokusí odstranit nebo aktualizovat řádek v související tabulce. Následující tabulka popisuje různá nastavení, která jsou k dispozici pro vlastnosti **DeleteRule** a **UpdateRule** **služby ForeignKeyConstraint**.  
  
|Nastavení pravidla|Popis|  
|------------------|-----------------|  
|**Kaskády**|Odstranit nebo aktualizovat související řádky.|  
|**Nastavit hodnotu Null**|Nastavte hodnoty v souvisejících řádcích na **DBNull**.|  
|**Nastavit výchozí nastavení**|Nastavte hodnoty v souvisejících řádcích na výchozí hodnotu.|  
|**Žádné**|U souvisejících řádků neprovádějte žádnou akci. Toto nastavení je výchozí.|  
  
 A **ForeignKeyConstraint** můžete omezit, stejně jako šířit, změny související chvatcích. V závislosti na vlastnostech nastavených pro **ForeignKeyConstraint** sloupce, pokud **EnforceConstraints** vlastnost **DataSet** je **true**, provádění určitých operací na nadřazený řádek bude mít za následek výjimku. Například pokud **DeleteRule** vlastnost **ForeignKeyConstraint** je **None**, nadřazený řádek nelze odstranit, pokud má všechny podřízené řádky.  
  
 Můžete vytvořit omezení cizího klíče mezi jednotlivými sloupci nebo mezi pole sloupců pomocí konstruktoru **ForeignKeyConstraint.** Předajte výsledný objekt **ForeignKeyConstraint** metodě **Add** vlastnosti **Constraints** tabulky, která je **ConstraintCollection**. Můžete také předat argumenty konstruktoru na několik přetížení **Add** metoda **ConstraintCollection** vytvořit **ForeignKeyConstraint**.  
  
 Při vytváření **ForeignKeyConstraint**, můžete předat **DeleteRule** a **UpdateRule** hodnoty konstruktoru jako argumenty, nebo můžete nastavit jako vlastnosti jako v následujícím příkladu (kde **DeleteRule** hodnota je **nastavena**na none ).  
  
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
  
### <a name="acceptrejectrule"></a>PřijmoutOdmítnoucí pravidlo  
 Změny řádků lze přijmout pomocí metody **AcceptChanges** nebo zrušit pomocí metody **RejectChanges** **dataset**, **DataTable**nebo **DataRow**. Pokud **DataSet** obsahuje **ForeignKeyConstraints**, vyvolání **AcceptChanges** nebo **RejectChanges** metody vynucuje **AcceptRejectRule**. **AcceptRejectRule** vlastnost **ForeignKeyConstraint** určuje, která akce bude provedena na podřízené řádky při **AcceptChanges** nebo **RejectChanges** je volána na nadřazený řádek.  
  
 V následující tabulce jsou uvedena dostupná nastavení pravidla **AcceptRejectRule**.  
  
|Nastavení pravidla|Popis|  
|------------------|-----------------|  
|**Kaskády**|Přijměte nebo zamítněte změny podřízených řádků.|  
|**Žádné**|Neprovádějte žádnou akci na podřízených řádcích. Toto nastavení je výchozí.|  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.ForeignKeyConstraint>, nastaví několik jeho <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>vlastností, včetně <xref:System.Data.ConstraintCollection> , <xref:System.Data.DataTable> a přidá ji k objektu.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>Uniqueconstraint  
 Objekt **UniqueConstraint,** který lze přiřadit k jednomu sloupci nebo k poli sloupců v **tabulce DataTable**, zajišťuje, že všechna data v zadaném sloupci nebo sloupcích jsou jedinečná pro každý řádek. Pomocí konstruktoru **UniqueConstraint** můžete vytvořit jedinečné omezení pro sloupec nebo pole sloupců. Předá výsledný **Objekt UniqueConstraint** metodě **Add** **vlastnosti Constraints** tabulky, která je **ConstraintCollection**. Můžete také předat argumenty konstruktoru na několik přetížení **Add** metoda **ConstraintCollection** vytvořit **UniqueConstraint**. Při vytváření **jedinečného omezení** pro sloupec nebo sloupce můžete volitelně určit, zda jsou sloupce nebo sloupce primárním klíčem.  
  
 Můžete také vytvořit jedinečné omezení pro sloupec nastavením **jedinečné** vlastnosti sloupce na **hodnotu true**. Případně nastavení **Unique** vlastnost jednoho sloupce **false** odebere všechny jedinečné omezení, které může existovat. Definovánísloupce nebo sloupců jako primárního klíče pro tabulku automaticky vytvoří jedinečné omezení pro zadaný sloupec nebo sloupce. Pokud odeberete sloupec z **Vlastnosti PrimaryKey** **datatable**, **UniqueConstraint** je odebrán.  
  
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

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [Definice schématu datové tabulky](datatable-schema-definition.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
