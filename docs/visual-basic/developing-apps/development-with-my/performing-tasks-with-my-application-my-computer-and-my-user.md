---
title: Provádění úloh s objekty My.Application, My.Computer a My.User
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 55961d6857b690fc2726f541df8a5497a3207928
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411691"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Provádění úloh s objekty My.Application, My.Computer a My.User (Visual Basic)

Tři centrální `My` objekty, které poskytují přístup k informacím a běžně používaným funkcím, jsou `My.Application` ( <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> ), `My.Computer` ( <xref:Microsoft.VisualBasic.Devices.Computer> ), a `My.User` ( <xref:Microsoft.VisualBasic.ApplicationServices.User> ). Tyto objekty lze použít pro přístup k informacím, které se vztahují k aktuální aplikaci, počítači, na kterém je aplikace nainstalovaná, nebo aktuálnímu uživateli aplikace, v uvedeném pořadí.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My. Application, my. Computer a my. User  

 Následující příklady ukazují, jak lze informace načíst pomocí `My` .  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 Kromě načítání informací umožňují členové vystavené prostřednictvím těchto tří objektů také spouštět metody související s tímto objektem. Můžete například získat přístup k nejrůznějším metodám pro manipulaci se soubory nebo aktualizovat registr do `My.Computer` .  
  
 Vstupně-výstupní operace se soubory jsou výrazně snazší a rychlejší `My` , což zahrnuje různé metody a vlastnosti pro práci se soubory, adresáři a jednotkami. <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>Objekt umožňuje čtení z velkých strukturovaných souborů, které mají pole s oddělovači nebo s pevnou šířkou. Tento příklad otevře `TextFieldParser` `reader` a použije ho ke čtení z `C:\TestFolder1\test1.txt` .  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application`umožňuje změnit jazykovou verzi aplikace. Následující příklad ukazuje, jak lze tuto metodu volat.  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Závislost oboru názvů My na typu projektu](how-my-depends-on-project-type.md)
