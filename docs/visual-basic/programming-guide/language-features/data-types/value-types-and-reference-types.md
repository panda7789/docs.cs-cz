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
ms.openlocfilehash: 9456316f71a213905bcb50336533c4e618f5174a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651580"
---
# <a name="value-types-and-reference-types"></a>Typy hodnot a typy odkazu
V jazyce Visual Basic – datové typy jsou implementované podle jejich klasifikace. Datové typy jazyka Visual Basic můžou být klasifikované podle jestli proměnné určitého typu ukládá svá vlastní data nebo odkazy na data. Pokud ukládají svá vlastní data *typ hodnoty*; Pokud má ukazatel na data jinde v paměti je *odkazují na typ*.  
  
## <a name="value-types"></a>Typy hodnot  
 Datový typ *typ hodnoty* pokud drží dat v rámci vlastní přidělení paměti. Typy hodnot zahrnují následující:  
  
-   Všechny číselné datové typy  
  
-   `Boolean`, `Char`, a `Date`  
  
-   Všechny struktury, i když jsou jejich členové odkazové typy  
  
-   Výčty, protože jejich základní typ je vždy `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, nebo `ULong`  
  
 Každý struktura je hodnota typu, i v případě, že obsahuje členy typu odkaz. Z tohoto důvodu, hodnotu, jako typy `Char` a `Integer` jsou implementované struktury rozhraní .NET Framework.  
  
 Typ hodnoty můžou deklarovat pomocí vyhrazené slovo, například `Decimal`. Můžete také `New` – klíčové slovo k chybě při inicializaci typu hodnoty. To je obzvláště užitečné, pokud má tento typ konstruktor, který používá parametry. Příkladem je <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktor, který vytvoří nový `Decimal` hodnotu z části zadaný.  
  
## <a name="reference-types"></a>Typy odkazů  
 A *odkazují na typ* obsahuje ukazatel do jiného umístění paměti, která obsahuje data. Odkazové typy patří:  
  
-   `String`  
  
-   Všechna pole, i když jejich prvky jsou typy hodnot  
  
-   Typy tříd, jako například <xref:System.Windows.Forms.Form>  
  
-   Delegáty  
  
 Třída je *odkazují na typ*. Z tohoto důvodu odkazové typy `Object` a `String` podporuje [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy. Všimněte si, že každé pole je typu odkazu. i v případě jeho členové jsou typy hodnot.  
  
 Vzhledem k tomu, že každý typ odkazu představuje základní třídu rozhraní .NET Framework, je nutné použít [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo provést jeho inicializaci. Následující příkaz inicializuje pole.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Elementy, které nejsou typy  
 Následující elementům programování nemohou být jako typy, protože některý z nich nelze zadat jako datový typ pro element deklarované:  
  
-   Jmenné prostory  
  
-   Moduly  
  
-   Události  
  
-   Vlastnosti a postupy  
  
-   Pole, konstanty a proměnné  
  
## <a name="working-with-the-object-data-type"></a>Práce s datovým typem objektu  
 Proměnné můžete přiřadit odkazového typu nebo typ hodnoty `Object` datového typu. `Object` Proměnné vždy obsahuje ukazatel k datům, nikdy samotná data. Ale pokud přiřadíte typ hodnoty do `Object` proměnné, chová jako kdyby drží svá vlastní data. Další informace najdete v tématu [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Můžete zjistit, jestli se `Object` proměnná funguje jako odkaz na typ nebo typ hodnoty předáním jeho <xref:Microsoft.VisualBasic.Information.IsReference%2A> metoda v <xref:Microsoft.VisualBasic.Information> třídu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Vrátí `True` Pokud obsah `Object` proměnná představuje odkazového typu.  
  
## <a name="see-also"></a>Viz také  
 [Typy hodnot s povolenou hodnotou Null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Účinné používání datových typů](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
