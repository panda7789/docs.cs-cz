---
title: Seznam typů (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: d071e59d94e51ca55167983d0ee3098bd5c7dd8f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843627"
---
# <a name="type-list-visual-basic"></a>Seznam typů (Visual Basic)
Určuje *parametry typu* pro *obecný* programovací element. Více parametrů jsou odděleny čárkami. Následuje syntaxe pro parametr jednoho typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`genericmodifier`|Volitelné. Je možné jenom v obecných rozhraních a delegátech. Je možné deklarovat typ kovariantního pomocí [si](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) – klíčové slovo nebo kontravariantní pomocí [v](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) – klíčové slovo. Zobrazit [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).|  
|`typename`|Povinný parametr. Název parametru typu. Toto je zástupný symbol bude nahrazen určitého typu poskytl argument typu.|  
|`constraintlist`|Volitelné. Seznam všech požadavků, které datový typ, který může být zadán pro `typename`. Pokud máte více omezení, je uzavřete do složených závorek (`{ }`) a oddělit je čárkami. Musí zavést seznamu omezení [jako](../../../visual-basic/language-reference/statements/as-clause.md) – klíčové slovo. Použijete `As` jenom jednou na začátku seznamu.|  
  
## <a name="remarks"></a>Poznámky  
 Každý obecný programovací prvek přijme aspoň jeden parametr typu. Parametr typu je zástupný symbol pro konkrétní typ ( *vytvořený element*), určuje kód klienta při vytváření instance obecného typu. Můžete definovat obecnou třídu, strukturu, rozhraní, postupu nebo delegovat.  
  
 Další informace o při definování obecného typu, najdete v části [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md). Další informace o názvy parametrů typů naleznete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>pravidla  
  
-   **Závorky.** Pokud zadáte seznam parametrů typu, je nutné uzavřít do závorek a musí zavést seznamu [z](../../../visual-basic/language-reference/statements/of-clause.md) – klíčové slovo. Použijete `Of` jenom jednou na začátku seznamu.  
  
-   **Omezení.** Seznam *omezení* typu parametr může obsahovat následující položky v libovolné kombinaci:  
  
    -   Libovolný počet rozhraní. Zadaný typ musí implementovat každé rozhraní v tomto seznamu.  
  
    -   Nejvýše jednu třídu. Zadaný typ musí dědit z této třídy.  
  
    -   `New` – Klíčové slovo. Zadaný typ musí vystavit konstruktor bez parametrů, s přístupem k obecného typu. To je užitečné, pokud omezení parametru typu jeden nebo více rozhraní. Typ, který implementuje rozhraní nevystavuje nutně konstruktor a v závislosti na úrovni přístupu konstruktor nemusí být kód v rámci obecného typu k němu mít přístup.  
  
    -   Buď `Class` – klíčové slovo nebo `Structure` – klíčové slovo. `Class` – Klíčové slovo omezuje parametr obecného typu tak, aby vyžadovala, aby libovolný do něho předaný argument typu být typ odkazu, například řetězce, pole nebo delegáta, nebo vytvoří objekt ze třídy. `Structure` – Klíčové slovo omezí vyžadují, aby libovolný do něho předaný argument typu typ hodnoty, parametr obecného typu, například strukturu, výčet nebo základní datového typu. Nemůže obsahovat oba `Class` a `Structure` ve stejném `constraintlist`.  
  
     Zadaný typ musí splňovat každý požadavek zahrnete `constraintlist`.  
  
     U každého parametru typu omezení jsou nezávislé omezení na jiné parametry typu.  
  
## <a name="behavior"></a>Chování  
  
-   **Náhrada za kompilace.** Při vytváření konstruovaný typ z obecného programovací element je zadat typu definované pro každý parametr typu. Kompilátor jazyka Visual Basic nahradí zadaného typu pro všechny výskyty `typename` v rámci obecného prvku.  
  
-   **Neexistence omezení.** Pokud nezadáte žádné omezení pro parametr typu, je omezený na konzole operations Console a členy, nepodporuje váš kód [datový typ objektu](../../../visual-basic/language-reference/data-types/object-data-type.md) za parametr daného typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definici kostru třídy generický slovník, včetně kostru funkci, kterou chcete přidat novou položku do slovníku.  
  
 [!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Protože `dictionary` je obecný, kód, který používá ho můžete vytvořit různé objekty z něj, každý s stejné funkce, ale funguje na jiný datový typ. Následující příklad ukazuje řádek kódu, který vytváří `dictionary` objekt s `String` položky a `Integer` klíče.  
  
 [!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definici ekvivalentní kostru vygenerované v předchozím příkladu.  
  
 [!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [z](../../../visual-basic/language-reference/statements/of-clause.md)
- [Operátor New](../../../visual-basic/language-reference/operators/new-operator.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Datový typ Object](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [navýšení kapacity](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
