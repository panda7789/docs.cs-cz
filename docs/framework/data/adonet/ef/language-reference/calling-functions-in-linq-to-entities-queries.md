---
title: Volání funkcí v dotazech LINQ to Entities
description: Pomocí těchto článků zjistíte, jak třídy EntityFunctions a SqlFunctions poskytují přístup k kanonickým a databázovým funkcím jako součást Entity Framework.
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: faa6406713592f10e5e7371cd73f29bec4b03b7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286854"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Volání funkcí v dotazech LINQ to Entities
Témata v této části popisují, jak volat funkce v LINQ to Entitiesch dotazech.  
  
 <xref:System.Data.Objects.EntityFunctions>Třídy a <xref:System.Data.Objects.SqlClient.SqlFunctions> poskytují přístup k kanonickým a databázovým funkcím jako součást Entity Framework. Další informace naleznete v tématu [How to: Calling Kanonick Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).  
  
 Proces volání vlastní funkce vyžaduje tři základní kroky:  
  
1. Definujte funkci ve koncepčním modelu nebo Deklarujte funkci v modelu úložiště.  
  
2. Přidejte do své aplikace metodu a namapujte ji na funkci v modelu pomocí <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> .  
  
3. Volání funkce v dotazu LINQ to Entities.  
  
 Další informace najdete v tématech v této části.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Volání kanonických funkcí](how-to-call-canonical-functions.md)  
  
 [Postupy: Volání databázových funkcí](how-to-call-database-functions.md)  
  
 [Postupy: Volání vlastních databázových funkcí](how-to-call-custom-database-functions.md)  
  
 [Postupy: Volání modelově definovaných funkcí v dotazech](how-to-call-model-defined-functions-in-queries.md)  
  
 [Postupy: Volání modelově definovaných funkcí jako objektových metod](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Viz také

- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)
- [Kanonické funkce](canonical-functions.md)
- [Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Postupy: definování vlastních funkcí v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
