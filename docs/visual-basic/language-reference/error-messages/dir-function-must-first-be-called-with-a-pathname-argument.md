---
title: Funkce 'Dir' musí být nejdříve volána s argumentem 'PathName'.
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 828c715d9aaceef17d030113e7eda302f025ca9d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282583"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>Funkce 'Dir' musí být nejdříve volána s argumentem 'PathName'.
Počáteční volání `Dir` funkce nezahrnuje `PathName` argument. První volání `Dir` musí obsahovat `PathName`, ale následné volání `Dir` není potřeba zahrnovat parametry se mají načíst další položky.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zadat `PathName` argument ve volání funkce.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
