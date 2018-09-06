---
title: Použití indexerů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 3e4c1f346b83cf97c57a359984bd08e075b6451b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43738896"
---
# <a name="using-indexers-c-programming-guide"></a>Použití indexerů (Průvodce programováním v C#)
Indexery jsou syntaktické pohodlí, které vám umožní vytvořit [třídy](../../../csharp/language-reference/keywords/class.md), [struktura](../../../csharp/language-reference/keywords/struct.md), nebo [rozhraní](../../../csharp/language-reference/keywords/interface.md) , klientské aplikace můžou k stejně jako pole. Indexery jsou nejčastěji implementovány v typech, jejichž primárním účelem je k zapouzdření vnitřní kolekce nebo pole. Předpokládejme například, že máte třídu s názvem TempRecord, který představuje teploty v Farenheit zjištěná v různých časech 10 během období 24 hodin. Třída obsahuje pole s názvem "podmínky" float – typ pro reprezentaci teploty a <xref:System.DateTime> , který představuje datum teploty byly zaznamenány. Implementací indexer v této třídě klienti mají přístup k teploty v instanci TempRecord jako `float temp = tr[4]` místo jako `float temp = tr.temps[4]`. Notace indexeru nejen zjednodušuje syntaxi pro klientské aplikace; také udržuje třídy a jejím účelem intuitivnější pro ostatní vývojáři mohli pochopit.  
  
 Chcete-li deklarovat indexer na třídě nebo struktuře, použijte [to](../../../csharp/language-reference/keywords/this.md) – klíčové slovo, jako v následujícím příkladu:  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 Typ indexeru a jeho parametry musí být přinejmenším stejně dostupná jako samotný indexeru. Další informace o úrovní přístupu najdete v tématu [modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Další informace o tom, jak používat indexery s rozhraním najdete v tématu [rozhraní indexery](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).  
  
 Podpis indexeru se skládá z počet a typy formálních parametrů. Neobsahuje typ indexeru nebo názvy formálních parametrů. Je-li deklarována více než jeden indexeru ve stejné třídě, musí mít různé podpisy.  
  
 Není to indexerem hodnota klasifikováno jako proměnné. Proto nemůžete předat hodnotu indexer jako [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru.  
  
 Chcete-li poskytnout indexer s názvem, který můžete použít jiné jazyky, použijte `name` atribut v deklaraci. Příklad:  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 Indexer bude mít název `TheItem`. Neposkytují atribut name s žádným `Item` výchozí název.  
  
## <a name="example-1"></a>Příklad 1  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje, jak deklarovat soukromé pole `temps`a indexer. Indexer umožňuje přímý přístup k instanci `tempRecord[i]`. Je deklarovat pole jako alternativu k použití indexeru [veřejné](../../../csharp/language-reference/keywords/public.md) člena a přistupovat k jejím členům `tempRecord.temps[i]`, přímo.  
  
 Všimněte si, že při přístupu indexer vyhodnocování, například v `Console.Write` příkazu [získat](../../../csharp/language-reference/keywords/get.md) přístupového objektu je vyvolán. Proto pokud žádná `get` přistupující objekt existuje, dojde k chybě kompilace.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a>Indexování s využitím jiné hodnoty  
 C# neomezuje typ indexu na celé číslo. Například může být vhodné použít řetězec s indexeru. Pomocí hledání řetězce v kolekci a vrátí odpovídající hodnotu, může implementovat takové indexer. Jako přístupové objekty mohou být přetíženy, řetězce a celá čísla verzí můžou existovat vedle sebe.  
  
## <a name="example-2"></a>Příklad 2  
  
### <a name="description"></a>Popis  
 V tomto příkladu je deklarována třída, ve kterém je uložený dny v týdnu. A `get` přístupový objekt je deklarovaný, která přebírá řetězec názvu dne a vrátí odpovídající celé číslo. Například neděle se vrátí 0, pondělí se vrátí 1 atd.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Existují dva hlavní způsoby, ve kterých se může zlepšit zabezpečení a spolehlivost indexery:  
  
-   Nezapomeňte zahrnout nějaký typ strategie zpracování chyb pro zpracování riziko klientský kód předá hodnotu neplatný index. V prvním příkladu výše v tomto tématu poskytuje třídu TempRecord vlastnost Length, která umožňuje klientské kód pro ověření vstupu před předáním to indexerem. Můžete také vložit kód uvnitř samotného indexeru pro zpracování chyb. Ujistěte se, k dokumentaci pro uživatele žádné výjimky, které můžete vyvolat uvnitř indexer přistupující objekt.  
  
-   Nastavte přístupnost `get` a [nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekty být omezení je přijatelné. To je důležité pro `set` přístupového objektu v konkrétní. Další informace najdete v tématu [omezení přístupnosti přístupového objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Indexery](../../../csharp/programming-guide/indexers/index.md)  
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
