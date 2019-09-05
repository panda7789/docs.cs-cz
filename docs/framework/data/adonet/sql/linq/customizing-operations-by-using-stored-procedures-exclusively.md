---
title: Přizpůsobení operací výhradně pomocí uložených procedur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: a242ecdc774d67721aee640e75847317c1b815d6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247549"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a>Přizpůsobení operací výhradně pomocí uložených procedur
Přístup k datům pomocí uložených procedur je běžným scénářem.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Můžete upravit příklad poskytnutý v části [přizpůsobení operací pomocí uložených procedur](customizing-operations-by-using-stored-procedures.md) tak, že nahradíte i první dotaz (což způsobí dynamické provádění SQL) s voláním metody, která zabalí uloženou proceduru.  
  
 Přepokládejme `CustomersByCity` je metoda, jak je uvedeno v následujícím příkladu.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 Následující kód se provede bez dynamického SQL.  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Odpovědnosti vývojáře při přepisu výchozího chování](responsibilities-of-the-developer-in-overriding-default-behavior.md)
