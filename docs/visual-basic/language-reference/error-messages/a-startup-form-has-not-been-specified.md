---
title: "Nebyl zadán formulář spuštění."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fdffc182ee66497d68aafb7dc37cfef75b4d2e9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="a-startup-form-has-not-been-specified"></a>Nebyl zadán formulář spuštění.
Aplikace používá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> třídy, ale neurčuje formulář spuštění.  
  
 Tato situace může nastat, pokud **Povolit aplikační rozhraní** v Návrháři projektu je zaškrtnuté políčko ale **formulář spuštění** není zadán. Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zadejte spouštěcí objekt pro aplikaci.  
  
     Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
2.  Přepsání <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodu a nastavit <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> vlastnost pro formulář spuštění.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>  
 [Přehled aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
