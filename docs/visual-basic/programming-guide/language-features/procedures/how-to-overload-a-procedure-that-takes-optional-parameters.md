---
title: 'Postupy: Přetížení procedury, která přebírá volitelné parametry (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 58c52a7d73efbd96d772dd85d6bf2c9084fb1241
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320223"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Postupy: Přetížení procedury, která přebírá volitelné parametry (Visual Basic)
Pokud procedura má jeden nebo více [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) parametry, nelze definovat přetížený verzi, která odpovídá některé z jeho implicitní přetížení. Další informace najdete v tématu "Implicitní přetížení pro volitelné parametry" [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Jeden volitelný parametr  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Přetížení procedury, která přijímá jeden volitelný parametr  
  
1. Zápis `Sub` nebo `Function` příkazu deklarace, která obsahuje volitelný parametr v seznamu parametrů. Nepoužívejte `Optional` – klíčové slovo v této verzi přetížená.  
  
2. Předcházet `Sub` nebo `Function` – klíčové slovo se [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.  
  
3. Napište kód postup, který by se měl spustit, když volající kód poskytuje nepovinný argument.  
  
4. Ukončí proceduru s `End Sub` nebo `End Function` příkaz podle potřeby.  
  
5. Zápis druhého příkazu deklarace, která je stejná jako první deklarace s tím rozdílem, že neobsahuje volitelný parametr v seznamu parametrů.  
  
6. Napište kód postup, který by se měl spustit, když volající kód neposkytuje nepovinný argument. Ukončí proceduru s `End Sub` nebo `End Function` příkaz podle potřeby.  
  
     Následující příklad ukazuje definované s volitelným parametrem, ekvivalentní sadu dvě přetížení procedury a nakonec příkladem neplatné a platný přetížené verze procedury.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Více volitelné parametry  
 Pro proceduru s více než jeden volitelný parametr musíte obvykle více než dvě přetížené verze. Například pokud existují dva volitelné parametry a volající kód můžete zadat nebo vynechat, nechte každé z nich nezávisle na druhém, je třeba čtyři přetížené verze, jeden pro jednotlivých možných kombinací zadaným argumentům.  
  
 Jak se zvyšuje počet volitelné parametry, zvyšuje složitost přetížení. Není-li některá kombinace zadané argumenty nejsou přípustné, nepovinných parametrů. N potřebujete 2 ^ N přetížené verze. V závislosti na povaze postup můžete zjistit, že srozumitelnost logiky odůvodňuje další úsilí definice přetížené verze.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Přetížení procedury, která má více než jeden volitelný parametr  
  
1. Určete, jaké kombinace zadaná volitelné argumenty jsou přijatelné logiku podle postupu. Nepřijatelné kombinaci může nastat, pokud jeden volitelný parametr, závisí na jiném. Například pokud jeden parametr přijímá název manželem a jiné přijímá stáří partnera, kombinace argumentů poskytnutí stáří, ale bez názvu nepřijatelné.  
  
2. Pro každý přijatelné kombinace zadaná volitelné argumenty zapisovat `Sub` nebo `Function` příkazu deklarace, která definuje odpovídající seznamu parametrů. Nepoužívejte `Optional` – klíčové slovo.  
  
3. V deklaraci, předcházet `Sub` nebo `Function` – klíčové slovo se [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.  
  
4. Po deklaraci psát kód postup, který by se měl spustit, když volající kód poskytuje seznam argumentů odpovídající této deklarace seznamu parametrů.  
  
5. Ukončit každý postup s `End Sub` nebo `End Function` příkaz podle potřeby.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Nepovinné parametry](./optional-parameters.md)
- [Pole parametrů](./parameter-arrays.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Řešení přetížení](./overload-resolution.md)
