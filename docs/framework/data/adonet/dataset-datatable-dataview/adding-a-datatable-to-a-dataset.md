---
title: Přidání datové tabulky do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: d62d55771e4fda74d336163b3f53b3f50cfb1e39
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205287"
---
# <a name="adding-a-datatable-to-a-dataset"></a>Přidání datové tabulky do datové sady
ADO.NET umožňuje vytvářet <xref:System.Data.DataTable> objekty a přidávat je do existujících <xref:System.Data.DataSet>objektů. Můžete nastavit informace o omezení pro a <xref:System.Data.DataTable> <xref:System.Data.DataTable.PrimaryKey%2A> pomocí vlastností a <xref:System.Data.DataColumn.Unique%2A> .  
  
## <a name="example"></a>Příklad  
 <xref:System.Data.DataSet>Následující příklad konstrukce vytvoří, přidá nový <xref:System.Data.DataTable> objekt do <xref:System.Data.DataSet>objektu a poté přidá do tabulky tři <xref:System.Data.DataColumn> objekty. Nakonec kód nastaví jeden sloupec jako sloupec primárního klíče.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Rozlišovat velká a malá písmena  
 Dvě nebo více tabulek nebo vztahů se stejným názvem, ale různými velikostmi písmen, může existovat v <xref:System.Data.DataSet>. V takových případech odkazují odkazy podle názvu na tabulky a relace na velká a malá písmena. Například pokud <xref:System.Data.DataSet> **datová sada** obsahuje tabulky **Tabulka1** a **Tabulka1**, měli byste odkazovat na **Tabulka1** podle názvu jako **DataSet. Tables ["Tabulka1"]** a **Tabulka1** jako **DataSet. Tables ["Tabulka1"]** . Došlo k pokusu o odkaz na jednu z tabulek jako na **datovou sadu. tabulky ["Tabulka1"]** by vygenerovaly výjimku.  
  
 Chování rozlišování velkých a malých písmen neplatí, pokud pouze jedna tabulka nebo vztah má konkrétní název. Například pokud má pouze hodnotu <xref:System.Data.DataSet> **Tabulka1**, můžete na ni odkazovat pomocí **DataSet. Tables ["Tabulka1"]** .  
  
> [!NOTE]
> Vlastnost nemá vliv na <xref:System.Data.DataSet> toto chování. <xref:System.Data.DataSet.CaseSensitive%2A> Tato <xref:System.Data.DataSet.CaseSensitive%2A> vlastnost se vztahuje na data <xref:System.Data.DataSet> v nástroji a ovlivňuje řazení, vyhledávání, filtrování, vynucování omezení atd.  
  
## <a name="namespace-support"></a>Podpora oboru názvů  
 Ve verzích ADO.NET starších než 2,0 nemohly mít dvě tabulky stejný název, i když byly v různých oborech názvů. Toto omezení se odebralo v ADO.NET 2,0. Může obsahovat dvě tabulky, které mají stejnou <xref:System.Data.DataTable.TableName%2A> hodnotu vlastnosti, ale jiné <xref:System.Data.DataTable.Namespace%2A> hodnoty vlastností. <xref:System.Data.DataSet>  
  
## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
