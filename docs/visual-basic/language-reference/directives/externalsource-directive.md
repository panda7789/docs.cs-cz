---
title: "#<a name=\"externalsource-directive\"></a>ExternalSource – direktiva"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "160"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f90b838e50b65b8652cd9cf6f6ee084e9552f025
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
