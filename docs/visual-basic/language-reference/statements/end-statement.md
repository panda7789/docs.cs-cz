---
title: End – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: fe17a82662c4014069c77f2da76723a051ab9084
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404703"
---
# <a name="end-statement"></a>End – příkaz
Okamžitě ukončí provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
End  
```  
  
## <a name="remarks"></a>Poznámky  
 Příkaz lze umístit `End` kdekoli v proceduře pro vynucení zastavení celé aplikace. `End`zavře všechny soubory otevřené `Open` příkazem a vymaže všechny proměnné aplikace. Aplikace se zavře, jakmile neexistují žádné další programy, které by podržely odkazy na své objekty a žádný z jeho kódu není spuštěn.  
  
> [!NOTE]
> `End`Příkaz zastaví provádění kódu náhlé a nevyvolává `Dispose` metodu or ani `Finalize` žádný jiný kód Visual Basic. Odkazy na objekty držené jinými programy jsou neověřené. Pokud `End` se v rámci bloku nebo vyskytne příkaz `Try` `Catch` , ovládací prvek neprojde odpovídajícím `Finally` blokem.  
  
 `Stop`Příkaz pozastaví provádění, ale na rozdíl od `End` , neuzavře žádné soubory ani nevymaže žádné proměnné, pokud se nevyskytly v kompilovaném spustitelném souboru (. exe).  
  
 Vzhledem k tomu, že `End` aplikace ukončí aplikaci bez účasti na jakýchkoli prostředcích, které mohou být otevřeny, měli byste se před použitím pokusit ukončit činnost. Například pokud má vaše aplikace otevřené nějaké formuláře, měli byste je před tím, než ovládací prvek dosáhne `End` příkazu, zavřít.  
  
 Měli byste používat `End` jenom zřídka a jenom v případě, že potřebujete okamžitě skončit. Normální způsoby ukončení procedury ([příkaz return](return-statement.md) a [příkaz exit](exit-statement.md)) nezavřou pouze postup, ale také volajícímu kódu, aby příležitost uzavřela čistou činnost. Konzolová aplikace může být například jednoduše `Return` z `Main` procedury.  
  
> [!IMPORTANT]
> `End`Příkaz volá <xref:System.Environment.Exit%2A> metodu <xref:System.Environment> třídy v <xref:System> oboru názvů. <xref:System.Environment.Exit%2A>vyžaduje, abyste měli `UnmanagedCode` oprávnění. Pokud to neuděláte, <xref:System.Security.SecurityException> dojde k chybě.  
  
 Když následuje klíčové slovo Next, [ \<keyword> příkaz end](end-keyword-statement.md) rozděluje konec definice příslušného postupu nebo bloku. Například `End Function` ukončí definici `Function` procedury.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `End` příkaz k ukončení provádění kódu, pokud si ho uživatel požádá.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Tento příkaz není podporován.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop – příkaz](stop-statement.md)
- [\<keyword>Příkaz end](end-keyword-statement.md)
