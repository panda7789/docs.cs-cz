---
title: 'Postupy: Inicializace proměnné pole'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 7feaf71fa1c59c24aa751f2b9e28328d47ba357c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413063"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Postupy: Inicializace proměnné pole v jazyce Visual Basic
Inicializujete proměnnou pole zahrnutím literálu pole do `New` klauzule a určením počátečních hodnot pole. Můžete buď zadat typ, nebo ho nechat odvoditelné z hodnot v literálu pole. Další informace o tom, jak je typ odvozen, naleznete v části "vyplnění pole počátečními hodnotami" v [polích](index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Inicializace proměnné pole pomocí literálu pole  
  
- Buď v `New` klauzuli, nebo při přiřazení hodnoty pole zadejte hodnoty elementu do složených závorek ( `{}` ). Následující příklad ukazuje několik způsobů, jak deklarovat, vytvořit a inicializovat proměnnou tak, aby obsahovala pole s prvky typu `Char` .  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     Po spuštění každého příkazu má pole vytvořené délku 3 s prvky v indexu 0 až index 2 obsahující počáteční hodnoty. Pokud zadáte horní mez a hodnoty, je nutné zahrnout hodnotu pro každý prvek z indexu 0 až po horní mez.  
  
     Všimněte si, že není nutné zadat horní mez indexu, pokud zadáváte hodnoty prvků v literálu pole. Pokud není zadána žádná horní mez, je velikost pole odvozena v závislosti na počtu hodnot v literálu pole.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Inicializace proměnné multidimenzionálního pole pomocí literálů pole  
  
- Vnořit hodnoty do složených závorek ( `{}` ) uvnitř složených závorek (). Zajistěte, aby literály vnořeného pole byly odvozeny jako pole stejného typu a délky. Následující příklad kódu ukazuje několik příkladů inicializace multidimenzionálního pole.  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- Můžete explicitně zadat hranice pole nebo je nechat vypnout a nechat kompilátor odvodit hranice pole na základě hodnot v literálu pole. Pokud zadáte horní meze i hodnoty, je nutné zahrnout hodnotu pro každý prvek z indexu 0 až po horní mez v každé dimenzi. Následující příklad ukazuje několik způsobů, jak deklarovat, vytvořit a inicializovat proměnnou tak, aby obsahovala dvourozměrné pole, které má prvky typu`Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     Po spuštění každého příkazu obsahuje vytvořené pole šest inicializovaných prvků, které mají indexy `(0,0)` , `(0,1)` ,,, `(0,2)` `(1,0)` `(1,1)` a `(1,2)` . Každé umístění pole obsahuje hodnotu `10` .  
  
- Následující příklad provede iteraci multidimenzionálního pole. V konzolové aplikaci systému Windows, která je napsána v Visual Basic, vložte kód do `Sub Main()` metody. Poslední komentáře ukazují výstup.  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Inicializace proměnné vícenásobného pole pomocí literálů pole  
  
- Hodnoty vnořených objektů do složených závorek ( `{}` ). I když lze také vnořit literály pole, které určují pole různých délek, v případě vícenásobného pole se ujistěte, že literály vnořeného pole jsou uzavřeny v závorkách ( `()` ). Závorky vynutí vyhodnocení literálů vnořeného pole a výsledná pole se používají jako počáteční hodnoty nevícenásobného pole. Následující příklad kódu ukazuje dva příklady inicializace vícenásobného pole.  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- Následující příklad projde vícenásobné pole. V konzolové aplikaci systému Windows, která je napsána v Visual Basic, vložte kód do `Sub Main()` metody.  Poslední komentáře v kódu ukazují výstup.  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Viz také

- [Pole](index.md)
- [Řešení potíží s poli](troubleshooting-arrays.md)
