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
ms.openlocfilehash: 4e0831a045da5eb5798d10aeb977981ecae20040
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61869664"
---
# <a name="value-types-and-reference-types"></a>Typy hodnot a typy odkazu
Datové typy v jazyce Visual Basic jsou implementovány podle jejich klasifikace. Datové typy jazyka Visual Basic lze rozdělit podle Určuje, zda proměnná určitého typu ukládá svoje vlastní data nebo ukazatel na data. Pokud ukládá svoje vlastní data *typ hodnoty*; pokud drží ukazatel na data jinde v paměti je *odkazovat na typ*.  
  
## <a name="value-types"></a>Typy hodnot  
 Datový typ je *typ hodnoty* pokud obsahuje data v rámci své vlastní přidělení paměti. Typy hodnot patří:  
  
- Všechny číselné datové typy  
  
- `Boolean`, `Char`, a `Date`  
  
- Všechny struktury, i když jejich členové jsou odkazové typy  
  
- Výčty, protože jeho základní typ je vždy `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, nebo `ULong`  
  
 Každý struktura je typ hodnoty, i v případě, že obsahuje členy typu odkazu. Z tohoto důvodu hodnotové typy, jako `Char` a `Integer` implementují struktury rozhraní .NET Framework.  
  
 Typ hodnoty je možné deklarovat pomocí vyhrazené slovo, například `Decimal`. Můžete také použít `New` – klíčové slovo k inicializaci typu hodnoty. To je obzvláště užitečné, pokud typ má konstruktor, který používá parametry. Příkladem je <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktor, který vytvoří nový `Decimal` hodnotu ze zadaného částí.  
  
## <a name="reference-types"></a>Typy odkazů  
 A *odkazovat na typ* obsahuje ukazatel do jiného umístění v paměti, která obsahuje data. Odkazové typy zahrnují následující:  
  
- `String`  
  
- Všechna pole, i když jsou jejich prvky typy hodnot  
  
- Typy, jako například tříd <xref:System.Windows.Forms.Form>  
  
- Delegáty  
  
 Třída je *odkazovat na typ*. Z tohoto důvodu referenční typy `Object` a `String` podporují [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy. Upozorňujeme, že každé pole typu odkazu, i v případě, že její členy jsou typy hodnot.  
  
 Protože každý odkaz na typ představuje základní třídy rozhraní .NET Framework, je nutné použít [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo je inicializovat. Následující příkaz inicializuje pole.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Prvky, které nejsou typy  
 Následující programovací prvky nekvalifikujte jako typy, protože některý z nich nelze zadat pro element deklarovaný typ dat:  
  
- Jmenné prostory  
  
- Moduly  
  
- Události  
  
- Vlastnosti a postupy  
  
- Proměnné, konstanty a pole  
  
## <a name="working-with-the-object-data-type"></a>Práce s datovým typem objektu  
 Proměnné můžete přiřadit odkazový typ nebo hodnotový typ `Object` datového typu. `Object` Proměnnou vždy obsahuje ukazatel na data, nikdy vlastní data. Nicméně pokud přiřadíte typ hodnoty do `Object` proměnné, se chová jako obsahuje vlastní data. Další informace najdete v tématu [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Můžete zjistit, jestli se `Object` proměnné funguje jako odkaz na typ nebo hodnotový typ ji do <xref:Microsoft.VisualBasic.Information.IsReference%2A> metoda ve <xref:Microsoft.VisualBasic.Information> třídu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Vrátí `True` Pokud obsah `Object` proměnná představuje typ odkazu.  
  
## <a name="see-also"></a>Viz také:

- [Typy hodnot s povolenou hodnotou Null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Účinné používání datových typů](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
