---
title: Typy hodnot a typy odkazu
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 466bb5386235917705344d35c5141c8bf779218d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582648"
---
# <a name="value-types-and-reference-types"></a>Typy hodnot a typy odkazu
Existují dva druhy typů v Visual Basic: typy odkazu a typy hodnot. Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data. V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou. S typy hodnot každá proměnná má svou vlastní kopii dat a není možné, aby operace s jednou proměnnou ovlivnily jiný (kromě případu, kdy [Modifikátor ByRef u parametrů](../../../language-reference/modifiers/byref.md)).
  
## <a name="value-types"></a>Typy hodnot  
 Datový typ je *typ hodnoty* , pokud obsahuje data v rámci své vlastní alokace paměti. Typy hodnot zahrnují následující:  
  
- Všechny číselné datové typy  
  
- `Boolean`, `Char` a `Date`  
  
- Všechny struktury, i když jejich členové jsou odkazové typy  
  
- Výčty, protože jejich nadřízený typ je vždy `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger` nebo `ULong`  
  
 Každá struktura je typ hodnoty, a to i v případě, že obsahuje členy typu odkazu. Z tohoto důvodu jsou typy hodnot, například `Char` a `Integer`, implementovány pomocí .NET Framework struktury.  
  
 Typ hodnoty lze deklarovat pomocí klíčového slova rezervované, například `Decimal`. Můžete také použít klíčové slovo `New` k inicializaci typu hodnoty. To je užitečné hlavně v případě, že typ má konstruktor, který přebírá parametry. Příkladem je <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktor, který vytváří novou hodnotu `Decimal` ze zadaných částí.  
  
## <a name="reference-types"></a>Typy odkazů  
 *Odkazový typ* ukládá odkaz na jeho data. Typy odkazů zahrnují následující:  
  
- `String`  
  
- Všechna pole, i když jejich prvky jsou typy hodnot  
  
- Typy tříd, například <xref:System.Windows.Forms.Form>  
  
- Delegáty  
  
 Třída je *odkazový typ*. Všimněte si, že každé pole je typ odkazu, a to i v případě, že jeho členy jsou typy hodnot.  
  
 Vzhledem k tomu, že každý typ odkazu představuje základní třídu .NET Framework, je nutné při inicializaci použít klíčové slovo [New operátor](../../../../visual-basic/language-reference/operators/new-operator.md) . Následující příkaz inicializuje pole.  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Prvky, které nejsou typy  
 Následující programovací prvky neopravňují jako typy, protože nemůžete zadat žádné z nich jako datový typ pro deklarovaný element:  
  
- Jmenné prostory  
  
- Moduly  
  
- Události  
  
- Vlastnosti a procedury  
  
- Proměnné, konstanty a pole  
  
## <a name="working-with-the-object-data-type"></a>Práce s datovým typem objektu  
 Můžete přiřadit buď odkazový typ, nebo typ hodnoty na proměnnou datového typu `Object`. Proměnná `Object` vždy obsahuje odkaz na data, nikdy samotná data. Pokud však k proměnné `Object` přiřadíte typ hodnoty, bude se chovat, jako by obsahuje vlastní data. Další informace najdete v tématu [datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Můžete zjistit, zda `Object` proměnná funguje jako typ odkazu nebo typ hodnoty předáním do metody <xref:Microsoft.VisualBasic.Information.IsReference%2A> ve třídě <xref:Microsoft.VisualBasic.Information> oboru názvů <xref:Microsoft.VisualBasic?displayProperty=nameWithType>. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> vrátí `True`, pokud obsah `Object` proměnné představuje typ odkazu.  
  
## <a name="see-also"></a>Viz také:

- [Typy hodnot s povolenou hodnotou Null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Účinné používání datových typů](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
