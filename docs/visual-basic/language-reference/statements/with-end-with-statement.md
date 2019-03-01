---
title: With...End With – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: b9d2ce983398f34747f09d4ffd2cc8fa9e6b2b53
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968254"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With – příkaz (Visual Basic)
Vykoná řadu příkazů, které opakovaně odkazují na jeden objekt nebo strukturu, takže příkazy mohou při přístupu k členům tohoto objektu nebo struktury použít zjednodušenou syntaxi.  Při použití struktury lze pouze číst hodnoty členů nebo vyvolávat metody a dojde k chybě, pokud se pokusíte přiřadit hodnoty k členům struktury použité v `With...End With` příkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`objectExpression`|Povinný parametr. Výraz, který se vyhodnotí na objekt. Výraz může být libovolně složitý a vyhodnotí se pouze jednou. Výraz lze vyhodnotit na libovolný datový typ včetně základních typů.|  
|`statements`|Volitelné. Jeden nebo více příkazů mezi `With` a `End With` , které mohou odkazovat na členy objektu vzniklého vyhodnocením `objectExpression`.|  
|`End With`|Povinný parametr. Ukončí definici `With` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 S použitím `With...End With`, můžete provádět řadu příkazů pro zadaný objekt bez zadání názvu objektu více než jednou. V rámci `With` blok příkazů, můžete určit člen objektu začínající tečkou, jako kdyby `With` ním byl objekt příkazu.  
  
 Chcete-li změnit více vlastností jednoho objektu, například umístit příkazy pro přiřazení vlastnosti uvnitř `With...End With` bloku, odkazující na tento objekt pouze jednou ne u každého přiřazení vlastnosti.  
  
 Pokud váš kód přistupuje ke stejným objektu ve více příkazech, získáte následující výhody pomocí `With` – příkaz:  
  
-   Nemusíte vyhodnocovat složitý výraz vícekrát ani přiřazovat výsledek k dočasné proměnné, chcete-li na jeho členy odkazovat vícekrát.  
  
-   Odstraněním opakovaných kvalifikačních výrazů zlepšíte přehlednost kódu.  
  
 Datový typ `objectExpression` může být libovolné třídy nebo typ struktury nebo dokonce základní typ jazyka Visual Basic například `Integer`.  Pokud `objectExpression` výsledky v nic jiného než objekt, můžete pouze číst hodnoty jeho členů nebo vyvolávat metody a dojde k chybě, pokud se pokusíte přiřadit hodnoty k členům struktury použité v `With...End With` příkazu.  Toto je ke stejné chybě kdyby jste vyvolali metodu, která vrátila strukturu a okamžitě získat přístup a přiřadili hodnotu člena výsledku této funkce, jako například `GetAPoint().x = 1`.  Problémem je v obou případech to, že tato struktura existuje pouze v zásobníku volání a neexistuje žádný způsob, jak člena změněné struktury v těchto situacích zapsat někam tak, aby jakýkoli jiný kód v programu tuto změnu zpozoroval.  
  
 `objectExpression` Se vyhodnotí jednou při vstupu do bloku. Přiřazení nemůžete nastavit `objectExpression` v rámci `With` bloku.  
  
 V rámci `With` bloku, máte přístup bez kvalifikování metody a vlastnosti pouze zadaného objektu. Můžete použít metody a vlastnosti jiného objektu, musíte je ale kvalifikovat pomocí názvů jejich objektů.  
  
 Můžete umístit jeden `With...End With` příkaz v rámci jiného. Vnořené `With...End With` příkazy mohou být matoucí, pokud objekty, které se odkazuje, nejsou zřejmé z kontextu. Je nutné zadat plně kvalifikovaný odkaz na objekt, který je ve vnějším `With` blokovat, pokud objekt odkazován z vnitřního `With` bloku.  
  
 Nelze větvit do `With` blok příkazů z mimo blok.  
  
 Pokud blok neobsahuje cyklus, spustí se příkazy pouze jednou. Je možné vnořovat různé druhy řídicích struktur. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  Můžete použít `With` – klíčové slovo v inicializátorech objektu také. Další informace a příklady najdete v tématu [inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) a [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
>   
>  Pokud používáte `With` blok jenom k inicializaci vlastností nebo polí objektu, který jste právě vytvořena, zvažte místo toho použít inicializátor objektu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu každý `With` blok se spustí řadu příkazů u jednoho objektu.  
  
 [!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá vnořené `With…End With` příkazy. Uvnitř vnořeného `With` prohlášení, odkazuje syntaxe na vnitřní objekt.  
  
 [!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Collections.Generic.List%601>
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
