---
title: Take While – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 181cc641bb12329c898cc3bb226ea49f0836e979
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932024"
---
# <a name="take-while-clause-visual-basic"></a>Take While – klauzule (Visual Basic)
Obsahuje elementy v kolekci, tak dlouho, dokud je zadaná podmínka `true` a vynechány zbývající prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression`|Požadováno. Výraz, který představuje podmínku pro prvky pro testování. Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, jako `Integer` má být vyhodnocen jako `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 `Take While` Klauzule obsahuje prvků od začátku výsledek dotazu do zadané `expression` vrátí `false`. Po `expression` vrátí `false`, dotaz bude vynechat všechny zbývající prvky. `expression` Se ignoruje pro zbývající výsledky.  
  
 `Take While` Klauzule se liší od `Where` klauzule in, který `Where` klauzule umožňuje zahrnout všechny prvky z dotazu, které splňují určitou podmínku. `Take While` Klauzule obsahuje prvky pouze až do první podmínka není splněna. `Take While` Klauzule je nejužitečnější při práci s výsledek seřazených dotazů.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Take While` klauzule k načtení výsledků, dokud nebude nalezen první zákazníků bez všech objednávek.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/index.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Take](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
