---
title: "Resume – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb4334f302c07c81b6b8a7d0626be08cc69b1ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="resume-statement"></a>Resume – příkaz
Obnoví zpracování po dokončení rutiny chyba zpracování.  
  
 Doporučujeme použít strukturované zpracování výjimek ve vašem kódu, pokud je to možné, nikoli pomocí nestrukturovaných výjimek a `On Error` a `Resume` příkazy. Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Součásti  
 `Resume`  
 Požadováno. Pokud k chybě došlo ve stejný postup jako obslužná rutina chyb, provádění obnoví pomocí příkazu, který způsobil chybu. Pokud k chybě došlo v postupu názvem, provádění pokračuje v příkazu, který naposledy provedla volání mimo procedura obsahuje rutiny pro zpracování chyb.  
  
 `Next`  
 Volitelné. Pokud k chybě došlo ve stejný postup jako obslužná rutina chyb, provádění pokračuje s příkazem okamžitě následující příkaz, který chybu způsobil. Pokud k chybě došlo v postupu názvem, provádění pokračuje s příkazem okamžitě následující příkaz, který naposledy provedla volání mimo procedura obsahuje rutiny pro zpracování chyb (nebo `On Error Resume Next` příkaz).  
  
 `line`  
 Volitelné. Provádění pokračuje v řádku zadaný v požadovaných `line` argument. `line` Argument je popisek čáry nebo číslo řádku a musí být v stejným způsobem jako obslužná rutina chyb.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Doporučujeme použít strukturované zpracování výjimek ve vašem kódu, pokud je to možné, nikoli pomocí nestrukturovaných výjimek a `On Error` a `Resume` příkazy. Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Pokud používáte `Resume` příkaz kdekoli jinak než v rutiny zpracování chyb, dojde k chybě.  
  
 `Resume` Příkaz nelze použít v jakékoli postupu, který obsahuje `Try...Catch...Finally` příkaz.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Resume` příkaz k ukončení zpracování chyb v postupu a poté pokračovat v provádění pomocí příkazu, který způsobil chybu. Číslo chyby 55 se vygeneruje pro ilustraci použití `Resume` příkaz.  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic –](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Sestavení:** jazyka Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také  
 [Try... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Error – příkaz](../../../visual-basic/language-reference/statements/error-statement.md)  
 [On Error – příkaz](../../../visual-basic/language-reference/statements/on-error-statement.md)
