---
title: Uživatelem definované funkce
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: fb55a8b248b085275f83d47b1f452cd07bd8dcb1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582652"
---
# <a name="user-defined-functions"></a>Uživatelem definované funkce
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] metody v objektovém modelu používá k reprezentaci uživatelem definované funkce. Označení metod jako funkce použitím <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut a v případě potřeby <xref:System.Data.Linq.Mapping.ParameterAttribute> atribut. Další informace najdete v tématu [The LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Aby se zabránilo <xref:System.InvalidOperationException>, uživatelem definované funkce v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí být v jednom z následujících forem:  
  
- Zabalená funkce jako volání metody s atributy správné mapování. Další informace najdete v tématu [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
- Specifické pro statickou metodu SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
- Funkce nepodporuje metodu rozhraní .NET Framework.  
  
 Témata v této části ukazují, jak formulář a volat tyto metody ve své aplikaci psát kód sami. Obvykle byste použili vývojářům používajícím Visual Studio [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapovat uživatelem definované funkce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Použití funkce vracející skalární uživatelem definované](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Popisuje, jak implementovat funkci vracející skalární hodnoty.  
  
 [Postupy: Použití Table-Valued uživatelsky definovaných funkcí](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Popisuje, jak implementovat funkci vracející tabulku hodnot.  
  
 [Postupy: Volat uživatelsky definovaných funkcí](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Popisuje, jak volat vložené funkce a jaký je rozdíl v provádění po přišla vložené.
