---
title: Provádění úloh s objekty My.Application, My.Computer a My.User (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: bc2b0521598c00cdb398d936d61d65874a9cf274
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Provádění úloh s objekty My.Application, My.Computer a My.User (Visual Basic)
Tři ústřední `My` objekty, které poskytují informace a běžně používané funkce jsou `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), a `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>). Tyto objekty můžete použít pro přístup k informacím, které je aktuální aplikace, počítače, které aplikace se nainstaluje na nebo aktuální uživatel aplikace, v uvedeném pořadí.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>Objekty My.Application, My.Computer a My.User  
 Následující příklady ukazují, jak mohou být informace načíst pomocí `My`.  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 Kromě načítání informací o, členy zveřejněné prostřednictvím tyto tři objekty také umožňují spouštět metody vztahující se na tento objekt. Například můžete zpřístupnit různé způsoby práce se soubory nebo aktualizovat registr prostřednictvím `My.Computer`.  
  
 Soubor vstupně-výstupních operací je výrazně jednodušší a rychlejší s `My`, což zahrnuje celou řadu metod a vlastností pro manipulaci s soubory, adresářů a jednotky. <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Objekt umožňuje číst z velkých strukturované soubory, které mají oddělovače nebo pole s pevnou šířkou. Otevře se v tomto příkladu `TextFieldParser``reader` a používá ke čtení `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 `My.Application` Umožňuje změnit jazykovou verzi pro vaši aplikaci. Následující příklad ukazuje, jak tuto metodu lze volat.  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Závislost oboru názvů My na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
