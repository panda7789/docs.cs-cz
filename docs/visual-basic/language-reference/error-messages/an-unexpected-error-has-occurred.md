---
title: Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 640e32dc7f748ecd0a999a8432512103f46862c2
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976181"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.

Aplikaci se nepovedlo získat potřebný prostředek operačního systému. Mezi možné příčiny tohoto problému patří:  
  
- Aplikace nemá oprávnění k vytváření pojmenovaných objektů operačního systému.  
  
- Modul CLR (Common Language Runtime) nemá oprávnění k vytváření souborů mapovaných do paměti.  
  
- Aplikace potřebuje přístup k objektu operačního systému, ale používá ho jiný proces.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ověřte, zda má aplikace dostatečná oprávnění k vytváření pojmenovaných objektů operačního systému.  
  
2. Ověřte, zda má modul common language runtime dostatečná oprávnění k vytváření souborů mapovaných do paměti.  
  
3. Restartujte počítač a zrušte tak všechny procesy, které mohou používat prostředek potřebný pro připojení k původní instanci aplikace.  
  
4. Poznamenejte si okolnosti, za kterých došlo k chybě, a zavolejte služby Microsoft Product Support.  
  
## <a name="see-also"></a>Viz také:

- [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Základy ladicího programu](/visualstudio/debugger/debugger-basics)
- [Kontaktujte nás](/visualstudio/ide/feedback-options)
