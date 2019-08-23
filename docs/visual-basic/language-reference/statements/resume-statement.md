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
ms.openlocfilehash: 884bdaa0c19508b5a6bf6377568a53acc6880518
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957680"
---
# <a name="resume-statement"></a>Resume – příkaz
Po dokončení rutiny zpracování chyb pokračuje v provádění.  
  
 Doporučujeme, abyste ve svém kódu používali strukturované zpracování výjimek, kdykoli je to možné, místo použití nestrukturovaných zpracování výjimek `On Error` a `Resume` příkazů a. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Součásti  
 `Resume`  
 Povinný parametr. Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyby, spuštění pokračuje s příkazem, který způsobil chybu. Pokud k chybě došlo v volané proceduře, spuštění pokračuje na příkazu, který naposledy volal proceduru, která obsahuje rutinu zpracování chyb.  
  
 `Next`  
 Volitelný parametr. Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyby, provádění pokračuje příkazem hned po příkazu, který způsobil chybu. Pokud k chybě došlo v volané proceduře, provádění pokračuje příkazem ihned po příkazu, který byl naposledy volán z procedury obsahující rutinu zpracování chyb (nebo `On Error Resume Next` příkazu).  
  
 `line`  
 Volitelný parametr. Spuštění pokračuje na řádku zadaném v požadovaném `line` argumentu. `line` Argument je popisek řádku nebo číslo řádku a musí být ve stejném postupu jako obslužná rutina chyby.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Doporučujeme používat strukturované zpracování výjimek v kódu, kdykoli je to možné, místo použití nestrukturovaného zpracování výjimek a `On Error` příkazů a. `Resume` Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Použijete- `Resume` li příkaz kdekoli jinde než v rutině zpracování chyb, dojde k chybě.  
  
 Příkaz nelze použít v žádné proceduře, která `Try...Catch...Finally` obsahuje příkaz. `Resume`  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se `Resume` používá příkaz k ukončení zpracování chyb v proceduře a následné pokračování v provádění s příkazem, který způsobil chybu. K ilustraci použití `Resume` příkazu se generuje číslo chyby 55.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Požadavky  
 **Hosting** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Shromážděním** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Příkaz Error](../../../visual-basic/language-reference/statements/error-statement.md)
- [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
