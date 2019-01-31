---
title: 'Při vytváření manifestu sestavení došlo k chybě: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: f9c8d9fe4b8bea45e4b655415b044937f248deab
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266478"
---
# <a name="error-creating-assembly-manifest-error-message"></a>Chyba při vytváření manifestu sestavení: \<chybová zpráva >
Kompilátor jazyka Visual Basic volá Assembly Linker (Al.exe, označované také jako Alink) ke generování sestavení s manifestem. Linker ohlásilo chybu ve fázi předběžného emisí vytváření sestavení.  
  
 Tato situace může nastat, pokud dochází k problémům s souboru klíče nebo kontejneru klíčů určeném. Chcete-li plně podepsat sestavení, je nutné zadat platný soubor s klíčem, který obsahuje informace o veřejných a privátních klíčů. Zpoždění podepsání sestavení, musíte vybrat **zpoždění podepsání** zaškrtněte políčko a zadejte platný soubor s klíčem, který obsahuje informace o informace o veřejném klíči. Privátní klíč není nezbytné, pokud sestavení se zpožděným podpisem. Další informace najdete v tématu [jak: Podepsání sestavení silným názvem](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 **ID chyby:** BC30140  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte v uvozovkách chybovou zprávu a najdete v tématu [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). pro další vysvětlení chyby AL1019 a poradenství  
  
2.  Pokud potíže potrvají, shromážděte informace o okolnostech a upozornit Microsoft Product Support Services.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Podepsání sestavení silným názvem](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [Stránka podepisování, Návrhář projektu](/visualstudio/ide/reference/signing-page-project-designer)
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
- [Kontaktujte nás](/visualstudio/ide/talk-to-us)
