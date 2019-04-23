---
title: Objekt nebo třída nepodporuje sadu událostí.
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: ad9176b5332a75f03968e742501c3fce541055de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342879"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Objekt nebo třída nepodporuje sadu událostí.
Pokusili jste se použít `WithEvents` proměnné s komponentou, která nemůže fungovat jako zdroj událostí pro zadanou sadu událostí. Například Kdybyste chtěli zpracování událostí objektu a pak vytvořte jiný objekt, který `Implements` první objekt. I když možná myslíte, že může zpracování událostí z objektu implementované, to není vždy případu. `Implements` pouze implementuje rozhraní pro metody a vlastnosti. `WithEvents` není podporováno pro privátní `UserControls`, protože typ informace potřebné k vyvolání `ObjectEvent` není k dispozici v době běhu.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Nelze jímky událostí pro komponentu, která není zdroje událostí.  
  
## <a name="see-also"></a>Viz také:

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
