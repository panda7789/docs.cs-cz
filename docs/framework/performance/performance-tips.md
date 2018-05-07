---
title: Tipy pro zvýšení výkonu rozhraní .NET
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 728bac6985d47afdb4263f8c41a9d282dd2574b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="net-performance-tips"></a>Tipy pro zvýšení výkonu rozhraní .NET
Termín *výkonu* obvykle odkazuje na rychlost zpracování programu. Rychlost provádění někdy zvýšíte následující některých základních pravidel ve zdrojovém kódu. V některých aplikacích je důležité, abyste pečlivě zkontrolujte kód a použít profilery a ujistěte se, zda je spuštěna co nejrychleji. V jiných programů nemáte provést tyto optimalizace, protože je kód spuštěn přijatelně rychlé, jako je zapsán. V tomto článku jsou uvedené některé běžné oblasti, kde můžete sníží výkon a tipy pro zlepšení ho a také odkazy na témata další výkonu. Další informace o plánování a měření výkonu najdete v tématu [výkonu](../../../docs/framework/performance/index.md)  
  
## <a name="boxing-and-unboxing"></a>Zabalení a rozbalení  
 Doporučujeme nepoužívat hodnotu typy v situacích, kde musí být do pole velký počet dobu, například v třídy neobecnou kolekcí, jako <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Zabalení typů hodnot se můžete vyhnout pomocí obecné kolekce <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Zabalení a rozbalení jsou náročné procesy. Když je do pole zadejte hodnotu, musí být vytvořený zcela nový objekt. Může to trvat až 20 x delší než jednoduchý odkaz přiřazení. Po rozbalení, může proces přetypování trvat čtyřikrát stejně dlouho jako přiřazení. Další informace najdete v tématu [zabalení a rozbalení](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Řetězce  
 Když jste řetězení velký počet proměnných řetězce, například ve smyčce úzkou použít <xref:System.Text.StringBuilder?displayProperty=nameWithType> místo jazyka C# [+ – operátor](~/docs/csharp/language-reference/operators/addition-operator.md) nebo Visual Basic [operátory zřetězení](~/docs/visual-basic/language-reference/operators/concatenation-operators.md). Další informace najdete v tématu [postupy: řetězení více řetězců](../../csharp/how-to/concatenate-multiple-strings.md) a [operátory řetězení v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Destruktory  
 Nepoužívejte prázdné destruktory. Pokud třída obsahuje destruktor, bude vytvořena položka ve frontě Finalize. Při volání destruktoru, volá se ke zpracování fronty uvolňování paměti. Pokud destruktoru je prázdná, to jednoduše vede ke ztrátě výkonu. Další informace najdete v tématu [destruktory](~/docs/csharp/programming-guide/classes-and-structs/destructors.md) a [doba života objektu: jak jsou objekty vytvořen a Destroyed](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Další zdroje  
  
-   [Spravovaný kód a rychlejší psaní: Vědět, co věcí náklady](http://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [Zápis vysoce výkonné aplikace spravovaného: Základy](http://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [Základní informace o systém uvolňování paměti a výkon pomocné parametry](http://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [Tipy pro zvýšení výkonu a triky v aplikacích .NET](http://go.microsoft.com/fwlink/?LinkId=99297)  

-   [Tidbits Portoriku Mariani výkonu](http://go.microsoft.com/fwlink/?LinkId=115679)  

-   [Blog hovou Morrison](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>Viz také  
 [Výkon](../../../docs/framework/performance/index.md)  
 [Koncepty programování](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6)  
 [Průvodce programováním v jazyce Visual Basic](../../visual-basic/programming-guide/index.md)  
 [Průvodce programováním v jazyce C#](http://msdn.microsoft.com/library/ac0f23a2-6bf3-4077-be99-538ae5fd3bc5)
