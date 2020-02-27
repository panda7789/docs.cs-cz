---
title: Použití indexerů – C# Průvodce programováním
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628160"
---
# <a name="using-indexers-c-programming-guide"></a>Použití indexerů (C# Průvodce programováním)

Indexery jsou syntaktické pohodlí, které umožňují vytvořit [třídu](../../language-reference/keywords/class.md), [strukturu](../../language-reference/builtin-types/struct.md)nebo [rozhraní](../../language-reference/keywords/interface.md) , které mohou klientské aplikace přistupovat pouze jako pole. Indexery se nejčastěji implementují v typech, jejichž primární účel je zapouzdření interní kolekce nebo pole. Předpokládejme například, že máte třídu `TempRecord`, která představuje teplotu ve stupních Fahrenheita zaznamenanou v 10 různých časech během 24 hodin. Třída obsahuje pole `temps` typu `float[]` pro uložení hodnot teploty. Implementací indexeru v této třídě mají klienti přístup k teplotám v instanci `TempRecord` jako `float temp = tr[4]` namísto `float temp = tr.temps[4]`. Zápis indexeru zjednodušuje syntaxi pro klientské aplikace. také umožňuje, aby byla třída a její účel intuitivnějšíější, aby bylo možné porozumět ostatním vývojářům.  
  
Chcete-li deklarovat indexer pro třídu nebo strukturu, použijte klíčové slovo [This](../../language-reference/keywords/this.md) , jak ukazuje následující příklad:

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a>Poznámky

Typ indexeru a typ jeho parametrů musí být alespoň tak přístupný jako indexovací člen. Další informace o úrovních dostupnosti najdete v tématu [modifikátory přístupu](../../language-reference/keywords/access-modifiers.md).  
  
 Další informace o použití indexerů s rozhraním naleznete v tématu [indexery rozhraní](./indexers-in-interfaces.md).  
  
 Signatura indexeru se skládá z počtu a typů jeho formálních parametrů. Nezahrnuje typ indexeru ani názvy formálních parametrů. Pokud deklarujete více než jednoho indexeru ve stejné třídě, musí mít jiné signatury.  
  
 Hodnota indexeru není klasifikována jako proměnná; Proto nemůžete předat hodnotu indexeru jako parametr [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) .  
  
 Chcete-li poskytnout indexer s názvem, který mohou použít jiné jazyky, použijte <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, jak ukazuje následující příklad:  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

Tento indexer bude mít název `TheItem`. Neposkytnutí atributu name by `Item` výchozí název.  
  
## <a name="example-1"></a>Příklad 1  
  
Následující příklad ukazuje, jak deklarovat pole soukromého pole, `temps`a indexer. Indexer umožňuje přímý přístup k instanci `tempRecord[i]`. Alternativou k použití indexeru je deklarovat pole jako [veřejný](../../language-reference/keywords/public.md) člen a přistupovat ke svým členům, `tempRecord.temps[i]`přímo.  
  
 Všimněte si, že při vyhodnocení přístupu indexeru, například v příkazu `Console.Write`, je vyvolán přistupující objekt [Get](../../language-reference/keywords/get.md) . Proto pokud neexistuje žádný přistupující objekt `get`, dojde k chybě při kompilaci.  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a>Indexování pomocí jiných hodnot

C#neomezuje typ parametru indexeru na celé číslo. Může být například užitečné použít řetězec s indexerem. Takový indexer může být implementován vyhledáním řetězce v kolekci a vrácením příslušné hodnoty. Protože přistupující objekty mohou být přetíženy, může řetězec a celočíselná verze existovat souběžně.  
  
## <a name="example-2"></a>Příklad 2  
  
Následující příklad deklaruje třídu, která ukládá dny v týdnu. Přistupující objekt `get` přebírá řetězec, název dne a vrátí odpovídající celé číslo. Například "neděle" vrátí 0, "pondělí" vrátí 1 a tak dále.  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a>Robustní programování

 Existují dva hlavní způsoby, jak lze zlepšit zabezpečení a spolehlivost indexerů:  
  
- Nezapomeňte začlenit nějaký typ strategie zpracování chyb pro zpracování pravděpodobnosti, že klientský kód projde neplatnou hodnotou indexu. V prvním příkladu výše v tomto tématu Třída TempRecord poskytuje vlastnost length, která umožňuje kódu klienta ověřit vstup před jeho předáním indexeru. Kód pro zpracování chyb můžete také vložit do samotného indexeru. Nezapomeňte uživatelům zdokumentovat všechny výjimky, které jste vyvolali uvnitř přístupového objektu indexeru.  
  
- Nastavte přístupnost přístupových objektů [Get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) jako omezujících oprávnění, která jsou přiměřená. To je důležité zejména pro přistupující objekt `set`. Další informace najdete v tématu [Omezení přístupnosti přístupového objektu](../classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Indexery](./index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
