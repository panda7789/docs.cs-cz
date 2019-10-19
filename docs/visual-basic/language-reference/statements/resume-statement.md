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
ms.openlocfilehash: 7b8c2e123c04ff9720d690507ee41a6b52f40c3f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583274"
---
# <a name="resume-statement"></a>Resume – příkaz
Po dokončení rutiny zpracování chyb pokračuje v provádění.  
  
 Doporučujeme, abyste ve svém kódu používali strukturované zpracování výjimek, kdykoli je to možné, místo použití nestrukturovaného zpracování výjimek a příkazů `On Error` a `Resume`. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Součásti  
 `Resume`  
 Požadováno. Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyby, spuštění pokračuje s příkazem, který způsobil chybu. Pokud k chybě došlo v volané proceduře, spuštění pokračuje na příkazu, který naposledy volal proceduru, která obsahuje rutinu zpracování chyb.  
  
 `Next`  
 Volitelné. Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyby, provádění pokračuje příkazem hned po příkazu, který způsobil chybu. Pokud k chybě došlo v volané proceduře, spuštění pokračuje pomocí příkazu ihned po příkazu, který naposledy vyvolal proceduru, která obsahuje rutinu zpracování chyb (nebo příkaz `On Error Resume Next`).  
  
 `line`  
 Volitelné. Provádění pokračuje na řádku zadaném v argumentu Required `line`. Argument `line` je popisek řádku nebo číslo řádku a musí být ve stejném postupu jako obslužná rutina chyby.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Doporučujeme používat strukturované zpracování výjimek v kódu, kdykoli je to možné, místo použití nestrukturovaného zpracování výjimek a příkazů `On Error` a `Resume`. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Použijete-li příkaz `Resume` kdekoli jinde než v rutině zpracování chyb, dojde k chybě.  
  
 Příkaz `Resume` nelze použít v jakékoli proceduře, která obsahuje příkaz `Try...Catch...Finally`.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se pomocí příkazu `Resume` ukončí zpracování chyb v proceduře a pak pokračuje v provádění s příkazem, který chybu způsobil. K ilustraci použití příkazu `Resume` je vygenerována chyba č. 55.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Požadavky  
 **Obor názvů:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Příkaz Error](../../../visual-basic/language-reference/statements/error-statement.md)
- [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
