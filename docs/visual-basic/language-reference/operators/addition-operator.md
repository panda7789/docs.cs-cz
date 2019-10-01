---
title: + – Operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 3187551afb7d25470f48dad894188766a811bb0a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701002"
---
# <a name="-operator-visual-basic"></a>+ – operátor (Visual Basic)
Přidá dvě čísla nebo vrátí kladnou hodnotu číselného výrazu. Lze také použít ke zřetězení dvou řetězcových výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
expression1 + expression2
```
  
or

```vb  
+expression1  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression1`|Požadováno. Libovolný numerický nebo řetězcový výraz.|  
|`expression2`|Povinné, pokud operátor `+` nepočítá zápornou hodnotu. Libovolný numerický nebo řetězcový výraz.|  
  
## <a name="result"></a>Výsledek  
 Pokud `expression1` a `expression2` jsou číselné, výsledkem je aritmetický součet.  
  
 Pokud chybí `expression2`, operátor `+` je *unárním* operátorem identity pro nezměněnou hodnotu výrazu. V tomto smyslu se operace skládá z uchování znaménka `expression1`, takže výsledek je negativní, pokud je `expression1` záporný.  
  
 Pokud `expression1` a `expression2` jsou oba řetězce, je výsledkem zřetězení jejich hodnot.  
  
 Pokud `expression1` a `expression2` jsou smíšené typy, akce provedena závisí na jejich typech, jejich obsahu a nastavení [příkazu Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). Další informace najdete v tabulkách v části "poznámky".  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal` a `String`.  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí, `+` provede aritmetické přidávání, pokud je to možné, a zřetězí se pouze v případě, že jsou oba výrazy řetězce.  
  
 Pokud žádný výraz není `Object`, Visual Basic provede následující akce.  
  
|Datové typy výrazů|Akce podle kompilátoru|  
|---|---|  
|Oba výrazy jsou číselné datové typy (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single` nebo 0).|Přidávání. Výsledný datový typ je číselný typ, který je vhodný pro datové typy `expression1` a `expression2`. Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba výrazy jsou typu `String`.|Zřetězit.|  
|Jeden výraz je číselný datový typ a druhý je řetězec.|Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.<br /><br /> Pokud je `Option Strict` `Off`, implicitně převeďte `String` na `Double` a přidejte.<br /><br /> Pokud `String` nelze převést na `Double`, vyvolejte výjimku <xref:System.InvalidCastException>.|  
|Jeden výraz je numerický datový typ a druhý není [nic](../../../visual-basic/language-reference/nothing.md)|Přidejte s @no__t hodnotou 0, která se vyhodnotí jako nula.|  
|Jeden výraz je řetězec a druhý je `Nothing`|Zřetězte s @no__t hodnotou 0, která se vyhodnotí jako "".|  
  
 Pokud je jeden výraz výraz `Object`, Visual Basic provede následující akce.  
  
|Datové typy výrazů|Akce podle kompilátoru|  
|---|---|  
|výraz `Object` obsahuje číselnou hodnotu a druhý je číselný datový typ.|Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.<br /><br /> Pokud je `Option Strict` `Off`, pak přidejte.|  
|výraz `Object` obsahuje číselnou hodnotu a druhá je typu `String`.|Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.<br /><br /> Pokud je `Option Strict` `Off`, implicitně převeďte `String` na `Double` a přidejte.<br /><br /> Pokud `String` nelze převést na `Double`, vyvolejte výjimku <xref:System.InvalidCastException>.|  
|výraz `Object` obsahuje řetězec a druhý je číselný datový typ.|Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.<br /><br /> Pokud je `Option Strict` `Off`, implicitně převeďte řetězec `Object` na `Double` a přidejte.<br /><br /> Pokud řetězec `Object` nelze převést na `Double`, vyvolejte výjimku <xref:System.InvalidCastException>.|  
|výraz `Object` obsahuje řetězec a druhý je typu `String`.|Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.<br /><br /> Pokud je `Option Strict` `Off`, implicitně převede `Object` na `String` a zřetězení.|  
  
 Pokud jsou oba výrazy @no__t výrazy-0, Visual Basic provede následující akce (pouze `Option Strict Off`).  
  
|Datové typy výrazů|Akce podle kompilátoru|  
|---|---|  
|Oba výrazy `Object` uchovávají číselné hodnoty.|Přidávání.|  
|Výrazy `Object` jsou typu `String`.|Zřetězit.|  
|Jeden výraz `Object` obsahuje číselnou hodnotu a druhý obsahuje řetězec.|Implicitně převeďte řetězec `Object` na `Double` a přidat.<br /><br /> Pokud řetězec `Object` nelze převést na číselnou hodnotu, vyvolejte výjimku <xref:System.InvalidCastException>.|  
  
 Pokud je výraz `Object` vyhodnocen jako [Nothing](../../../visual-basic/language-reference/nothing.md) nebo <xref:System.DBNull>, operátor `+` ho považuje za `String` s hodnotou "".  
  
> [!NOTE]
> Pokud použijete operátor `+`, možná nebudete moci určit, zda dojde k přidání nebo zřetězení řetězců. Pomocí operátoru `&` pro zřetězení Eliminujte nejednoznačnosti a poskytněte kód pro samoobslužný dokument.  
  
## <a name="overloading"></a>Přetížení  
 Operátor `+` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `+` pro přidání čísel. Pokud jsou operandy číselné, Visual Basic vypočítá aritmetický výsledek. Aritmetický výsledek představuje součet dvou operandů.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 K zřetězení řetězců můžete použít také operátor `+`. Pokud jsou operandy řetězcem, Visual Basic je zřetězí. Výsledek zřetězení představuje jeden řetězec skládající se z obsahu dvou operandů jednoho po druhém.  
  
 Pokud jsou operandy smíšeného typu, výsledek závisí na nastavení [příkazu Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). Následující příklad ilustruje výsledek, pokud je `Option Strict` `On`.  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Následující příklad ilustruje výsledek, pokud je `Option Strict` `Off`.  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Chcete-li odstranit nejednoznačnost, měli byste použít operátor `&` namísto `+` pro zřetězení.  
  
## <a name="see-also"></a>Viz také:

- [Operátor &](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Operátory řetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
