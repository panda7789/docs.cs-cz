---
title: Použití indexerů – programovací příručka jazyka C#
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628160"
---
# <a name="using-indexers-c-programming-guide"></a>Použití indexerů (Průvodce programováním jazyka C#)

Indexery jsou syntaktické pohodlí, které umožňují vytvořit [třídu](../../language-reference/keywords/class.md), [strukturu](../../language-reference/builtin-types/struct.md)nebo [rozhraní,](../../language-reference/keywords/interface.md) ke kterým mohou klientské aplikace přistupovat stejně jako pole. Indexery jsou nejčastěji implementovány v typech, jejichž primárním účelem je zapouzdřit vnitřní kolekci nebo pole. Předpokládejme například, že `TempRecord` máte třídu, která představuje teplotu ve Fahrenheitu, jak je zaznamenána v 10 různých časech během období 24 hodin. Třída obsahuje pole `temps` typu `float[]` pro uložení hodnot teploty. Implementací indexeru v této třídě mohou klienti `TempRecord` přistupovat k teplotám v instanci jako `float temp = tr[4]` namísto jako `float temp = tr.temps[4]`. Zápis indexeru nejen zjednodušuje syntaxi pro klientské aplikace; to také dělá třídu a její účel intuitivnější pro ostatní vývojáře pochopit.  
  
Chcete-li deklarovat indexer ve třídě nebo struktuře, použijte klíčové slovo [This,](../../language-reference/keywords/this.md) jak ukazuje následující příklad:

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a>Poznámky

Typ indexeru a typ jeho parametrů musí být alespoň stejně přístupný jako samotný indexer. Další informace o úrovních usnadnění naleznete [v tématu Access Modifiers](../../language-reference/keywords/access-modifiers.md).  
  
 Další informace o použití indexerů s rozhraním naleznete v [tématu Interface Indexers](./indexers-in-interfaces.md).  
  
 Podpis indexeru se skládá z počtu a typů jeho formálních parametrů. Neobsahuje typ indexeru nebo názvy formálních parametrů. Pokud deklarujete více než jeden indexer ve stejné třídě, musí mít různé podpisy.  
  
 Hodnota indexeru není klasifikována jako proměnná. proto nelze předat hodnotu indexeru jako [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) parametr.  
  
 Chcete-li indexeru poskytnout název, který <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>mohou používat jiné jazyky, použijte , jak ukazuje následující příklad:  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

Tento indexer bude `TheItem`mít název . Nezadání atributu name `Item` by vytvořilo výchozí název.  
  
## <a name="example-1"></a>Příklad 1  
  
Následující příklad ukazuje, `temps`jak deklarovat soukromé pole pole a indexer. Indexer umožňuje přímý přístup `tempRecord[i]`k instanci . Alternativou k použití indexeru je deklarovat pole jako `tempRecord.temps[i]` [veřejný](../../language-reference/keywords/public.md) člen a přístup k jeho členy, , přímo.  
  
 Všimněte si, že při vyhodnocování `Console.Write` přístupu indexeru, například v příkazu, je vyvolán přístupový objekt [get.](../../language-reference/keywords/get.md) Proto pokud `get` neexistuje žádný přistupující objektů, dojde k chybě v době kompilace.  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a>Indexování pomocí jiných hodnot

C# neomezuje typ parametru indexeru na celé číslo. Například může být užitečné použít řetězec s indexerem. Takový indexer může být implementována hledáním řetězce v kolekci a vrácením příslušné hodnoty. Jako přístupové položky mohou být přetíženy, řetězec a celočíselné verze mohou existovat společně.  
  
## <a name="example-2"></a>Příklad 2  
  
Následující příklad deklaruje třídu, která ukládá dny v týdnu. Přistupující `get` pole trvá řetězec, název dne a vrátí odpovídající celé číslo. Například "Neděle" vrátí 0, "Pondělí" vrátí 1 a tak dále.  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a>Robustní programování

 Existují dva hlavní způsoby, jak zlepšit zabezpečení a spolehlivost indexerů:  
  
- Nezapomeňte začlenit nějaký typ strategie zpracování chyb pro zpracování pravděpodobnosti předání kódu klienta v neplatné hodnotě indexu. V prvním příkladu dříve v tomto tématu TempRecord třída poskytuje Length vlastnost, která umožňuje kód klienta ověřit vstup před předáním do indexeru. Můžete také umístit kód zpracování chyb uvnitř samotného indexeru. Ujistěte se, že dokument pro uživatele všechny výjimky, které vyvoláte uvnitř přístupu indexeru.  
  
- Nastavte přístupnost [přístupových](../../language-reference/keywords/get.md) a [nastavených](../../language-reference/keywords/set.md) přístupových částí, které mají být stejně omezující jako přiměřené. To je důležité `set` zejména pro přistupujícího. Další informace naleznete v [tématu Omezení přístupnosti přístupu k přístupu](../classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Indexery](./index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
