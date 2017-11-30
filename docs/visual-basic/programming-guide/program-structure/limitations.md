---
title: "Omezení jazyka Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97a2e162b9f1a673fbe805a5d2ef1421cd423a4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-limitations"></a>Omezení jazyka Visual Basic
Starší verze [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vynutit hranice v kódu, jako je délka názvy proměnných, počet proměnných v moduly a velikost modulu povoleny. V jazyce Visual Basic .NET tato omezení mít byla zmírnit, která poskytuje větší svobodu v psaní a uspořádání kódu.  
  
 Fyzické omezení jsou závislé více běhové paměti než v době kompilace aspekty. Pokud používáte doporučeno programovací postupy a velké aplikace rozdělte do více tříd a moduly, pak je velmi malé pravděpodobnost vzniku interní [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] omezení.  
  
 Tady jsou některá omezení, které se mohou vyskytnout ve výjimečných případech:  
  
-   **Délka názvu.** Maximální počet znaků pro název každé deklarované programovací element není k dispozici. Tento maximální platí pro řetězec celý kvalifikace v případě, že je kvalifikovaný název elementu. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Délka řádku.** Je delší než 65 535 znaků na fyzické řádku zdrojového kódu. Řádek kódu logické zdroj může být delší, pokud používáte znaky pokračování řádku. V tématu [postupy: přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Rozměry pole.** Je maximální počet dimenzí, které můžou deklarovat pro pole. Toto nastavení omezuje počet indexů, můžete použít k určení k elementu pole. V tématu [pole dimenzí v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Délka řetězce.** Je maximální počet znaků Unicode, kam můžete ukládat v jednom řetězci. V tématu [řetězcový datový typ](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Délka řetězce prostředí.** Je delší než 32768 znaků pro libovolný řetězec prostředí použít jako argument příkazového řádku. Jedná se o omezení na všech platformách.  
  
## <a name="see-also"></a>Viz také  
 [Struktura programu a pravidla týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
