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
ms.openlocfilehash: fc9fd9093a3db4785bfc94719dbae9ec1d586050
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329583"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Provádění úloh s objekty My.Application, My.Computer a My.User (Visual Basic)

Tři objekty centrálního `My`, které poskytují přístup k informacím a běžně používaným funkcím, jsou `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>) a `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>). Tyto objekty lze použít pro přístup k informacím, které se vztahují k aktuální aplikaci, počítači, na kterém je aplikace nainstalovaná, nebo aktuálnímu uživateli aplikace, v uvedeném pořadí.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My. Application, my. Computer a my. User  

 Následující příklady ukazují, jak lze informace načíst pomocí `My`.  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 Kromě načítání informací umožňují členové vystavené prostřednictvím těchto tří objektů také spouštět metody související s tímto objektem. Můžete například získat přístup k nejrůznějším metodám pro manipulaci se soubory nebo aktualizovat registr prostřednictvím `My.Computer`.  
  
 I/O soubor je u `My`mnohem jednodušší a rychlejší, což zahrnuje různé metody a vlastnosti pro manipulaci se soubory, adresáři a jednotkami. Objekt <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> umožňuje čtení z velkých strukturovaných souborů, které mají pole s oddělovači nebo s pevnou šířkou. Tento příklad otevře `TextFieldParser` `reader` a použije ho ke čtení z `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application` umožňuje změnit jazykovou verzi vaší aplikace. Následující příklad ukazuje, jak lze tuto metodu volat.  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Závislost oboru názvů My na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
