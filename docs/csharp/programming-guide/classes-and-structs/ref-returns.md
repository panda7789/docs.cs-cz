---
title: Návratové hodnoty REF a ref lokální proměnné (Průvodce C#)
description: Zjistěte, jak definovat a použijte ref vrátit a místní hodnoty ref
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: e749b9c9309a4b1a737a0c1d0b5e1cfe5748114a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ref-returns-and-ref-locals"></a>Vrátí REF a místní hodnoty ref

Od verze 7.0 C#, C# podporuje odkaz návratové hodnoty (ref vrátí). Odkaz vrátí hodnotu umožňuje metodu pro odkaz na proměnnou, nikoli hodnotu, vrátí zpět do volající. Volající může zvolte zacházet s Vrácená proměnná, jako kdyby byly vráceny, hodnotou nebo odkazem. Volající můžete vytvořit nové proměnné, který je sám odkaz na vrácené hodnoty, názvem ref místní.

## <a name="what-is-a-reference-return-value"></a>Co je návratovou hodnotu odkazu?

Většina vývojářů obeznámeni s předáním argumentu volané metodě *odkazem*. Seznam argumentů zavolat metodu zahrnuje předaná odkaz na proměnnou. Všechny změny provedené zavolat metodu na jeho hodnotu je možné vysledovat volajícího. A *odkazovat návratovou hodnotu* znamená, že metoda vrátí *odkaz* (nebo alias) některé proměnné. Tuto proměnnou oboru musí obsahovat metodu. Tuto proměnnou životnost, musíte rozšířit nad rámec návratový metody. Úpravy návratovou hodnotu metody volajícího jsou vytvářeny proměnnou, kterou vrátí metodu.

Deklarace, který vrací metodu *odkazovat návratová hodnota* označuje, že metoda vrátí alias proměnné. Návrh je často, volající kód mají mít přístup k této proměnné prostřednictvím alias, včetně jej upravit. Vyplývá, že metody vrácení podle reference nemůže mít návratový typ `void`.

Existují některá omezení na výrazu, která vrací metodu jako návratová hodnota odkazu. Omezení, patří:

- Návratová hodnota musí mít životnost, který je delší než provádění metody. Jinými slovy nemůže být místní proměnné v metodě, která vrátí ji. Dá se instanci nebo statické pole třídy, nebo může být argument předaný metodě. Probíhá pokus o vraťte se generuje chyba kompilátoru CS8168, místní proměnné "nemůže vrátit místní 'obj' odkazem protože se nejedná o místní ref."

- Návratová hodnota nemůže být literál `null`. Vrácení `null` vygeneruje Chyba kompilátoru CS8156, "výraz nelze použít v tomto kontextu, protože nemusí být vrátil odkazem."

   Metoda s návratovým ref může vrátit alias do proměnné, jehož hodnota je aktuálně hodnotu null (bez instancí) nebo [typ s možnou hodnotou Null](../nullable-types/index.md) pro typ hodnoty.
 
- Návratová hodnota nemůže být konstanta, člena výčtu, podle hodnota vrácená vlastnost nebo metoda `class` nebo `struct`. Narušení toto pravidlo generuje chyba kompilátoru CS8156, "výraz nelze použít v tomto kontextu, protože nemusí být vrátil odkazem."

Kromě toho odkaz návratové hodnoty nejsou povoleny na asynchronní metody. Asynchronní metoda může vrátit před dokončením provádění, zatímco vrácená hodnota je stále neznámé.
 
## <a name="defining-a-ref-return-value"></a>Definice návratové hodnoty ref

Definice návratové hodnoty ref přidáním [ref](../../language-reference/keywords/ref.md) – klíčové slovo k návratový typ podpis metody. Například následující podpis znamená, že `GetContactInformation` vrátí odkaz na vlastnost `Person` objekt, který má volající:

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

Kromě toho název objektu vrácené každou [vrátit](../../language-reference/keywords/return.md) příkaz v těle metoda musí předcházet [ref](../../language-reference/keywords/ref.md) – klíčové slovo. Například následující `return` příkaz vrátí odkaz na `Person` objekt s názvem `p`:

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>Využívání návratové hodnoty ref

Ref vrátí, zda je hodnota alias jiné proměnné v oboru zavolat metodu. Dokáže interpretovat jakékoli využití návratový ref jako použití proměnné ho aliasy:

- Při přiřazení jeho hodnota se přiřazení hodnoty proměnné ho aliasy.
- Při čtení jeho hodnota se čtení hodnoty proměnné ho aliasy.
- Pokud se ji vrátíte *odkazem*, alias se vrátíte k dané stejné proměnné.
- Pokud předáte na jinou metodu *odkazem*, jsou předáním odkazu na proměnnou ho aliasy.
- Pokud vytvoříte [ref místní](#ref-local) alias, provedete nový alias stejnou proměnnou.


## <a name="ref-locals"></a>Místní hodnoty REF

Předpokládejme, `GetContactInformation` metoda je deklarován jako ref návratový:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

-Hodnota přiřazení čte hodnotu proměnné a přiřadí ji k nové proměnné:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Předchozí přiřazení deklaruje `p` jako místní proměnné. Počáteční hodnoty budou zkopírována z čtení hodnoty vrácené `GetContactInformation`. Všechny budoucí přiřazení `p` nedojde ke změně hodnoty proměnné vrácený `GetContactInformation`. Proměnná `p` již není alias proměnnou vrátila.

Deklarování *ref místní* proměnné pro kopírování alias na původní hodnotu. V následující přiřazení `p` je alias proměnnou, kterou vrátil `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Následné použití `p` je stejný jako použití proměnné vrácený `GetContactInformation` protože `p` je alias pro tuto proměnnou. Změny `p` změnit také proměnnou, kterou vrátil `GetContactInformation`.

`ref` – Klíčové slovo se používá i před místní deklarace proměnné *a* před voláním metody. 

Hodnotu můžete přejít pomocí odkazu stejným způsobem. V některých případech přístup k hodnotu odkazem zvyšuje výkon vyhnout potenciálně nákladné kopírování. Například následující příkaz ukazuje, jak jeden můžete definovat ref místní hodnotu, která slouží k odkazování hodnotu.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

`ref` – Klíčové slovo se používá i před místní deklarace proměnné *a* před hodnotu v druhém příkladu. Nepodařilo se současně obsahovat `ref` klíčová slova v deklarace proměnné a přiřazení v obou příklady výsledkem chyba kompilátoru CS8172, "nelze inicializovat proměnnou podle odkazu s hodnotou." 

Před C# 7.3 nelze odkazovat na jiného úložiště po inicializaci přeřadit ref lokální proměnné. Aby byla odebrána omezení. Následující příklad ukazuje opětovnému přiřazení:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Lokální proměnné REF musí být stále inicializován, když jsou deklarovány.

## <a name="ref-returns-and-ref-locals-an-example"></a>Vrátí REF a místní hodnoty ref: příklad

V následujícím příkladu definuje `NumberStore` třídu, která ukládá pole celočíselné hodnoty. `FindNumber` Metoda vrátí odkaz na číslo, kterým je větší než nebo rovná počtu předat jako argument. Pokud žádné číslo větší než nebo rovna hodnotě argument, metoda vrátí číslo v indexu 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Následující příklad volání `NumberStore.FindNumber` metoda načíst první hodnotu, která je větší než nebo rovný 16. Volající pak zdvojnásobí hodnota vrácená metodou. Výstup z příkladu zobrazuje změny projeví v hodnotě pole elementů `NumberStore` instance.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Bez podpory pro vrácené hodnoty odkaz takovou operaci provádí vrácení index pole element společně s jeho hodnotu. Volající potom můžete pomocí tohoto indexu změňte hodnotu v samostatné metodě volání. Volající však můžete také upravit index pro přístup a které by mohly mít úpravy ostatní hodnoty pole.  

Následující příklad ukazuje jak `FindNumber` metoda by mohla být přepsána po 7.3 C# používat místní změny přiřazení ref:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Tato druhá verze je efektivnější s delší pořadí ve scénářích, kde číslo žádá o blíž ke konci pole.

## <a name="see-also"></a>Viz také

[REF – klíčové slovo](../../language-reference/keywords/ref.md)  
[Odkaz na sémantiku s typy hodnot](../../../csharp/reference-semantics-with-value-types.md)
