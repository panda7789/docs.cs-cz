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
ms.openlocfilehash: 3a1de120f5f97ba93939f332f121d70cd3091216
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392971"
---
# <a name="value-types-and-reference-types"></a>Typy hodnot a typy odkazu
Existují dva druhy typů v Visual Basic: typy odkazu a typy hodnot. Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data. V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou. S typy hodnot každá proměnná má svou vlastní kopii dat a není možné, aby operace s jednou proměnnou ovlivnily jiný (kromě případu, kdy [Modifikátor ByRef u parametrů](../../../language-reference/modifiers/byref.md)).
  
## <a name="value-types"></a>Typy hodnot  
 Datový typ je *typ hodnoty* , pokud obsahuje data v rámci své vlastní alokace paměti. Typy hodnot zahrnují následující:  
  
- Všechny číselné datové typy  
  
- `Boolean`, `Char` a`Date`  
  
- Všechny struktury, i když jejich členové jsou odkazové typy  
  
- Výčty, protože jejich nadřízený typ je vždy `SByte` , `Short` , `Integer` , `Long` , `Byte` , `UShort` , `UInteger` nebo`ULong`  
  
 Každá struktura je typ hodnoty, a to i v případě, že obsahuje členy typu odkazu. Z tohoto důvodu jsou typy hodnot jako `Char` a `Integer` implementovány .NET Framework struktury.  
  
 Typ hodnoty lze deklarovat pomocí klíčového slova rezervované, například `Decimal` . Můžete také použít `New` klíčové slovo k inicializaci typu hodnoty. To je užitečné hlavně v případě, že typ má konstruktor, který přebírá parametry. Příkladem je <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktor, který vytváří novou `Decimal` hodnotu ze zadaných částí.  
  
## <a name="reference-types"></a>Typy odkazů  
 *Odkazový typ* ukládá odkaz na jeho data. Typy odkazů zahrnují následující:  
  
- `String`  
  
- Všechna pole, i když jejich prvky jsou typy hodnot  
  
- Typy tříd, jako např.<xref:System.Windows.Forms.Form>  
  
- Delegáti  
  
 Třída je *odkazový typ*. Všimněte si, že každé pole je typ odkazu, a to i v případě, že jeho členy jsou typy hodnot.  
  
 Vzhledem k tomu, že každý typ odkazu představuje základní třídu .NET Framework, je nutné při inicializaci použít klíčové slovo [New operátor](../../../language-reference/operators/new-operator.md) . Následující příkaz inicializuje pole.  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Prvky, které nejsou typy  
 Následující programovací prvky neopravňují jako typy, protože nemůžete zadat žádné z nich jako datový typ pro deklarovaný element:  
  
- Obory názvů  
  
- Moduly  
  
- Události  
  
- Vlastnosti a procedury  
  
- Proměnné, konstanty a pole  
  
## <a name="working-with-the-object-data-type"></a>Práce s datovým typem objektu  
 Proměnné datového typu můžete přiřadit buď odkazový typ, nebo typ hodnoty `Object` . `Object`Proměnná vždy obsahuje odkaz na data, ale samotná data. Pokud však přiřadíte typ hodnoty `Object` proměnné, bude se chovat jako, pokud obsahuje vlastní data. Další informace najdete v tématu [datový typ Object](../../../language-reference/data-types/object-data-type.md).  
  
 Můžete zjistit, zda proměnná funguje `Object` jako typ odkazu nebo typ hodnoty předáním do <xref:Microsoft.VisualBasic.Information.IsReference%2A> metody ve <xref:Microsoft.VisualBasic.Information> třídě <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>Vrátí, `True` zda obsah `Object` proměnné představuje typ odkazu.  
  
## <a name="see-also"></a>Viz také

- [Typy hodnot s možnou hodnotou null](nullable-value-types.md)
- [Převody typů v jazyce Visual Basic](type-conversions.md)
- [Structure – příkaz](../../../language-reference/statements/structure-statement.md)
- [Účinné používání datových typů](efficient-use-of-data-types.md)
- [Datový typ objektu](../../../language-reference/data-types/object-data-type.md)
- [Datové typy](index.md)
