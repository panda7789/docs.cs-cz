---
title: Skip While – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: a3c0749560d8cea1e46d96298347ce54f0bf9185
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43537169"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While – klauzule (Visual Basic)
Vynechává prvky v kolekci, tak dlouho, dokud je zadaná podmínka `true` a vrací zbývající prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression`|Požadováno. Výraz, který představuje podmínku pro prvky pro testování. Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, jako `Integer` má být vyhodnocen jako `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 `Skip While` Klauzule vynechává prvky od začátku výsledek dotazu do zadané `expression` vrátí `false`. Po `expression` vrátí `false`, dotaz vrátí všechny zbývající prvky. `expression` Se ignoruje pro zbývající výsledky.  
  
 `Skip While` Klauzule se liší od `Where` klauzule in, který `Where` klauzuli lze použít k vyloučení všechny prvky z dotazu, které nesplňují určité podmínky. `Skip While` Klauzule vyloučí prvky pouze až do první podmínka není splněna. `Skip While` Klauzule je nejužitečnější při práci s výsledek seřazených dotazů.  
  
 Můžete obejít určitý počet výsledků od začátku výsledku dotazu pomocí `Skip` klauzuli.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Skip While` klauzule pro vyřazení výsledků, dokud nebude nalezen první zákazníků z USA.  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/index.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Skip](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Klauzule Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
