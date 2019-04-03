---
title: Ordinální číslo není platné.
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: f3207c2cc237ae22c295c2b3ed56f18601625226
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822246"
---
# <a name="ordinal-is-not-valid"></a>Ordinální číslo není platné.
Volání dynamická knihovna (DLL) uvedené číslo nahrazujícím název procedury pomocí `#num` syntaxe. Tato chyba má následující možné příčiny:  
  
-   Pokus o převod `#num` výraz, který se ordinální číslo se nezdařil.  
  
-   `#num` Zadané neurčuje žádné funkce v knihovně DLL.  
  
-   Knihovna typů má neplatnou deklarací výsledkem interní použití neplatné ordinální číslo.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že výraz představuje platné číslo nebo voláním procedury podle názvu.  
  
2.  Ujistěte se, že `#num` identifikuje platná funkce v knihovně DLL.  
  
3.  Vzájemnou izolací volání procedury, které jsou příčinou problému, tak kód. Zápis `Declare` příkaz pro postup a sestavy problém, který chcete dodavatele knihovny typů.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
