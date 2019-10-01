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
ms.openlocfilehash: ac7096e998dd8d2a416dc739e1d7625e1abff7a6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696828"
---
# <a name="externalsource-directive"></a>#ExternalSource – direktiva
Označuje mapování mezi konkrétními řádky zdrojového kódu a textem externím ke zdroji.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Součásti  
 `StringLiteral`  
 Cesta k externímu zdroji  
  
 `IntLiteral`  
 Číslo řádku prvního řádku externího zdroje.  
  
 `LogicalLine`  
 Řádek, kde dojde k chybě v externím zdroji.  
  
 `#End ExternalSource`  
 Ukončí blok `#ExternalSource`.  
  
## <a name="remarks"></a>Poznámky  
 Tuto direktivu používá pouze kompilátor a ladicí program.  
  
 Zdrojový soubor může obsahovat externí zdrojové direktivy, které označují mapování mezi konkrétními řádky kódu ve zdrojovém souboru a textem externím ke zdroji, jako je například soubor. aspx. Pokud dojde k chybám v určeném zdrojovém kódu během kompilace, jsou identifikovány jako pocházející z externího zdroje.  
  
 Direktivy externího zdroje nemají žádný vliv na kompilaci a nemohou být vnořené. Jsou určené pouze pro interní použití pouze aplikací.  
  
## <a name="see-also"></a>Viz také:

- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
