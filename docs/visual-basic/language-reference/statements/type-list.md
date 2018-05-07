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
ms.openlocfilehash: 5fbb07154fce27feb257b431c1726446b42fbfe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="type-list-visual-basic"></a>Seznam typů (Visual Basic)
Určuje, *parametry typu* pro *Obecné* programovací element. Několik parametrů jsou oddělené čárkami. Toto je syntaxe pro jeden typ parametru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`genericmodifier`|Volitelné. Lze použít pouze v obecných rozhraní a delegáti. Je možné deklarovat typu kovariantní pomocí [se](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) – klíčové slovo nebo kontravariant pomocí [v](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) – klíčové slovo. V tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).|  
|`typename`|Požadováno. Název typu parametru. Toto je zástupný symbol, budou nahrazeny určitého typu poskytl argument typu.|  
|`constraintlist`|Volitelné. Seznam požadavků, které určují datový typ, který můžete zadat pro `typename`. Pokud máte více omezení, uzavřete je do složených závorek (`{ }`) a oddělte je čárkami. Je nutné zavést seznamu omezení s [jako](../../../visual-basic/language-reference/statements/as-clause.md) – klíčové slovo. Používáte `As` pouze jednou na začátku seznamu.|  
  
## <a name="remarks"></a>Poznámky  
 Každý obecný programovací element vyžaduje alespoň jeden parametr typu. Parametr typu je zástupný symbol pro konkrétní typ ( *vytvořený element*), kód klienta Určuje, kdy se vytvoří instance obecného typu. Můžete definovat obecné třídy, struktury, rozhraní, postupu nebo delegovat.  
  
 Další informace o při definování obecného typu, najdete v části [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md). Další informace o typu názvy parametrů najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Závorky.** Pokud zadáte seznam parametrů typu, je nutné uzavřít do závorek a je nutné zavést seznamu pomocí [z](../../../visual-basic/language-reference/statements/of-clause.md) – klíčové slovo. Používáte `Of` pouze jednou na začátku seznamu.  
  
-   **Omezení.** Seznam *omezení* parametr pro typ může obsahovat následující položky v libovolné kombinace:  
  
    -   Libovolný počet rozhraní. Zadaný typ musí implementovat každé rozhraní v tomto seznamu.  
  
    -   Maximálně jednu třídu. Zadaný typ musí dědit z této třídy.  
  
    -   `New` – Klíčové slovo. Zadaný typ musí vystavit konstruktor bez parametrů, kterým může přistupovat obecného typu. To je užitečné, pokud omezit parametr typu pomocí jednoho nebo více rozhraní. Typ, který implementuje rozhraní nevystavuje nutně konstruktor, a v závislosti na úroveň přístupu tohoto konstruktoru, nemusí být možné pro přístup k ní kód v rámci obecného typu.  
  
    -   Buď `Class` – klíčové slovo nebo `Structure` – klíčové slovo. `Class` – Klíčové slovo omezí parametr obecného typu, který se požadovat, aby některý typ argument předaný být odkazového typu, například řetězce, pole nebo delegáta, nebo vytvořen objekt ze třídy. `Structure` – Klíčové slovo omezí parametr obecného typu, který se vyžadují, aby některý typ argument předaný typ hodnoty, například strukturu, výčet nebo základní datového typu. Nemůže současně obsahovat `Class` a `Structure` ve stejné `constraintlist`.  
  
     Zadaný typ musí splňovat každý požadavek, můžete zahrnout `constraintlist`.  
  
     Omezení pro každý parametr typu jsou nezávislé na omezení dalších parametrů typu.  
  
## <a name="behavior"></a>Chování  
  
-   **Nahrazení kompilaci.** Při vytváření typu vytvořený z obecné programovací element, můžete zadat určitého typu pro každý parametr typu. Visual Basic – kompilátor nahradí zadaný typu pro každý výskyt `typename` v rámci obecné elementu.  
  
-   **Neexistence omezení.** Pokud nezadáte žádné omezení pro parametr typu, je omezený na operace a členy nepodporuje kódu [Object – datový typ](../../../visual-basic/language-reference/data-types/object-data-type.md) pro tento parametr typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definici kostru obecné slovník třídy, včetně kostru funkci, kterou chcete přidat novou položku do slovníku.  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a>Příklad  
 Protože `dictionary` je obecný, kód, který používá ji můžete vytvořit různé objekty z něj, každý s stejné funkce, ale funguje na jiný datový typ. Následující příklad ukazuje řádek kódu, který vytvoří `dictionary` objektu s `String` položky a `Integer` klíče.  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definici ekvivalentní kostru vygenerované v předchozím příkladu.  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 [z](../../../visual-basic/language-reference/statements/of-clause.md)  
 [Operátor New](../../../visual-basic/language-reference/operators/new-operator.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Datový typ Object](../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [na více systémů](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
