---
title: Uživatelem definované funkce
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: f1222d9332d365c9c3c6ca2aa28cbb48e92c04e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="user-defined-functions"></a>Uživatelem definované funkce
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá metody v objektovém modelu k reprezentaci uživatelsky definované funkce. Jako funkce určíte použitím metody <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut a v případě potřeby <xref:System.Data.Linq.Mapping.ParameterAttribute> atribut. Další informace najdete v tématu [technologii LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Aby nedošlo <xref:System.InvalidOperationException>, uživatelsky definované funkce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí být v jednom z následujících podob:  
  
-   Zabalená funkce jako volání metody s atributy správné mapování. Další informace najdete v tématu [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Statickou metodu SQL specifické pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
-   Funkce nepodporuje [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] metoda.  
  
 Témata v této části ukazují, jak vytvořit a volání těchto metod ve vaší aplikaci můžete psát kód sami. Pomocí sady Visual Studio vývojáři obvykle využije [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapovat uživatelem definované funkce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Popisuje, jak implementovat funkci, která vrátí skalárních hodnot.  
  
 [Postupy: Použití uživatelem definovaných funkcí s tabulkovými hodnotami](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Popisuje, jak implementovat funkci, která vrátí tabulku hodnot.  
  
 [Postupy: Volání vložených funkcí definovaných uživatelem](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Popisuje, jak provádět volání vnořené funkce a rozdíly ve zpracování při volání vnořené.
