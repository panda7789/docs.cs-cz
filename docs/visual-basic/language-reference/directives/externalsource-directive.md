---
title: '#ExternalSource – direktiva'
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
ms.openlocfilehash: 146ab41d74b45acc4063e2463baca26c7caa4652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586588"
---
# <a name="externalsource-directive"></a>#ExternalSource – direktiva
Určuje mapování mezi konkrétní řádků zdrojového kódu a textové externí zdroj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Součásti  
 `StringLiteral`  
 Cesta k externí zdroj.  
  
 `IntLiteral`  
 Číslo řádku prvního řádku externí zdroje.  
  
 `LogicalLine`  
 Na řádku, kde dojde k chybě v externím zdroji.  
  
 `#End ExternalSource`  
 Ukončí `#ExternalSource` bloku.  
  
## <a name="remarks"></a>Poznámky  
 Tato direktiva je používána pouze kompilátor a ladicí program.  
  
 Zdrojový soubor může obsahovat direktivy externího zdroje, které označují mapování mezi konkrétní řádky kódu ve zdrojovém souboru a text externí zdroj, například soubor .aspx. Pokud dojde k chybám v určené zdrojový kód během kompilace, jsou identifikovány jako pocházející z externího zdroje.  
  
 Externí zdroj direktivy mít žádný vliv na kompilace a nelze je vnořovat. Ty jsou určené aplikací pouze pro interní použití.  
  
## <a name="see-also"></a>Viz také  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
