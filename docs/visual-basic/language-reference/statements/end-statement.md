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
ms.openlocfilehash: cb2fb4abb21b7b9c6575cec4aca1374f63687607
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343727"
---
# <a name="end-statement"></a>End – příkaz
Okamžitě ukončí provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
End  
```  
  
## <a name="remarks"></a>Poznámky  
 Příkaz `End` můžete umístit kamkoli do postupu pro vynucení, že se celá aplikace přestane spouštět. `End` zavře všechny soubory otevřené pomocí příkazu `Open` a vymaže všechny proměnné aplikace. Aplikace se zavře, jakmile neexistují žádné další programy, které by podržely odkazy na své objekty a žádný z jeho kódu není spuštěn.  
  
> [!NOTE]
> Příkaz `End` zastaví provádění kódu náhlém způsobem a nevyvolává metodu `Dispose` nebo `Finalize` ani jiný kód Visual Basic. Odkazy na objekty držené jinými programy jsou neověřené. Pokud byl v rámci `Try` nebo `Catch` bloku nalezen příkaz `End`, ovládací prvek neprojde odpovídajícím `Finally` bloku.  
  
 Příkaz `Stop` pozastaví provádění, ale na rozdíl od `End`nezavře žádné soubory ani nevymaže žádné proměnné, pokud se nevyskytly v kompilovaném spustitelném souboru (. exe).  
  
 Vzhledem k tomu, že `End` ukončí vaši aplikaci, aniž by se účastnila jakýchkoli prostředků, které by mohly být otevřené, měli byste se před použitím pokusit ukončit činnost. Například pokud má vaše aplikace otevřené nějaké formuláře, měli byste je zavřít před tím, než ovládací prvek dosáhne příkazu `End`.  
  
 Měli byste použít `End` bez jakýchkoli potřeb, a to pouze v případě, že potřebujete okamžitě ukončit činnost. Normální způsoby ukončení procedury ([příkaz return](../../../visual-basic/language-reference/statements/return-statement.md) a [příkaz exit](../../../visual-basic/language-reference/statements/exit-statement.md)) nezavřou pouze postup, ale také volajícímu kódu, aby příležitost uzavřela čistou činnost. Konzolová aplikace může například jednoduše `Return` z `Main`ho postupu.  
  
> [!IMPORTANT]
> Příkaz `End` volá metodu <xref:System.Environment.Exit%2A> třídy <xref:System.Environment> v oboru názvů <xref:System>. <xref:System.Environment.Exit%2A> vyžaduje, abyste měli `UnmanagedCode` oprávnění. Pokud to neuděláte, dojde k chybě <xref:System.Security.SecurityException>.  
  
 Po následování dalšího klíčového slova [end \<> příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) určí konec definice příslušného postupu nebo bloku. Například `End Function` ukončí definici `Function` postupu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `End` k ukončení provádění kódu, pokud si ho uživatel požádá.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Tento příkaz není podporován.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Příkaz Stop](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Příkaz end \<– klíčové slovo >](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
