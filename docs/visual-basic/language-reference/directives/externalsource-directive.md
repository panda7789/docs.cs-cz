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
ms.openlocfilehash: e4c7704c32c3a6c73e069d0b7129d5386696b438
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402989"
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
 Ukončí `#ExternalSource` blok.  
  
## <a name="remarks"></a>Poznámky  

 Tuto direktivu používá pouze kompilátor a ladicí program.  
  
 Zdrojový soubor může obsahovat externí zdrojové direktivy, které označují mapování mezi konkrétními řádky kódu ve zdrojovém souboru a textem externím ke zdroji, jako je například soubor. aspx. Pokud dojde k chybám v určeném zdrojovém kódu během kompilace, jsou identifikovány jako pocházející z externího zdroje.  
  
 Direktivy externího zdroje nemají žádný vliv na kompilaci a nemohou být vnořené. Jsou určené pouze pro interní použití pouze aplikací.  
  
## <a name="see-also"></a>Viz také

- [Podmíněná kompilace](../../programming-guide/program-structure/conditional-compilation.md)
