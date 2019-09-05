---
title: 'Postupy: Spuštění polymorfního dotazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 49e0a6b44af0729959fabf6278cc6d8ecf37a16b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251514"
---
# <a name="how-to-execute-a-polymorphic-query"></a>Postupy: Spuštění polymorfního dotazu

Toto téma ukazuje, jak spustit polymorfní [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz pomocí operátoru [OfType](./language-reference/oftype-entity-sql.md) .

### <a name="to-run-the-code-in-this-example"></a>Spuštění kódu v tomto příkladu

1. Přidejte do svého projektu [školní model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) a nakonfigurujte projekt tak, aby používal Entity Framework. Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).

2. Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. Upravte koncepční model tak, aby měl dědičnost tabulky na hierarchii, podle kroků v [návodu: Mapování dědičnosti – tabulka na hierarchii](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).

## <a name="example"></a>Příklad

Následující příklad používá operátor OfType k získání a zobrazení kolekce pouze `OnsiteCourses` z `Courses`kolekce.

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>Viz také:

- [Zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md)
- [Jazyk Entity SQL](./language-reference/entity-sql-language.md)
