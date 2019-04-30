---
title: Uživatelem definované funkce
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: f1222d9332d365c9c3c6ca2aa28cbb48e92c04e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917656"
---
# <a name="user-defined-functions"></a>Uživatelem definované funkce
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] metody v objektovém modelu používá k reprezentaci uživatelem definované funkce. Označení metod jako funkce použitím <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut a v případě potřeby <xref:System.Data.Linq.Mapping.ParameterAttribute> atribut. Další informace najdete v tématu [The LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Aby se zabránilo <xref:System.InvalidOperationException>, uživatelem definované funkce v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí být v jednom z následujících forem:  
  
- Zabalená funkce jako volání metody s atributy správné mapování. Další informace najdete v tématu [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
- Specifické pro statickou metodu SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
- Funkce podporované [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] metoda.  
  
 Témata v této části ukazují, jak formulář a volat tyto metody ve své aplikaci psát kód sami. Obvykle byste použili vývojářům používajícím Visual Studio [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapovat uživatelem definované funkce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Použití funkce vracející skalární uživatelem definované](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Popisuje, jak implementovat funkci vracející skalární hodnoty.  
  
 [Postupy: Použití Table-Valued uživatelsky definovaných funkcí](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Popisuje, jak implementovat funkci vracející tabulku hodnot.  
  
 [Postupy: Volat uživatelsky definovaných funkcí](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Popisuje, jak volat vložené funkce a jaký je rozdíl v provádění po přišla vložené.
