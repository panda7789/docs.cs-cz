---
title: Jak deklarovat, vytvořit instanci a použít průvodce programováním v jazyce Delegate – Programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 7ac1d736e19c4dcf1c8408db944505c399762778
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712361"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Jak deklarovat, konkretizovat a používat delegate (C# Programovací příručka)
V jazyce C# 1.0 a novější delegáti mohou být deklarovány, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 C# 2.0 poskytuje jednodušší způsob, jak napsat předchozí deklarace, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 V C# 2.0 a novější je také možné použít anonymní metodu k deklarování a inicializaci [delegáta](../../language-reference/builtin-types/reference-types.md), jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 V jazyce C# 3.0 a novější delegáti mohou být také deklarovány a vytvořena instance pomocí výrazu lambda, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 Další informace naleznete v tématu [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).  
  
 Následující příklad ukazuje deklarování, vytváření instancí a použití delegáta. Třída `BookDB` zapouzdřuje databázi knihkupectví, která udržuje databázi knih. Zpřístupní metodu `ProcessPaperbackBooks`, která vyhledá všechny brožované knihy v databázi a zavolá delegáta pro každou z nich. Použitý `delegate` typ je pojmenován `ProcessBookDelegate`. Třída `Test` používá tuto třídu k tisku názvů a průměrné ceny brožknih.  
  
 Použití delegátů podporuje dobré oddělení funkcí mezi databází knihkupectví a klientským kódem. Klientský kód nemá žádné znalosti o tom, jak jsou knihy uloženy nebo jak kód knihkupectví najde brožované knihy. Kód knihkupectví nemá žádné znalosti o tom, jaké zpracování se provádí na brožované knihy poté, co je najde.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
- Deklarování delegáta.  
  
     Následující příkaz deklaruje nový typ delegáta.  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     Každý typ delegáta popisuje počet a typy argumentů a typ vrácené hodnoty metod, které může zapouzdřit. Kdykoli je potřeba nová sada typů argumentů nebo typ vrácené hodnoty, musí být deklarován nový typ delegáta.  
  
- Vytvoření instance delegáta.  
  
     Po deklarování typu delegáta musí být objekt delegáta vytvořen a přidružen k určité metodě. V předchozím příkladu to provést `PrintTitle` předáním `ProcessPaperbackBooks` metody metodě jako v následujícím příkladu:  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     Tím se vytvoří nový objekt delegáta přidružený ke [statické](../../language-reference/keywords/static.md) metodě `Test.PrintTitle`. Podobně je nestatická `AddBookToTotal` metoda objektu `totaller` předána jako v následujícím příkladu:  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     V obou případech je metodě `ProcessPaperbackBooks` předán nový objekt delegáta.  
  
     Po vytvoření delegáta se metoda, ke které je přidružen, nikdy nezmění; delegovat objekty jsou neměnné.  
  
- Volání delegáta.  
  
     Po vytvoření objektu delegáta je objekt delegáta obvykle předán jinému kódu, který bude delegáta volat. Objekt delegáta je volán pomocí názvu objektu delegáta následovaným argumenty v závorce, které mají být předány delegátovi. Následuje příklad volání delegáta:  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     Delegát může být volána synchronně, jako v tomto příkladu, nebo `BeginInvoke` `EndInvoke` asynchronně pomocí a metody.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Akce](../events/index.md)
- [Delegáty](./index.md)
