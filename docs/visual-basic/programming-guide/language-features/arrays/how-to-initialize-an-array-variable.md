---
title: 'Postupy: Inicializace proměnné pole v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 0e450a370c27de4690105231847de25ce5a90553
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627456"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Postupy: Inicializace proměnné pole v jazyce Visual Basic
Inicializujte proměnnou pole včetně literálu pole v `New` klauzule a určením počáteční hodnoty pole. Můžete zadat typ nebo umožnit jeho odvození z hodnot v literálu pole. Další informace o tom, jak je odvozený typ, naleznete v tématu "Vyplnění pole počátečními hodnotami" v [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Inicializace proměnné pole pomocí literálu pole  
  
- Buď `New` klauzuli, nebo když přiřadíte hodnotu pole, zadejte hodnoty elementů uvnitř závorek (`{}`). Následující příklad ukazuje několik způsobů, jak deklarovat, vytvářet a inicializovat proměnnou tak, aby obsahovala pole s prvky typu `Char`.  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     Po spuštění všech příkazů má vytvořené pole délku 3, přičemž prvky v indexu 0 až 2 obsahují počáteční hodnoty. Pokud zadáte horní mez a hodnoty, je nutné zahrnout hodnotu pro každý prvek od indexu 0 až po horní mez.  
  
     Všimněte si, že nemusíte určit horní mez indexu, pokud zadáte hodnoty elementu v literálu pole. Pokud není zadána žádná horní mez, velikost pole odvozena na základě počtu hodnot literálu pole.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Inicializace vícedimenzovaného pole pomocí literálů pole  
  
- Vnořené hodnoty uvnitř složených závorek (`{}`) v závorkách. Ujistěte se, že jsou vnořené literály pole, které všechny odvozené jako pole stejného typu a délky. Následující příklad kódu ukazuje několik příkladů inicializace multidimenzionálního pole.  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- Můžete explicitně určit hranice pole nebo je vynechat a nechat kompilátor odvodit hranice pole na základě hodnot v literálu pole. Pokud zadáte horní mez a hodnoty, je nutné zahrnout hodnotu pro každý prvek od indexu 0 až po horní mez v každém rozměru. Následující příklad ukazuje několik způsobů, jak deklarovat, vytvářet a inicializovat proměnnou tak, aby obsahovala dvojrozměrné pole obsahující prvky typu `Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     Po spuštění všech příkazů obsahuje vytvořené pole šest inicializovaných prvků s indexy `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, a `(1,2)`. Každé umístění pole obsahuje hodnotu `10`.  
  
- Následující příklad provede iteraci multidimenzionálního pole. V konzolové aplikaci Windows, která je napsána v jazyce Visual Basic, vložte kód do `Sub Main()` metody. Poslední komentáře popisují výstup.  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Inicializace proměnné vícenásobného pole pomocí literálů pole  
  
- Hodnoty objektu vložte uvnitř složených závorek (`{}`). Ačkoli lze také vnořit literály pole, které specifikují pole různé délky, v případě vícenásobného pole, ujistěte se, že jsou vnořené literály pole uzavřeny do závorek (`()`). Závorky vynutí vyhodnocení literály vnořeného pole a výsledná pole jsou použita jako počáteční hodnoty vícenásobného pole. Následující příklad kódu ukazuje dva příklady inicializace vícenásobného pole.  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- Následující příklad provede iteraci vícenásobného pole. V konzolové aplikaci Windows, která je napsána v jazyce Visual Basic, vložte kód do `Sub Main()` metody.  Poslední komentáře v kódu popisují výstup.  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Viz také:

- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
