---
title: 'Při vytváření manifestu sestavení došlo k chybě: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 560635718a931cc9cdb687154a1d23970136de97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972289"
---
# <a name="error-creating-assembly-manifest-error-message"></a>Chyba při vytváření manifestu sestavení \<: chybová zpráva >
Kompilátor Visual Basic volá linker sestavení (Al. exe, označovaný také jako ALink), aby vygeneroval sestavení s manifestem. Linker oznámil chybu v předprodukční fázi vytváření sestavení.  
  
 K tomu může dojít, pokud dojde k potížím se souborem klíče nebo s určeným kontejnerem klíčů. Pro úplné podepsání sestavení je nutné zadat platný soubor klíče, který obsahuje informace o veřejných a privátních klíčích. Chcete-li zpozdit podepsání sestavení, je nutné zaškrtnout políčko **pouze zpožděné znaménko** a zadat platný soubor klíče, který obsahuje informace o informacích o veřejném klíči. Privátní klíč není nezbytný, pokud je sestavení podepsáno opožděně. Další informace najdete v tématu [jak: Podepište sestavení silným názvem](../../../standard/assembly/sign-strong-name.md).  
  
 **ID chyby:** BC30140  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Prohlédněte si chybovou zprávu v uvozovkách a Projděte si téma [Al. exe](../../../framework/tools/al-exe-assembly-linker.md). Další vysvětlení a Rady k chybě AL1019  
  
2. Pokud chyba přetrvává, shromážděte informace o okolnostech a upozorněte služby podpory společnosti Microsoft.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Podepsat sestavení silným názvem](../../../standard/assembly/sign-strong-name.md)
- [Stránka Podepisování, Návrhář projektu](/visualstudio/ide/reference/signing-page-project-designer)
- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Kontaktujte nás](/visualstudio/ide/talk-to-us)
