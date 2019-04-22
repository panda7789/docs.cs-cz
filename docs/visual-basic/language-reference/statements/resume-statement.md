---
title: Resume – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 796342d17b0d0f1a642aff381274746d1fda3559
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816444"
---
# <a name="resume-statement"></a>Resume – příkaz
Pokračuje v provádění po dokončení rutiny zpracování chyb.  
  
 Doporučujeme používat strukturované zpracování výjimek ve vašem kódu, kdykoli je to možné, spíš než nestrukturované zpracování výjimek a `On Error` a `Resume` příkazy. Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Součásti  
 `Resume`  
 Povinný parametr. Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyb, provádění pokračuje s příkazem, který způsobil chybu. Pokud k chybě došlo ve volané procedury, provádění pokračuje v příkazu, který naposledy provedla volání mimo procedura obsahuje rutiny pro zpracování chyb.  
  
 `Next`  
 Volitelné. Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyb, provádění pokračuje s příkazem bezprostředně následující příkaz, který způsobil chybu. Pokud k chybě došlo ve volané procedury, provádění pokračuje s příkazem okamžitě po příkazu, který naposledy provedla volání mimo procedura obsahuje rutiny pro zpracování chyb (nebo `On Error Resume Next` příkaz).  
  
 `line`  
 Volitelné. Provádění pokračuje na řádku zadaném v požadovaném `line` argument. `line` Argument popisku řádku nebo číslo řádku a musí být ve stejné proceduře jako obslužná rutina chyb.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Doporučujeme používat strukturované zpracování výjimek ve vašem kódu, kdykoli je to možné, spíš než nestrukturované zpracování výjimek a `On Error` a `Resume` příkazy. Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Pokud používáte `Resume` příkaz kdekoli jinak než v rutiny zpracování chyb, dojde k chybě.  
  
 `Resume` Příkaz nelze použít v všechny procedury, které obsahuje `Try...Catch...Finally` příkazu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Resume` příkazu k ukončení zpracování chyb v proceduru a poté pokračovat v provádění pomocí příkazu, který způsobil chybu. Číslo chyby 55 se vygeneruje pro ilustraci použití `Resume` příkazu.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Sestavení:** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Příkaz Error](../../../visual-basic/language-reference/statements/error-statement.md)
- [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
