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
ms.openlocfilehash: 853f3fe060b70c8a43957d3c843fb95539981679
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/27/2018
ms.locfileid: "39296153"
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
 Požadováno. Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyb, provádění pokračuje s příkazem, který způsobil chybu. Pokud k chybě došlo ve volané procedury, provádění pokračuje v příkazu, který naposledy provedla volání mimo procedura obsahuje rutiny pro zpracování chyb.  
  
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
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Sestavení:** knihovny prostředí Runtime jazyka Visual Basic (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Příkaz Error](../../../visual-basic/language-reference/statements/error-statement.md)  
 [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
