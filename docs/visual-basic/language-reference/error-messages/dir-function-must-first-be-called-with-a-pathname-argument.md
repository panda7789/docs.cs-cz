---
title: Funkce 'Dir' musí být nejdříve volána s argumentem 'PathName'.
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: d255b8dddd098835764f72b8a166eaa08b0353df
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323639"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>Funkce 'Dir' musí být nejdříve volána s argumentem 'PathName'.
Počáteční volání `Dir` funkce nezahrnuje `PathName` argument. První volání `Dir` musí obsahovat `PathName`, ale následné volání `Dir` není potřeba zahrnovat parametry se mají načíst další položky.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zadat `PathName` argument ve volání funkce.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
