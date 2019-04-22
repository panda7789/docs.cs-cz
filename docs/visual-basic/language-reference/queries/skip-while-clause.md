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
ms.openlocfilehash: 3d6caeb1938e8e53e8ec2575f740cd5e49496f62
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839896"
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
|`expression`|Povinný parametr. Výraz, který představuje podmínku pro prvky pro testování. Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, jako `Integer` má být vyhodnocen jako `Boolean`.|  
  
## <a name="remarks"></a>Poznámky  
 `Skip While` Klauzule vynechává prvky od začátku výsledek dotazu do zadané `expression` vrátí `false`. Po `expression` vrátí `false`, dotaz vrátí všechny zbývající prvky. `expression` Se ignoruje pro zbývající výsledky.  
  
 `Skip While` Klauzule se liší od `Where` klauzule in, který `Where` klauzuli lze použít k vyloučení všechny prvky z dotazu, které nesplňují určité podmínky. `Skip While` Klauzule vyloučí prvky pouze až do první podmínka není splněna. `Skip While` Klauzule je nejužitečnější při práci s výsledek seřazených dotazů.  
  
 Můžete obejít určitý počet výsledků od začátku výsledku dotazu pomocí `Skip` klauzuli.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Skip While` klauzule pro vyřazení výsledků, dokud nebude nalezen první zákazníků z USA.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Klauzule Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
