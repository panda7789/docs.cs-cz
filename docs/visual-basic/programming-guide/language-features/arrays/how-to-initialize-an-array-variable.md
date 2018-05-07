---
title: 'Postupy: Inicializace proměnné pole v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: ee8cb91fd2fae9637a0d0e33fca63a4cdb9d2fce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Postupy: Inicializace proměnné pole v jazyce Visual Basic
Inicializace proměnné pole zahrnutím literál v pole `New` klauzule a zadat počáteční hodnoty pole. Můžete buď zadat typ nebo umožněte její odvodit z hodnot v poli literálu. Další informace o tom, jak je odvodit typ, najdete v části "Vyplní pole s počáteční hodnoty" v [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Inicializace proměnné pole s použitím pole literálu  
  
-   Buď v `New` klauzuli, nebo když přiřazujete hodnota pole, zadejte hodnoty element uvnitř složené závorky (`{}`). Následující příklad znázorňuje několik způsobů, jak deklarovat, vytvoření a inicializace proměnnou, která bude obsahovat pole, které má elementy typu `Char`.  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     Po provedení každého příkazu, pole, která je vytvořena má délku 3 s prvky na pozici 0 prostřednictvím index 2 obsahující počáteční hodnoty. Pokud zadáte horní mez a hodnoty, musí obsahovat hodnotu pro každý element z indexu 0 prostřednictvím horní mez.  
  
     Všimněte si, že nemáte zadejte index horní mez, pokud zadáte hodnoty prvků v matici literálu. Pokud není zadaný žádný horní mez, je velikost pole odvodit na základě počtu hodnot v poli literálu.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>K chybě při inicializaci proměnnou multidimenzionálního pole pomocí pole literály  
  
-   Vnořit hodnoty v závorkách (`{}`) v rámci složené závorky. Zajistěte, aby literály vnořená pole, které všechny odvození jako pole stejného typu a délka. Následující příklad kódu ukazuje několik příkladů, inicializace multidimenzionálního pole.  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   Můžete explicitně zadat rozsah pole nebo je vynecháte a mít kompilátoru odvození meze pole na základě hodnot v poli literálu. Pokud zadáte horní hranice a hodnoty, musí obsahovat hodnotu pro každý element z indexu 0 prostřednictvím horní hranice v každé dimenze. Následující příklad znázorňuje několik způsobů, jak deklarovat, vytvoření a inicializace proměnné tak, aby obsahovala dvourozměrná pole, která má elementy typu `Short`  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     Po provedení každého příkazu, vytvořené pole obsahuje šest inicializovaného prvky, které mají indexy `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, a `(1,2)`. Každé pole umístění obsahuje hodnotu `10`.  
  
-   V následujícím příkladu prochází multidimenzionálního pole. V aplikaci konzoly systému Windows, který je napsán v jazyce Visual Basic, vložte kód do `Sub Main()` metoda. Poslední komentáře zobrazit výstup.  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>K chybě při inicializaci proměnnou Vícenásobná pole pomocí pole literály  
  
-   Vnořit hodnoty objektu uvnitř složené závorky (`{}`). I když lze také vnořit literály pole, které určují pole různých délek, v případě Vícenásobná pole, ujistěte se, že který literály vnořená pole jsou uzavřené v závorkách (`()`). Závorky vynutit vyhodnocení literály vnořená pole a pole výsledné jsou použity jako počáteční hodnoty Vícenásobná pole. Následující příklad kódu ukazuje dva příklady inicializace Vícenásobná pole.  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   V následujícím příkladu prochází Vícenásobná pole. V aplikaci konzoly systému Windows, který je napsán v jazyce Visual Basic, vložte kód do `Sub Main()` metoda.  Poslední komentáře v kódu zobrazit výstup.  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
