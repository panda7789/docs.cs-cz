---
title: Nebyl zadán formulář spuštění.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 301f249e6222c929d2c513964ecbb21df5fbc47f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976196"
---
# <a name="a-startup-form-has-not-been-specified"></a>Nebyl zadán formulář spuštění.

Aplikace používá třídu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>, ale neurčuje úvodní formulář.  
  
 K této chybě může dojít, pokud je v Návrháři projektu zaškrtnuto políčko **Povolit rozhraní aplikace** , ale **formulář spuštění** není zadán. Další informace naleznete na [stránce aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zadejte spouštěcí objekt pro aplikaci.  
  
     Další informace naleznete na [stránce aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
2. Přepište metodu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> a nastavte vlastnost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> na úvodní formulář.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [Přehled aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
