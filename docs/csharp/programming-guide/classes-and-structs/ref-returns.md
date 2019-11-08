---
title: Návratové hodnoty ref a lokální hodnoty REFC# (Průvodce)
description: Naučte se definovat a používat místní hodnoty Return a ref ref.
ms.date: 04/04/2018
ms.openlocfilehash: 7ade422b5b3805ef2e1f487252a98fb85cdfe70c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736815"
---
# <a name="ref-returns-and-ref-locals"></a>Návratové hodnoty podle odkazu a lokální proměnné podle odkazu

Počínaje C# 7,0 C# podporuje návratové hodnoty odkazů (vrátí ref). Návratová hodnota odkazu umožňuje metodě vrátit odkaz na proměnnou, nikoli na hodnotu, zpět volajícímu. Volající pak může zvolit, že se vrácená proměnná bude zacházet, jako kdyby byla vrácena hodnotou nebo odkazem. Volající může vytvořit novou proměnnou, která je sám odkazem na vrácenou hodnotu, která se nazývá ref Local.

## <a name="what-is-a-reference-return-value"></a>Co je návratová hodnota odkazu?

Většina vývojářů je obeznámená s předáním argumentu s volanou metodou *odkazem*. Seznam argumentů volané metody obsahuje proměnnou předanou odkazem. Všechny změny provedené v hodnotě volané metodou jsou pozorovány volajícím. *Návratová hodnota odkazu* znamená, že metoda vrátí *odkaz* (nebo alias) na určitou proměnnou. Rozsah této proměnné musí zahrnovat metodu. Životnost této proměnné musí překračovat rámec návratové metody. Změny návratové hodnoty metody volajícím jsou provedeny na proměnnou, která je vrácena metodou.

Deklarace, že metoda vrátí *návratovou hodnotu odkazu* , označuje, že metoda vrací alias k proměnné. Záměr návrhu je často, že volající kód by měl mít přístup k této proměnné prostřednictvím aliasu, včetně změny. Tyto metody vracené odkazem nemohou mít návratový typ `void`.

Existují určitá omezení pro výraz, který metoda může vracet jako návratovou hodnotu odkazu. Mezi omezení patří:

- Návratová hodnota musí mít životnost, která překračuje provádění metody. Jinými slovy nemůže být lokální proměnná v metodě, která ji vrací. Může to být instance nebo statické pole třídy, nebo může být argument předaný metodě. Pokus o návrat lokální proměnné generuje chybu kompilátoru CS8168, "" nemůže vrátit místní "obj" odkazem, protože se nejedná o místní odkaz. "

- Návratovou hodnotou nemůže být literální `null`. Vrácení `null` generuje chybu kompilátoru CS8156; "výraz nelze v tomto kontextu použít, protože jej nelze vrátit odkazem."

   Metoda s návratovým odkazem může vracet alias k proměnné, jejíž hodnota je aktuálně hodnotou null (bez instancí) nebo [typ hodnoty s možnou hodnotou null](../../language-reference/builtin-types/nullable-value-types.md) pro typ hodnoty.

- Návratovou hodnotou nemůže být konstanta, člen výčtu, návratová hodnota po hodnotě z vlastnosti nebo metoda `class` nebo `struct`. Porušení tohoto pravidla generuje chybu kompilátoru CS8156. výraz nemůže být v tomto kontextu použit, protože jej nelze vrátit odkazem.

Kromě toho nejsou povoleny návratové hodnoty odkazů u asynchronních metod. Asynchronní metoda může vracet před dokončením provádění, zatímco vrácená hodnota je stále neznámá.

## <a name="defining-a-ref-return-value"></a>Definování návratové hodnoty REF

Metoda, která vrací *vrácenou hodnotu odkazu* , musí splňovat následující dvě podmínky:

- Signatura metody obsahuje klíčové slovo [ref](../../language-reference/keywords/ref.md) před návratovým typem.
- Každý příkaz [return](../../language-reference/keywords/return.md) v těle metody obsahuje klíčové slovo [ref](../../language-reference/keywords/ref.md) před název vrácené instance.

Následující příklad ukazuje metodu, která splňuje tyto podmínky a vrací odkaz na objekt `Person` s názvem `p`:

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Využívání návratové hodnoty REF

