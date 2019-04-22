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
ms.openlocfilehash: 0372fbf63f6d12e266674f92225183911aa4ca30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834038"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Provádění úloh s objekty My.Application, My.Computer a My.User (Visual Basic)
Tři centrální `My` objekty, které poskytují přístup k informacím a běžně používané funkce jsou `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), a `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>). Můžete použít tyto objekty se dostat k informacím, která souvisí s aktuální aplikace, počítači, na kterém je aplikace nainstalovaná na nebo aktuálního uživatele aplikace, v uvedeném pořadí.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>Objekty My.Application, My.Computer a My.User  
 Následující příklady ukazují, jak informace mohou být načteny pomocí `My`.  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 Kromě načítání informací o členy zveřejněné prostřednictvím těchto tří objektů umožňují spouštět metody vztahující se na tento objekt. Například můžete zpřístupnit různé druhy metody pro práci se soubory nebo aktualizaci registru, které prostřednictvím `My.Computer`.  
  
 Soubor vstupně-výstupních operací je výrazně jednodušší a rychlejší při použití `My`, která zahrnuje celou řadu metod a vlastností pro práce se soubory, adresáře a jednotky. <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Objekt umožňuje čtení z velké soubory, které máte oddělených nebo pole s pevnou šířkou. Tento příklad otevře `TextFieldParser` `reader` a používá ke čtení z `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application` Umožňuje změnit jazykové verze pro vaši aplikaci. Následující příklad ukazuje, jak tuto metodu lze volat.  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Závislost oboru názvů My na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
