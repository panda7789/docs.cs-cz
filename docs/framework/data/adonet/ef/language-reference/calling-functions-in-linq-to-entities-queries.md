---
title: Volání funkcí v dotazech LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 267bb393d9e75c66eb18139e8897da34bd86e159
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251266"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Volání funkcí v dotazech LINQ to Entities
Témata v této části popisují, jak volat funkce v LINQ to Entitiesch dotazech.  
  
 Třídy <xref:System.Data.Objects.EntityFunctions> a<xref:System.Data.Objects.SqlClient.SqlFunctions> poskytují přístup k kanonickým a databázovým funkcím jako součást Entity Framework. Další informace najdete v tématu [jak: Zavolejte kanonické](how-to-call-canonical-functions.md) funkce [a postupy: Volání funkcí](how-to-call-database-functions.md)databáze.  
  
 Proces volání vlastní funkce vyžaduje tři základní kroky:  
  
1. Definujte funkci ve koncepčním modelu nebo Deklarujte funkci v modelu úložiště.  
  
2. Přidejte do své aplikace metodu a namapujte ji na funkci v modelu pomocí <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3. Volání funkce v dotazu LINQ to Entities.  
  
 Další informace najdete v tématech v této části.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Volání normativních funkcí](how-to-call-canonical-functions.md)  
  
 [Postupy: Volání funkcí databáze](how-to-call-database-functions.md)  
  
 [Postupy: Volání vlastních databázových funkcí](how-to-call-custom-database-functions.md)  
  
 [Postupy: Volání funkcí definovaných modelem v dotazech](how-to-call-model-defined-functions-in-queries.md)  
  
 [Postupy: Volání funkcí definovaných modelem jako metod objektů](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Viz také:

- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)
- [Kanonické funkce](canonical-functions.md)
- [Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Postupy: Definování vlastních funkcí v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
