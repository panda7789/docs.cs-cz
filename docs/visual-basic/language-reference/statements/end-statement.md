---
title: "End – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b692409f2895f5e9b713c57fc35ff2def40bce75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="end-statement"></a>End – příkaz
Ukončí provádění okamžitě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
End  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete umístit `End` příkaz kdekoli v proceduře vynutit bude celá aplikace zastavení. `End`Zavře všechny soubory otevřené se `Open` prohlášení a vymaže všechny aplikace proměnné. Aplikace se zavře, jakmile nejsou žádné další programy, která uchovává odkazy na jeho objekty a žádný z jeho kód běží.  
  
> [!NOTE]
>  `End` Příkaz náhle zastaví spuštění kódu a nevyvolá `Dispose` nebo `Finalize` metoda nebo jakýkoli jiný kód jazyka Visual Basic. Odkazy na objekty ukládaná jinými programy jsou zneplatněny. Pokud `End` je příkaz zjistil v rámci `Try` nebo `Catch` bloku řízení nepředává do odpovídajících `Finally` bloku.  
  
 `Stop` Příkaz pozastaví spuštění, ale na rozdíl od `End`, nemá zavřete všechny soubory, nebo zrušte všechny proměnné, pokud se vyskytuje v kompilovaném spustitelný soubor (.exe) soubor.  
  
 Protože `End` ukončí aplikaci bez vaši účast na všechny prostředky, které může být otevřený, že byste měli zkusit zavřete dolů ještě jednou před jeho použitím. Například pokud vaše aplikace nemá žádné formuláře otevřete, zavřete je před dosáhnou ovládacího prvku `End` příkaz.  
  
 Měli byste použít `End` pouze a pouze pokud je třeba ukončit okamžitě. Běžné způsoby ukončit procedury ([příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) a [ukončení příkazu](../../../visual-basic/language-reference/statements/exit-statement.md)) nejen zavřít řízení, které ještě jednou, ale také poskytnout kód volání možnost Zavřít ještě jednou. Konzolové aplikace, například můžete jednoduše `Return` z `Main` postupu.  
  
> [!IMPORTANT]
>  `End` Příkaz volání <xref:System.Environment.Exit%2A> metodu <xref:System.Environment> třídy v <xref:System> oboru názvů. <xref:System.Environment.Exit%2A>vyžaduje, abyste měli `UnmanagedCode` oprávnění. Pokud ho použít nechcete, <xref:System.Security.SecurityException> dojde k chybě.  
  
 Když následuje další klíčové slovo, [End \<– klíčové slovo > příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) určí konec definici vhodný postup uvedený nebo bloku. Například `End Function` ukončí definice `Function` postupu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `End` příkaz k ukončení provádění kódu, pokud uživatel požaduje.  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 Tento příkaz není podporován.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [Stop – příkaz](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [End \<– klíčové slovo > – příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
