---
title: Erase – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: cab3da4465b4671d203036c2d9bcd40662dc234a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522437"
---
# <a name="erase-statement-visual-basic"></a>Erase – příkaz (Visual Basic)
Slouží k uvolnění proměnných pole a navrácení paměti používané pro jejich elementy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>Součásti  
 `arraylist`  
 Povinný parametr. Seznam proměnných jsou vymazány. Více proměnných jsou odděleny čárkami.  
  
## <a name="remarks"></a>Poznámky  
 `Erase` Příkaz se může zobrazit jenom na úroveň procedury. To znamená, že můžete uvolnit pole uvnitř procedury, ale ne na úrovni třídy nebo modulu.  
  
 `Erase` Příkaz je ekvivalentní k přiřazení `Nothing` pro každou proměnnou pole.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Erase` příkaz dvě pole vymazat a uvolnit paměť, jejich (1 000 až 100 elementů úložiště, v uvedeném pořadí). `ReDim` Příkaz pak přiřadí nové pole instance na trojrozměrné pole.  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Příkaz ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
