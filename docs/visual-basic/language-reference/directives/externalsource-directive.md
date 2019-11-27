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
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343834"
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
