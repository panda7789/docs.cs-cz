---
title: Resume – příkaz
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
ms.openlocfilehash: 3f49f05f1deb2027b03bbf3443ca44f30c44344e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404210"
---
# <a name="resume-statement"></a>Resume – příkaz
Po dokončení rutiny zpracování chyb pokračuje v provádění.  
  
 Doporučujeme, abyste ve svém kódu používali strukturované zpracování výjimek, kdykoli je to možné, místo použití nestrukturovaných zpracování výjimek `On Error` a `Resume` příkazů a. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Součásti  
 `Resume`  
 Povinná hodnota. Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyby, spuštění pokračuje s příkazem, který způsobil chybu. Pokud k chybě došlo v volané proceduře, spuštění pokračuje na příkazu, který naposledy volal proceduru, která obsahuje rutinu zpracování chyb.  
  
 `Next`  
 Nepovinný parametr. Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyby, provádění pokračuje příkazem hned po příkazu, který způsobil chybu. Pokud k chybě došlo v volané proceduře, provádění pokračuje příkazem ihned po příkazu, který byl naposledy volán z procedury obsahující rutinu zpracování chyb (nebo `On Error Resume Next` příkazu).  
  
 `line`  
 Nepovinný parametr. Spuštění pokračuje na řádku zadaném v požadovaném `line` argumentu. `line`Argument je popisek řádku nebo číslo řádku a musí být ve stejném postupu jako obslužná rutina chyby.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Doporučujeme používat strukturované zpracování výjimek v kódu, kdykoli je to možné, místo použití nestrukturovaného zpracování výjimek a `On Error` `Resume` příkazů a. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](try-catch-finally-statement.md).  
  
 Použijete-li `Resume` příkaz kdekoli jinde než v rutině zpracování chyb, dojde k chybě.  
  
 `Resume`Příkaz nelze použít v žádné proceduře, která obsahuje `Try...Catch...Finally` příkaz.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá `Resume` příkaz k ukončení zpracování chyb v proceduře a následné pokračování v provádění s příkazem, který způsobil chybu. K ilustraci použití příkazu se generuje číslo chyby 55 `Resume` .  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Požadavky  
 **Obor názvů:** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Viz také

- [Try...Catch....Finally – příkaz](try-catch-finally-statement.md)
- [Error – příkaz](error-statement.md)
- [On Error – příkaz](on-error-statement.md)
