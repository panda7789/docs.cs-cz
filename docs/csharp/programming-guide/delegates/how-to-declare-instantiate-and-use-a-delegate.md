---
title: 'Postupy: Deklarace, vytvoření instance a použití průvodce C# programováním delegátů'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 565ae2a6c42de57570f564edc9d0bde5cab8efa8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590625"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Postupy: Deklarace, vytvoření instance a použití delegáta (C# Průvodce programováním)
V C# 1,0 a novějších, mohou být Delegáti deklarováni, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 C#2,0 poskytuje jednodušší způsob, jak napsat předchozí deklaraci, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 V C# 2,0 a novějších je také možné použít anonymní metodu k deklaraci a inicializaci delegáta, [](../../language-reference/keywords/delegate.md)jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 V C# 3,0 a novějších, mohou být Delegáti také deklarováni a vytvořeny pomocí výrazu lambda, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 Další informace naleznete v tématu [lambda výrazy](../statements-expressions-operators/lambda-expressions.md).  
  
 Následující příklad znázorňuje deklarování, vytváření instancí a použití delegáta. `BookDB` Třída zapouzdřuje databázi Bookstore, která udržuje databázi knih. Zpřístupňuje metodu, `ProcessPaperbackBooks`která najde všechny tištěné verze knihy v databázi a zavolá delegáta pro každý z nich. Typ, který se používá, se `ProcessBookDelegate`nazývá. `delegate` `Test` Třída používá tuto třídu k tisku názvů a průměrné ceny tištěné verze knih.  
  
 Použití delegátů podporuje dobré oddělení funkcí mezi databází Bookstore a klientským kódem. Kód klienta nemá žádné znalosti o tom, jak jsou knihy uložené, nebo jak kód Bookstore najde tištěné verze knihy. Kód Bookstore nemá žádné znalosti o tom, jaké zpracování se provádí na tištěné verzech knihách, jakmile je najde.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
- Deklarace delegáta.  
  
     Následující příkaz deklaruje nový typ delegáta.  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     Každý typ delegáta popisuje počet a typy argumentů a typ návratové hodnoty metod, které mohou být zapouzdřeny. Pokaždé, když je potřeba nová sada typů argumentů nebo návratový typ hodnoty, musí být deklarovaný nový typ delegáta.  
  
- Vytvoření instance delegáta.  
  
     Po deklarování typu delegáta musí být objekt delegáta vytvořen a přidružen k určité metodě. V předchozím příkladu je třeba předat `PrintTitle` metodu `ProcessPaperbackBooks` metodě jako v následujícím příkladu:  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     Tím se vytvoří nový objekt delegáta přidružený ke [statické](../../language-reference/keywords/static.md) metodě `Test.PrintTitle`. Podobně není statická metoda `AddBookToTotal` objektu `totaller` předána jako v následujícím příkladu:  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     V obou případech je `ProcessPaperbackBooks` metodě předán nový objekt delegát.  
  
     Po vytvoření delegáta metoda je přidružena bez jakýchkoli změn; objekty delegáta jsou neměnné.  
  
- Volání delegáta.  
  
     Po vytvoření objektu delegáta je objekt delegát obvykle předán jinému kódu, který bude volat delegáta. Objekt delegáta je volán pomocí názvu objektu delegáta následovaný argumenty v závorkách, které mají být předány delegátovi. Následuje příklad volání delegáta:  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     Delegát může být buď volán synchronně, jako v tomto příkladu, nebo asynchronně pomocí `BeginInvoke` metod a. `EndInvoke`  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Události](../events/index.md)
- [Delegáti](./index.md)
