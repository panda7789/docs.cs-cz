---
title: "Postupy: představují vypočítaného sloupce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 76f6d64c6577456d1208d2d157c5560e49f85f7e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-computed-columns"></a>Postupy: představují vypočítaného sloupce
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut představují sloupce, jejichž obsah je výsledek výpočtu.  
  
 Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Počítané sloupce nepodporuje jako primární klíče.  
  
### <a name="to-represent-a-computed-column"></a>Představují počítaný sloupec  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Přiřadit řetězcovou reprezentaci vzorec k <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
