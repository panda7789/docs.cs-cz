---
title: "Ordinální číslo není platné."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ordinal-is-not-valid"></a>Ordinální číslo není platné.
Volání do dynamická knihovna (DLL) uvedené pro použití číslo místo názvu postup pomocí `#num` syntaxe. Tato chyba má následující možné příčiny:  
  
-   Pokus o převést `#num` výraz, který má pořadí se nezdařilo.  
  
-   `#num` Zadaný v knihovně DLL neurčuje žádné funkce.  
  
-   Knihovny typů obsahuje neplatný deklaraci výsledkem interní použití neplatné číslo pořadí.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, zda že výraz představuje platné číslo nebo voláním procedury podle názvu.  
  
2.  Zajistěte, aby `#num` identifikuje platnou funkcí v knihovně DLL.  
  
3.  Izolujte volání procedury příčinou problému pomocí komentářů si kód. Zápis `Declare` příkaz pro postup a sestava tyto potíže k dodavatele knihovny typu.  
  
## <a name="see-also"></a>Viz také  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)
