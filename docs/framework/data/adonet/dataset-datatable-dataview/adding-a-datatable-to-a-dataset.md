---
title: Přidání datové tabulky do datové sady
description: Chcete-li se dozvědět, jak vytvořit objekty DataTable a přidat je do existující datové sady v ADO.NET, přečtěte si tento ukázkový kód.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 42bd36b394de560884a2ec607f4cbc65d1171e4e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286957"
---
# <a name="adding-a-datatable-to-a-dataset"></a>Přidání datové tabulky do datové sady
ADO.NET umožňuje vytvářet <xref:System.Data.DataTable> objekty a přidávat je do existujících objektů <xref:System.Data.DataSet> . Můžete nastavit informace o omezení pro a <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataColumn.Unique%2A> vlastností a.  
  
## <a name="example"></a>Příklad  
 Následující příklad konstrukce vytvoří <xref:System.Data.DataSet> , přidá nový <xref:System.Data.DataTable> objekt do objektu <xref:System.Data.DataSet> a poté přidá <xref:System.Data.DataColumn> do tabulky tři objekty. Nakonec kód nastaví jeden sloupec jako sloupec primárního klíče.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Rozlišovat velká a malá písmena  
 Dvě nebo více tabulek nebo vztahů se stejným názvem, ale různými velikostmi písmen, může existovat v <xref:System.Data.DataSet> . V takových případech odkazují odkazy podle názvu na tabulky a relace na velká a malá písmena. Například pokud <xref:System.Data.DataSet> **datová sada** obsahuje tabulky **Tabulka1** a **Tabulka1**, měli byste odkazovat na **Tabulka1** podle názvu jako **DataSet. Tables ["Tabulka1"]** a **Tabulka1** jako **DataSet. Tables ["Tabulka1"]**. Došlo k pokusu o odkaz na jednu z tabulek jako na **datovou sadu. tabulky ["Tabulka1"]** by vygenerovaly výjimku.  
  
 Chování rozlišování velkých a malých písmen neplatí, pokud pouze jedna tabulka nebo vztah má konkrétní název. Například pokud <xref:System.Data.DataSet> má pouze hodnotu **Tabulka1**, můžete na ni odkazovat pomocí **DataSet. Tables ["Tabulka1"]**.  
  
> [!NOTE]
> <xref:System.Data.DataSet.CaseSensitive%2A>Vlastnost <xref:System.Data.DataSet> nemá vliv na toto chování. Tato <xref:System.Data.DataSet.CaseSensitive%2A> vlastnost se vztahuje na data v nástroji <xref:System.Data.DataSet> a ovlivňuje řazení, vyhledávání, filtrování, vynucování omezení atd.  
  
## <a name="namespace-support"></a>Podpora oboru názvů  
 Ve verzích ADO.NET starších než 2,0 nemohly mít dvě tabulky stejný název, i když byly v různých oborech názvů. Toto omezení se odebralo v ADO.NET 2,0. <xref:System.Data.DataSet>Může obsahovat dvě tabulky, které mají stejnou <xref:System.Data.DataTable.TableName%2A> hodnotu vlastnosti, ale jiné <xref:System.Data.DataTable.Namespace%2A> hodnoty vlastností.  
  
## <a name="see-also"></a>Viz také

- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
