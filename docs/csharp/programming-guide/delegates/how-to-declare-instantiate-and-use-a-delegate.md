---
title: 'Postupy: Deklarování, vytváření instancí a použití delegáta (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 19e5883135d65a648bb6afb74a475b761f572a95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333970"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Postupy: Deklarování, vytváření instancí a použití delegáta (Průvodce programováním v C#)
V jazyce C# 1.0 nebo novější lze deklarovat delegáti, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 C# 2.0 poskytuje jednodušší způsob, jak zapsat předchozí deklaraci, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 V C# 2.0 nebo novější, je také možné použít anonymní metody deklarace a inicializace [delegovat](../../../csharp/language-reference/keywords/delegate.md), jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 V jazyce C# 3.0 nebo novější můžete delegáti také deklarovaný a vytvoření instance pomocí výrazu lambda, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Následující příklad ilustruje deklarování, vytváření instancí a použití delegáta. `BookDB` Třída zapouzdří knihkupectví databázi, která udržuje databázi knih. Poskytuje metody, `ProcessPaperbackBooks`, který vyhledá všechny paperback zarezervuje v databázi a volání delegáta pro každé z nich. `delegate` Typ, který se používá jmenuje `ProcessBookDelegate`. `Test` Třída používá tato třída tisknout názvy a průměrná cena formátu brožované knih.  
  
 Použití delegátů zvýší úroveň dobré oddělení funkcí mezi databázi pro knihkupectví a kódu klienta. Kód klienta nemá žádné informace o tom, jak jsou uložené webu knihy nebo jak kód pro knihkupectví vyhledá formátu brožované knihy. Kód pro knihkupectví nemá žádné informace o jaké zpracování provádí na formátu brožované knihy po nich najde.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
-   Deklarování delegáta.  
  
     Následující příkaz deklaruje nový typ delegáta.  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     Každý typ delegáta popisuje počet a typy argumentů a typ návratová hodnota metody, které může zapouzdřit. Vždy, když je potřeba novou sadu typy argumentů nebo typ návratové hodnoty, musí být deklarován nový typ delegáta.  
  
-   Vytváření instancí delegáta.  
  
     Poté, co byla deklarována typem delegáta, musí být objekt delegáta vytvořena a přidružena konkrétní metody. V předchozím příkladu, Uděláte to pomocí předání `PrintTitle` metodu `ProcessPaperbackBooks` metoda jako v následujícím příkladu:  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     Tím se vytvoří nový objekt delegáta přidružené [statické](../../../csharp/language-reference/keywords/static.md) metoda `Test.PrintTitle`. Podobně metoda nestatické `AddBookToTotal` u objektu `totaller` je předána jako v následujícím příkladu:  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     V obou případech je předán nový objekt delegáta `ProcessPaperbackBooks` metoda.  
  
     Po vytvoření delegáta metodu je spojena se nikdy změny; Delegát objekty jsou neměnné.  
  
-   Volání metody delegáta.  
  
     Po vytvoření objektu delegáta objekt delegáta obvykle předaný jiný kód, který bude volat delegát. Objekt delegáta nazývá pomocí názvu objektu delegáta, za nímž následuje argumenty v závorce mají být předány delegát. Tady je příklad delegáta volání:  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     Delegát může být buď volána synchronně, jako v následujícím příkladu, nebo asynchronně pomocí `BeginInvoke` a `EndInvoke` metody.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)
