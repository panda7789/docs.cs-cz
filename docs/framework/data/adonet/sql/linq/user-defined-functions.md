---
title: Uživatelem definované funkce
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 40697da4fe678668f8f7ecda86abebf40da7b973
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792301"
---
# <a name="user-defined-functions"></a>Uživatelem definované funkce
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]používá metody v objektovém modelu k reprezentaci uživatelsky definovaných funkcí. Metody můžete určit jako funkce <xref:System.Data.Linq.Mapping.FunctionAttribute> použitím atributu a v případě potřeby <xref:System.Data.Linq.Mapping.ParameterAttribute> atributem. Další informace najdete v tématu [model objektu LINQ to SQL](the-linq-to-sql-object-model.md).  
  
 Aby se zabránilo tomu <xref:System.InvalidOperationException>, uživatelsky definované funkce v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nástroji musí být v jednom z následujících forem:  
  
- Funkce zabalená jako volání metody se správnými atributy mapování. Další informace najdete v tématu [mapování na základě atributů](attribute-based-mapping.md).  
  
- Statická metoda SQL specifická pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
- Funkce podporovaná metodou .NET Framework.  
  
 Témata v této části ukazují, jak vytvořit a volat tyto metody v aplikaci, pokud píšete kód sami. Vývojáři, kteří používají Visual Studio, by obvykle používali Návrhář relací objektů k mapování uživatelsky definovaných funkcí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Použití uživatelem definovaných funkcí s skalární hodnotou](how-to-use-scalar-valued-user-defined-functions.md)  
 Popisuje, jak implementovat funkci, která vrací skalární hodnoty.  
  
 [Postupy: Použití uživatelsky definovaných funkcí s hodnotou tabulky](how-to-use-table-valued-user-defined-functions.md)  
 Popisuje, jak implementovat funkci, která vrací hodnoty tabulky.  
  
 [Postupy: Volání uživatelsky definovaných funkcí – inline](how-to-call-user-defined-functions-inline.md)  
 Popisuje, jak provést vložená volání funkcí a rozdíly v provádění, když je volání provedeno jako vložené.
