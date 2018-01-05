---
title: "Postupy: Zadejte názvy databází"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d0dffe22205b2d59dbd77bcd8f86efe4fa56be3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-database-names"></a>Postupy: Zadejte názvy databází
Použití <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut určit název databáze, když není zadaný název připojení.  
  
 Ukázky kódu, najdete v části <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
### <a name="to-specify-the-name-of-the-database"></a>Zadat název databáze  
  
1.  Přidat <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut deklarace třídy pro databázi.  
  
2.  Přidat <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut.  
  
3.  Nastavte <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> hodnotu vlastnosti na název, který chcete zadat.  
  
## <a name="see-also"></a>Viz také  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
