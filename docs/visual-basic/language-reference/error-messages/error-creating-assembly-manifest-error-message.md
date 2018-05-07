---
title: 'Chyba při vytváření sestavení manifestu: &lt;chybová zpráva&gt;'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: b3ea5b502abd318c34d957bf7f540602c53c9e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Chyba při vytváření sestavení manifestu: &lt;chybová zpráva&gt;
Visual Basic – kompilátor volá Linker sestavení (Al.exe, také známé jako Alink) ke generování sestavení s manifestu. Linkeru ohlásilo chybu ve fázi před emisí vytváření sestavení.  
  
 Tato situace může nastat, pokud dochází k problémům s souboru klíče nebo klíče zadaný kontejner. Chcete-li plně podepsání sestavení, je nutné zadat platný soubor klíče, který obsahuje informace o veřejné a soukromé klíče. Zpoždění podepsání sestavení, musíte vybrat **zpoždění podepsání** zaškrtněte políčko a zadejte platný soubor klíče, který obsahuje informace o informace o veřejném klíči. Privátní klíč není nutné, pokud je sestavení podepsané zpoždění. Další informace najdete v tématu [postupy: podepsání sestavení se silným názvem](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 **ID chyby:** BC30140  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Prověřením uvozovkách chybové zprávy a podívejte se téma [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). došlo k chybě AL1019 další vysvětlení a Rady, jak  
  
2.  Pokud potíže potrvají, shromažďovat informace o okolnostech a upozornění služby Microsoft Product Support Services.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Podepsání sestavení silným názvem](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Stránka Podepisování, Návrhář projektu](/visualstudio/ide/reference/signing-page-project-designer)  
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
 [Kontaktujte nás](/visualstudio/ide/talk-to-us)
