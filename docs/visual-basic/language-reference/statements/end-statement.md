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
ms.openlocfilehash: 8fd489dc9f12f7e80ef2dd49c6e2dee6c28ae761
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199394"
---
# <a name="end-statement"></a>End – příkaz
Ukončí provádění okamžitě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
End  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete umístit `End` příkaz kdekoli v proceduře přinutit celé aplikace ukončené. `End` Zavře všechny soubory otevřené se `Open` příkazu a vymaže všechny aplikace proměnné. Aplikace se zavře, jakmile nejsou žádné jiné programy obsahující odkazy na objekty a žádný z jeho kód běží.  
  
> [!NOTE]
>  `End` Příkaz náhle zastaví provádění kódu a se nevyvolá `Dispose` nebo `Finalize` metody nebo jakýkoli jiný kód jazyka Visual Basic. Odkazy na objekty uchovávat jinými programy nejsou zneplatněny. Pokud `End` příkaz dochází v rámci `Try` nebo `Catch` bloku, ovládací prvek nepředává odpovídající `Finally` bloku.  
  
 `Stop` Příkaz pozastaví provádění, ale na rozdíl od `End`, ne zavřít všechny soubory, nebo zrušte všechny proměnné, pokud není nalezen v souboru zkompilovaného spustitelného souboru (.exe).  
  
 Protože `End` ukončí vaše aplikace bez vaši účast na všechny prostředky, které může být otevřený, snažte se zavřít čistě před jeho použitím. Například pokud má vaše aplikace formulářů otevřete, zavřete je před ovládací prvek dosáhne `End` příkazu.  
  
 Měli byste použít `End` opatrně a pouze pokud je potřeba zastavit okamžitě. Běžné způsoby ukončí proceduru ([příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) a [příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) nejen ukončete proces čistě, ale také poskytují možnost Zavřít čistě volajícímu kódu. Konzolová aplikace, například můžete jednoduše `Return` z `Main` postup.  
  
> [!IMPORTANT]
>  `End` Příkaz volá <xref:System.Environment.Exit%2A> metodu <xref:System.Environment> třídy v <xref:System> oboru názvů. <xref:System.Environment.Exit%2A> vyžaduje, abyste měli `UnmanagedCode` oprávnění. Pokud tak neučiníte, <xref:System.Security.SecurityException> dojde k chybě.  
  
 Pokud následuje další klíčové slovo, [End \<– klíčové slovo > příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) kolem Konec definice vhodný postup uvedený nebo bloku. Například `End Function` ukončí definici `Function` postup.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `End` příkaz k ukončení provádění kódu, pokud uživatel požaduje.  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Tento příkaz není podporován.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [Příkaz Stop](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [End \<– klíčové slovo > – příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