Návratová hodnota REF je alias jiné proměnné v oboru volané metody. Můžete interpretovat jakékoli použití parametru REF jako pomocí proměnné aliasy IT:

- Pokud přiřadíte jeho hodnotu, přiřadíte jí hodnotu proměnné, které aliasuje.
- Při čtení hodnoty se čte hodnota proměnné, které aliasuje.
- Pokud ho vrátíte *odkazem*, vracíte alias pro stejnou proměnnou.
- Pokud je předáte do jiné metody *odkazem*, předáváte odkaz na proměnnou, kterou aliasuje.
- Při vytváření [referenčního místního](#ref-locals) aliasu je třeba vytvořit nový alias pro stejnou proměnnou.

## <a name="ref-locals"></a>Lokální hodnoty REF

Předpokládat, že metoda `GetContactInformation` je deklarovaná jako ref Return:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Přiřazení podle hodnoty přečte hodnotu proměnné a přiřadí ji k nové proměnné:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Předchozí přiřazení deklaruje `p` jako místní proměnnou. Počáteční hodnota je zkopírována z čtení hodnoty vrácené `GetContactInformation`. Jakákoli budoucí přiřazení `p` nemění hodnotu proměnné vrácené `GetContactInformation`. Proměnná `p` již není aliasem pro vrácenou proměnnou.

Deklaraci *místní proměnné ref* můžete pro zkopírování aliasu na původní hodnotu. V následujícím přiřazení je `p` alias pro proměnnou vrácenou z `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Následné použití `p` je stejné jako použití proměnné vrácené `GetContactInformation`, protože `p` je alias pro tuto proměnnou. Změny `p` také mění proměnnou vrácenou z `GetContactInformation`.

Klíčové slovo `ref` se používá před deklarací místní proměnné *a* před voláním metody. 

K hodnotě můžete přistupovat stejným způsobem pomocí odkazu. V některých případech přístup k hodnotě pomocí odkazu zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování. Například následující příkaz ukazuje, jak může jeden definovat místní hodnotu REF, která se používá k odkazování na hodnotu.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Klíčové slovo `ref` se používá před deklarací místní proměnné *a* před hodnotou v druhém příkladu. Nepovedlo se zahrnout klíčová slova `ref` v deklaraci proměnné a přiřazení v obou příkladech způsobí chybu kompilátoru CS8172. "nemůže inicializovat proměnnou podle odkazu s hodnotou." 

Před C# 7,3 se nepovedlo znovu přiřadit místní proměnné ref, aby se po inicializaci odkazovaly na jiné úložiště. Toto omezení bylo odebráno. Následující příklad ukazuje změnu přiřazení:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Místní proměnné ref musí být při deklarování stále inicializovány.

## <a name="ref-returns-and-ref-locals-an-example"></a>Návratové hodnoty ref a lokální hodnoty REF: příklad

Následující příklad definuje třídu `NumberStore`, která ukládá pole celočíselných hodnot. Metoda `FindNumber` vrací odkazem na první číslo, které je větší než nebo rovno číslu předanému jako argument. Pokud číslo není větší než nebo rovno argumentu, vrátí metoda číslo v indexu 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Následující příklad volá metodu `NumberStore.FindNumber` pro načtení první hodnoty, která je větší nebo rovna 16. Volající pak zdvojnásobí hodnotu vrácenou metodou. Výstup z příkladu ukazuje změnu odrážející se v hodnotě prvků pole instance `NumberStore`.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Bez podpory návratových hodnot odkazů je taková operace provedena vrácením indexu prvku pole spolu s jeho hodnotou. Volající pak může použít tento index k úpravě hodnoty v samostatném volání metody. Volající však může také změnit index k přístupu a případně upravit jiné hodnoty pole.  

Následující příklad ukazuje, jak může být metoda `FindNumber` přepsána po C# 7,3 pro použití místního opětovného přiřazení ref:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Tato druhá verze je efektivnější s delšími sekvencemi ve scénářích, kde se hledané číslo blíží konci pole.

## <a name="see-also"></a>Viz také:

- [ref – klíčové slovo](../../language-reference/keywords/ref.md)
- [Zapisovat bezpečný efektivní kód](../../write-safe-efficient-code.md)
