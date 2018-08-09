---
title: Návratové hodnoty REF a místní referenční hodnoty (Průvodce v C#)
description: Zjistěte, jak definovat a používat ref návratové a místní hodnoty ref
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: e749b9c9309a4b1a737a0c1d0b5e1cfe5748114a
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "33339615"
---
# <a name="ref-returns-and-ref-locals"></a>Návratové a místní referenční hodnoty

Od verze C# 7.0, C# podporuje referenční návratové hodnoty (ref vrátí). Odkaz na návratové hodnoty umožňuje metody, která vrátí odkaz na proměnnou, nikoli hodnotu, zpět do volajícího. Volající pak můžete přistupovat ke všem vrácené proměnnou, jako by byly vráceny hodnotou nebo odkazem. Volající může vytvořit odkaz na vrácené hodnoty ref volá místní novou proměnnou, která sama o sobě.

## <a name="what-is-a-reference-return-value"></a>Co je návratová hodnota odkaz?

Většina vývojářů znají předání argumentu do volané metody *odkazem*. Seznam argumentů volané metody obsahuje proměnnou předány podle odkazu. Změny provedené na hodnotu ve volané metody jsou dodržovány volajícím. A *odkazovat na návratovou hodnotu* znamená, že metoda vrátí *odkaz* (nebo alias) některé proměnné. Tato proměnná rozsahu musí zahrnovat metodu. Tato proměnná životnost musí přesahovat vrácení metody. Návratovou hodnotu metody volající změn do proměnné, který je vrácen touto metodou.

Deklarace, která vrací metoda *odkazovat na návratovou hodnotu* označuje, že metoda vrací alias na proměnnou. Návrh záměr je často, že volající kód mají mít přístup k této proměnné prostřednictvím alias, včetně jej upravit. Vyplývá, že metody vracející odkaz nemůže mít návratový typ `void`.

Platí určitá omezení na výraz, který metoda může vrátit jako návratovou hodnotu odkazu. Omezení patří:

- Vrácená hodnota musí mít životností, která se rozpíná za provádění metody. Jinými slovy nemůže být lokální proměnná v metodě, která vrátí jej. Může se jednat instance nebo statické pole třídy, nebo může být argument předaný metodě. Pokus o vrácení, že místní proměnná vygeneruje Chyba kompilátoru CS8168, "nejde vrátit místní"obj"podle odkazu protože se nejedná o lokální proměnnou."

- Návratová hodnota nemůže být literál `null`. Vrací `null` vygeneruje Chyba kompilátoru CS8156 "výraz nelze použít v tomto kontextu, protože nemusí být vrácená odkazem."

   Metoda s ref návratový může vrátit alias na proměnnou, jehož hodnota je aktuálně hodnotu null (nevytvořeným instancím) nebo [typ připouštějící hodnotu Null](../nullable-types/index.md) pro typ hodnoty.
 
- Návratová hodnota nemůže být konstantní, člen výčtového typu, podle hodnoty vrátí hodnotu z vlastnosti nebo metody `class` nebo `struct`. Porušení tohoto pravidla vygeneruje Chyba kompilátoru CS8156 "výraz nelze použít v tomto kontextu, protože nemusí být vrácená odkazem."

Kromě toho referenční návratové hodnoty nejsou povoleny v asynchronních metodách. Asynchronní metoda může vrátit předtím, než se dokončí provádění, vrácená hodnota je stále neznámý.
 
## <a name="defining-a-ref-return-value"></a>Definování návratová hodnota ref.

Metoda, která vrátí *odkazovat na návratovou hodnotu* musí splňovat tyto dvě podmínky:

- Podpis metody zahrnuje [ref](../../language-reference/keywords/ref.md) – klíčové slovo před návratovým typem.
- Každý [vrátit](../../language-reference/keywords/return.md) zahrnuje příkaz v těle metody [ref](../../language-reference/keywords/ref.md) – klíčové slovo před název vrácená instance.

Následující příklad ukazuje metodu, která splňuje tyto podmínky a vrátí odkaz na `Person` objekt s názvem `p`:

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Využívání návratová hodnota ref.

Ref návratové hodnoty je alias pro jiné proměnné v oboru volané metody. Lze interpretovat jakékoli využití návratový ref jako pomocí proměnné ho aliasy:

- Když přiřadíte její hodnotu, jsou přiřazení hodnoty proměnné ho aliasy.
- Při čtení jeho hodnotu při čtení hodnota proměnné je aliasy.
- Je-li se vrátit *odkazem*, alias se vrátí na tuto proměnnou stejné.
- Pokud předáte jiný způsob *odkazem*, jsou předáním odkazu na proměnnou je aliasy.
- Je-li [lokální proměnná podle odkazu](#ref-local) alias, můžete vytvořit nový alias u stejné proměnné.


## <a name="ref-locals"></a>Místní referenční hodnoty

Předpokládá `GetContactInformation` metoda je deklarován jako ref vrácení:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Přiřazení podle hodnoty přečte hodnotu proměnné a přiřadí ji nové proměnné:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Deklaruje předchozí přiřazení `p` jako místní proměnná. Počáteční hodnoty je zkopírován z čtení hodnoty vrácené `GetContactInformation`. Všechny budoucí přiřazení `p` nedojde ke změně hodnoty proměnné vrácený `GetContactInformation`. Proměnná `p` už není alias proměnné vrácen.

Deklarujete *lokální proměnná podle odkazu* proměnnou ke zkopírování alias na původní hodnotu. V následující přiřazení `p` se alias pro proměnnou vrácená `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Další využití `p` je stejný jako pomocí proměnné vrácený `GetContactInformation` protože `p` je alias pro danou proměnnou. Změny `p` také změnit proměnnou vrácená `GetContactInformation`.

`ref` Klíčové slovo se používá i před deklarace lokální proměnné *a* před voláním metody. 

Stejným způsobem můžete přistupovat hodnota podle odkazu. V některých případech se přístup k hodnota podle odkazu zvyšuje výkon se vyhnout operaci kopírování potenciálně nákladné. Následující příkaz například ukazuje, jak jeden můžete definovat, který se používá k odkazování hodnotu lokální hodnota ref.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

`ref` Klíčové slovo se používá i před deklarace lokální proměnné *a* před hodnotu v druhém příkladu. Selhání oba `ref` klíčová slova v deklaraci proměnné a přiřazení v obou příkladech vede k chybě kompilátoru CS8172, "nelze inicializovat proměnnou podle odkazu s hodnotou." 

Před C# 7.3 místní proměnné odkazu nelze přiřadit k odkazování na jiného úložiště po jejich inicializaci. Odebrali jsme omezení. Následující příklad ukazuje změnu přiřazení:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Místní proměnné odkazu musí být stále inicializován, pokud jsou deklarovány.

## <a name="ref-returns-and-ref-locals-an-example"></a>Návratové a místní referenční hodnoty: příklad

Následující příklad definuje `NumberStore` třída, která obsahuje pole celočíselných hodnot. `FindNumber` Metoda vrací odkazem. první číslo, které je větší než nebo rovno počtu předán jako argument. Pokud číslo je větší než nebo rovna hodnotě argumentu, metoda vrátí číslo v indexu 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Následující příklad volá `NumberStore.FindNumber` metoda načíst první hodnotu, která je větší než nebo rovný 16. Volající pak zdvojnásobuje hodnota vrácená metodou. Výstup z příkladu ukazuje změnu v hodnotě pole prvků `NumberStore` instance.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Bez podpory pro referenční návratové hodnoty tato operace se provádí tak, že vrací index prvku pole společně s jeho hodnotu. Volající pak můžete použít tento index ke změně hodnoty v samostatné metodě volání. Volající však můžete také upravit index pro přístup k a případně upravit další hodnoty pole.  

Následující příklad ukazuje způsob, jakým `FindNumber` metody by mohla být přepsána za C# 7.3 používat místní opětovné přiřazení odkazu:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Tento druhý verze je mnohem efektivnější s delší pořadí ve scénářích, kde číslo žádá o blíž ke konci pole.

## <a name="see-also"></a>Viz také:

[REF – klíčové slovo](../../language-reference/keywords/ref.md)  
[Referenční sémantika s typy hodnot](../../../csharp/reference-semantics-with-value-types.md)
