---
title: "Objekt nebo třída nepodporuje sadu událostí."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Objekt nebo třída nepodporuje sadu událostí.
Pokusili jste se použít `WithEvents` proměnné s komponenty, která nemůže pracovat jako zdroje událostí pro zadanou sadu událostí. Například Kdybyste chtěli jímky událostí objektu a pak vytvořte jiný objekt, který `Implements` první objekt. I když může si myslíte, že by mohla jímky událostí z implementovaná objektu, to není vždy případu. `Implements`pouze implementuje rozhraní pro metody a vlastnosti. `WithEvents`není podporováno pro privátní `UserControls`, protože typ informace potřebné k vyvolat `ObjectEvent` není k dispozici v době běhu.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nelze jímky událostí pro komponenty, která není zdroje událostí.  
  
## <a name="see-also"></a>Viz také  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [Implements – příkaz](../../../visual-basic/language-reference/statements/implements-statement.md)
