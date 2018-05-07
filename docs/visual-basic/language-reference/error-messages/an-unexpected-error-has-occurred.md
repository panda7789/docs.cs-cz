---
title: Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 313128d5511ddd0f3b75c58e2c10a74eb967d130
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.
Aplikace se nedá získat prostředek nezbytné operačního systému. Jsou některé možné příčiny tohoto problému:  
  
-   Aplikace nemá oprávnění k vytvoření pojmenovaných objektů operačního systému.  
  
-   Modul common language runtime nemá oprávnění k vytvoření soubory mapované paměti.  
  
-   Aplikace potřebuje přístup k objektu operačního systému, ale jej používá jiný proces.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, že aplikace má dostatečná oprávnění k vytvoření pojmenovaných objektů operačního systému.  
  
2.  Zkontrolujte, zda modul common language runtime má dostatečná oprávnění k vytvoření soubory mapované paměti.  
  
3.  Restartujte počítač zrušte všechny procesy, které může být prostředků potřebné pro připojení k původní instance aplikace.  
  
4.  Poznámka: v případech, za kterých se stala chyba a volání služby Microsoft Product Support Services  
  
## <a name="see-also"></a>Viz také  
 [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Základy ladicího programu](/visualstudio/debugger/debugger-basics)  
 [Kontaktujte nás](/visualstudio/ide/talk-to-us)
