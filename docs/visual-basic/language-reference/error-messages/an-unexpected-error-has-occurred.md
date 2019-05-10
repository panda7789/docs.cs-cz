---
title: Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 8130eee93ab5c14043283c28f522da53f9047e85
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646888"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.
Aplikaci nebylo možné získat prostředek operačního systému nutné. Zde jsou některé možné příčiny tohoto problému:  
  
- Aplikace nemá oprávnění k vytvoření pojmenovaných objektů operačního systému.  
  
- Modul common language runtime nemá oprávnění k vytvoření souborů mapovaných do paměti.  
  
- Aplikace potřebuje pro přístup k objektu operačního systému, ale používá jiný proces.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zkontrolujte, zda má dostatečná oprávnění k vytvoření aplikace s názvem objekty operačního systému.  
  
2. Zkontrolujte, zda modul common language runtime má dostatečná oprávnění k vytvoření souborů mapovaných do paměti.  
  
3. Restartujte počítač a zrušte všechny procesy, které mohou být zdroje potřebné pro připojení k původní instanci aplikace.  
  
4. Všimněte si okolnosti, kdy došlo k chybě a volat Microsoft Product Support Services  
  
## <a name="see-also"></a>Viz také:

- [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Základy ladicího programu](/visualstudio/debugger/debugger-basics)
- [Kontaktujte nás](/visualstudio/ide/talk-to-us)
