---
title: '#ExternalSource – direktiva (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: dcde8507eb033d0a47d5c5d3fa36176cd63b0856
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861781"
---
# <a name="externalsource-directive"></a>#ExternalSource – direktiva
Určuje mapování mezi konkrétní řádky zdrojového kódu a textem mimo zdroj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Součásti  
 `StringLiteral`  
 Cesta k externího zdroje.  
  
 `IntLiteral`  
 Číslo řádku prvního řádku externího zdroje.  
  
 `LogicalLine`  
 Na řádku, kde dojde k chybě v externím zdroji.  
  
 `#End ExternalSource`  
 Ukončuje `#ExternalSource` bloku.  
  
## <a name="remarks"></a>Poznámky  
 Tato direktiva se používá pouze v kompilátoru a ladicí program.  
  
 Zdrojový soubor může obsahovat direktivy externího zdroje, které označují mapování mezi konkrétní řádky kódu ve zdrojovém souboru a textem mimo zdroj, například soubor .aspx. Pokud nedojde k chybám v kódu zdrojové během kompilace, jsou identifikované jako pocházející z externího zdroje.  
  
 Direktivy externího zdroje nemají žádný vliv při kompilaci a nemohou být vnořeny. Ty jsou určené pro interní použití jenom aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
