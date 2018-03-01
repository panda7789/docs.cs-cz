---
title: "Použití indexerů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5c727edbbea116d858c6acf6b600f8fd9f43ee2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-indexers-c-programming-guide"></a>Použití indexerů (Průvodce programováním v C#)
Indexery jsou syntaktické pohodlí, které vám umožní vytvořit [třída](../../../csharp/language-reference/keywords/class.md), [struktura](../../../csharp/language-reference/keywords/struct.md), nebo [rozhraní](../../../csharp/language-reference/keywords/interface.md) , klient aplikace mají přístup k stejně jako pole. Indexery se nejčastěji implementují typy, jejichž primární účelem je zapouzdření k interní kolekce nebo pole. Předpokládejme například, že máte třídy s názvem TempRecord, který reprezentuje teplotní v Farenheit zjištěná v různých časech 10 během období 24 hodin. Třída obsahuje pole s názvem "temps" z typ float představují teploty a <xref:System.DateTime> představující datum teploty nebyly zaznamenány. Implementací indexer v této třídě, mohou klienti získat přístup teploty v instanci TempRecord jako `float temp = tr[4]` místo jako `float temp = tr.temps[4]`. Zápis indexer nejen zjednodušuje syntaxi pro klientské aplikace; také umožňuje třídě a jeho účel intuitivnější pro ostatní vývojáři pochopit.  
  
 Chcete-li na třídě nebo struktuře deklarovat indexer, použijte [to](../../../csharp/language-reference/keywords/this.md) – klíčové slovo, jako v následujícím příkladu:  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 Typ indexer a typ jeho parametry musí být dostupné jako indexeru sám sebe. Další informace o úrovní přístupu najdete v tématu [modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Další informace o tom, jak používat indexery s rozhraním najdete v tématu [rozhraní indexery](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).  
  
 Podpis indexer se skládá z počtu a typů jeho formální parametry. Nebude obsahovat typ indexer nebo názvy formální parametrů. Pokud je deklarovat více než jeden indexer ve stejné třídě, musí mít různé podpisy.  
  
 Hodnotu indexer není klasifikovaný jako proměnné. Proto nemůžete předat hodnotu indexer jako [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out.md) parametr.  
  
 Indexer poskytnout název, který můžete použít další jazyky, používat `name` atribut v deklaraci. Příklad:  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 Indexer bude mít název `TheItem`. Neposkytuje atribut názvu by zkontrolujte `Item` výchozí název.  
  
## <a name="example-1"></a>Příklad 1  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje, jak deklarovat privátní pole pole, `temps`a indexer. Indexer umožňuje přímý přístup k instanci `tempRecord[i]`. Deklarace pole jako alternativu k použití indexeru je [veřejné](../../../csharp/language-reference/keywords/public.md) člen a přístup k jeho členy `tempRecord.temps[i]`, přímo.  
  
 Všimněte si, že při přístupu indexeru je hodnocení, například v `Console.Write` příkaz, [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu je volána. Proto pokud žádné `get` přistupující objekt existuje, dojde k chybě kompilace.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a>Indexování pomocí jiných hodnot  
 C# neomezuje typ indexu na celé číslo. Například může být užitečné pro použití s indexer řetězec. Takové indexer může být implementována hledání řetězce v kolekci a návrat na odpovídající hodnotu. Jako přístupové objekty mohou být přetíženy, může existovat společně řetězec a celé číslo verze.  
  
## <a name="example-2"></a>Příklad 2  
  
### <a name="description"></a>Popis  
 V tomto příkladu je deklarován třídu, která ukládá dny v týdnu. A `get` je deklarovaný přistupujícího objektu, který přebírá řetězec, název dne a vrátí odpovídající celé číslo. Například neděle bude vrátit 0, pondělí budou vracet 1 a tak dále.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Existují dva hlavní způsoby, ve kterých je možné zlepšit zabezpečení a spolehlivost indexery:  
  
-   Ujistěte se, že začlenit nějaký typ strategie zpracování chyb pro zpracování riziko předávání v hodnotou neplatný index kódu klienta. V prvním příkladu výše v tomto tématu poskytuje třídu TempRecord délka vlastnosti, která umožňuje kód klienta ověření vstupu před jeho odesláním indexeru. Můžete také vložit kód uvnitř samotného indexeru pro zpracování chyb. Ujistěte se, že dokumentů pro uživatele jakékoli výjimky, které vyvolají uvnitř přistupující objekt indexer.  
  
-   Nastavit usnadnění přístupu `get` a [nastavit](../../../csharp/language-reference/keywords/set.md) přístupových objektů na omezující, jako je možné logicky. To je důležité pro `set` přistupujícího objektu v konkrétní. Další informace najdete v tématu [omezení přístupnosti přistupujícího objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Indexery](../../../csharp/programming-guide/indexers/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
