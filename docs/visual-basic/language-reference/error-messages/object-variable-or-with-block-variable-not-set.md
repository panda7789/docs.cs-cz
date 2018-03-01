---
title: "Objektová proměnná nebo proměnná bloku With nebyla nastavena."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e1f587e194acf744b6ec9b8f1bede3acef7b753
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Objektová proměnná nebo proměnná bloku With nebyla nastavena.
Odkazuje na neplatný objekt proměnnou.   Této chybě může dojít z několika důvodů:  
  
-   Proměnná byla deklarována bez zadání typu. Pokud je proměnná deklarována bez zadání typu, výchozí hodnoty na typ `Object`.  
  
     Například proměnná definovaná s `Dim x` by být typu `Object;` proměnné deklarovat s `Dim x As String` by být typu `String`.  
  
    > [!TIP]
    >  `Option Strict` Příkaz zakáže implicitní zadáte, která způsobí, že `Object` typu. Pokud není typu, dojde k chybě kompilace. V tématu [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
-   Pokoušíte se odkazovat na objekt, který je nastavený na`Nothing`  
  
     .  
  
-   Chcete získat přístup k elementu proměnná typu pole, který nebyl deklarován správně.  
  
     Například pole deklarované jako `products() As String` chyba se aktivuje, pokud se pokusíte odkazovat na prvek pole `products(3) = "Widget"`. Toto pole je žádné elementy a je považován za objekt.  
  
-   Pokoušíte se přístupového kódu v rámci `With...End With` blokovat před inicializací bloku.   A `With...End With` bloku se musí inicializovat spuštěním `With` příkaz vstupní bod.  
  
> [!NOTE]
>  V dřívějších verzích systému Visual Basic nebo VBA tato chyba byla aktivována také přiřazením hodnoty proměnné bez použití `Set` – klíčové slovo (`x = "name"` místo `Set x = "name"`). `Set` – Klíčové slovo již není platný v jazyce Visual Basic .net.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nastavit `Option Strict` k `On` přidáním následující kód do začátku souboru:  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  Pokud chcete povolit `Option Strict`, vyhledávání kódu pro všechny proměnné, které bylo zadáno bez typu (`Dim x` místo `Dim x As String`) a přidejte typ určený k deklaraci.  
  
3.  Zajistěte, aby nejsou odkazující na objektová proměnná, která byla nastavena na `Nothing`.  Hledání kódu pro klíčové slovo `Nothing`a zkontrolovat, jestli váš kód tak, aby objekt není nastavený na `Nothing` až poté, co jste odkazuje.  
  
4.  Ujistěte se, že jsou všechny proměnné pole dimenzovány předtím, než k nim přístup. Je možné přiřadit dimenzi při prvním vytváření pole (`Dim x(5) As String` místo `Dim x() As String`), nebo použijte `ReDim` – klíčové slovo nastavit rozměry pole před první přístup.  
  
5.  Zajistěte, aby vaše `With` bloku je inicializovat spuštěním `With` příkaz vstupní bod.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace proměnné objektu](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [ReDim – příkaz](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [S... End With – příkaz](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
