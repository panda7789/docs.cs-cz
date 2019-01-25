---
title: Přidání datové tabulky do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 16b60b2973524c8e600f5efebb3f2b291377ffcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732710"
---
# <a name="adding-a-datatable-to-a-dataset"></a>Přidání datové tabulky do datové sady
ADO.NET vám umožní vytvořit <xref:System.Data.DataTable> objekty a přidat do existujícího <xref:System.Data.DataSet>. Informace o omezení pro můžete nastavit <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.PrimaryKey%2A> a <xref:System.Data.DataColumn.Unique%2A> vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataSet>, přidá nový <xref:System.Data.DataTable> objektu <xref:System.Data.DataSet>a pak přidá tři <xref:System.Data.DataColumn> objekty do tabulky. Nakonec kód nastaví jeden sloupec jako sloupec primárního klíče.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Rozlišování velikosti písmen  
 V může existovat dva nebo více tabulek nebo vztahy se stejným názvem, ale jinou velikostí písmen, <xref:System.Data.DataSet>. V takových případech odkazy podle názvu tabulky a vztahy jsou malá a velká písmena. Například pokud <xref:System.Data.DataSet> **datovou sadu** obsahuje tabulky **Tabulka1** a **Tabulka1**, by odkazovat **Tabulka1** podle názvu jako **dataSet.Tables["Table1"]**, a **Tabulka1** jako **dataSet.Tables["table1"]**. Pokus o některou z tabulek jako odkaz na **dataSet.Tables["TABLE1"]** vygeneruje výjimku.  
  
 Chování rozlišování neplatí, pokud pouze jednu tabulku nebo vztah má určitý název. Například pokud <xref:System.Data.DataSet> má pouze **Tabulka1**, můžete na něj mohli odkazovat pomocí **dataSet.Tables["TABLE1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataSet.CaseSensitive%2A> Vlastnost <xref:System.Data.DataSet> nemá vliv na toto chování. <xref:System.Data.DataSet.CaseSensitive%2A> Vlastnost se vztahuje na data v <xref:System.Data.DataSet> a ovlivňuje řazení, hledání, filtrování, vynucení omezení a tak dále.  
  
## <a name="namespace-support"></a>Podpora Namespace  
 Ve verzích ADO.NET nižší než 2.0 dvě tabulky nesmí být stejný název, i kdyby šlo v různých oborech názvů. Toto omezení se odebral ve verzi 2.0 rozhraní ADO.NET. A <xref:System.Data.DataSet> může obsahovat dvou tabulek, které mají stejné <xref:System.Data.DataTable.TableName%2A> hodnotu vlastnosti, ale jiné <xref:System.Data.DataTable.Namespace%2A> hodnot vlastností.  
  
## <a name="see-also"></a>Viz také:
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
