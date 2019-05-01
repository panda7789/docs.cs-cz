---
title: 'Postupy: Zadání názvů databází'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a43a7ac541adb984eeb8bb88b7ab96db86baf26c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037567"
---
# <a name="how-to-specify-database-names"></a>Postupy: Zadání názvů databází
Použití <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnosti <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut k zadání názvu databáze, pokud není zadán název připojení.  
  
 Ukázky kódu najdete v tématu <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
### <a name="to-specify-the-name-of-the-database"></a>Chcete-li určit název databáze  
  
1. Přidat <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut deklarace třídy pro databázi.  
  
2. Přidat <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut.  
  
3. Nastavte <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> hodnotu vlastnosti na název, který chcete zadat.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
