---
title: End – příkaz (Visual Basic)
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
ms.openlocfilehash: 9307cf10e6125441bd49baa0e663a5a13f234005
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944466"
---
# <a name="end-statement"></a>End – příkaz
Okamžitě ukončí provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
End  
```  
  
## <a name="remarks"></a>Poznámky  
 `End` Příkaz lze umístit kdekoli v proceduře pro vynucení zastavení celé aplikace. `End`zavře všechny soubory otevřené `Open` příkazem a vymaže všechny proměnné aplikace. Aplikace se zavře, jakmile neexistují žádné další programy, které by podržely odkazy na své objekty a žádný z jeho kódu není spuštěn.  
  
> [!NOTE]
> Příkaz zastaví provádění kódu náhlé a `Dispose` nevyvolává metodu or `Finalize` ani žádný jiný kód Visual Basic. `End` Odkazy na objekty držené jinými programy jsou neověřené. Pokud se `Catch` `Finally` v rámci bloku `End` nebovyskytnepříkaz,ovládacíprvekneprojdeodpovídajícím`Try` blokem.  
  
 Příkaz pozastaví provádění, ale na rozdíl od `End`, neuzavře žádné soubory ani nevymaže žádné proměnné, pokud se nevyskytly v kompilovaném spustitelném souboru (. exe). `Stop`  
  
 Vzhledem `End` k tomu, že aplikace ukončí aplikaci bez účasti na jakýchkoli prostředcích, které mohou být otevřeny, měli byste se před použitím pokusit ukončit činnost. Například pokud má vaše aplikace otevřené nějaké formuláře, měli byste je před tím, `End` než ovládací prvek dosáhne příkazu, zavřít.  
  
 Měli byste používat `End` jenom zřídka a jenom v případě, že potřebujete okamžitě skončit. Normální způsoby ukončení procedury ([příkaz return](../../../visual-basic/language-reference/statements/return-statement.md) a [příkaz exit](../../../visual-basic/language-reference/statements/exit-statement.md)) nezavřou pouze postup, ale také volajícímu kódu, aby příležitost uzavřela čistou činnost. Konzolová aplikace může být například jednoduše `Return` `Main` z procedury.  
  
> [!IMPORTANT]
> `End` Příkaz<xref:System.Environment.Exit%2A> volá metodu<xref:System.Environment> třídy v<xref:System> oboru názvů. <xref:System.Environment.Exit%2A>vyžaduje, abyste `UnmanagedCode` měli oprávnění. Pokud to neuděláte, <xref:System.Security.SecurityException> dojde k chybě.  
  
 Když následuje klíčové slovo Next, [klíčové slovo \<end > příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) rozděluje konec definice příslušného postupu nebo bloku. Například `End Function` ukončí definici `Function` procedury.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `End` příkaz k ukončení provádění kódu, pokud si ho uživatel požádá.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Tento příkaz není podporován.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Příkaz Stop](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Klíčové \<slovo End > – příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
