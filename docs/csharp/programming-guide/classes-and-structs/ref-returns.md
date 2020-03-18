---
title: Ref vrácené hodnoty a místní ref (C# Guide)
description: Naučte se definovat a používat ref return a ref místní hodnoty
ms.date: 04/04/2018
ms.openlocfilehash: 87a9538db60d69062f0fb48ed9683a9d4f972b91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170070"
---
# <a name="ref-returns-and-ref-locals"></a>Návratové hodnoty podle odkazu a lokální proměnné podle odkazu

Počínaje C# 7.0, C# podporuje referenční vrácené hodnoty (ref vrátí). Vrácená hodnota odkazu umožňuje metodu vrátit odkaz na proměnnou, nikoli hodnotu, zpět volajícímu. Volající pak můžete zvolit léčbu vrácené proměnné, jako kdyby byly vráceny podle hodnoty nebo odkazem. Volající může vytvořit novou proměnnou, která je sama odkaz na vrácenou hodnotu, nazývanou ref local.

## <a name="what-is-a-reference-return-value"></a>Co je referenční vrácená hodnota?

Většina vývojářů je obeznámena s předáním argumentu volané *metodě odkazem*. Seznam argumentů volané metody obsahuje proměnnou předanou odkazem. Všechny změny provedené v jeho hodnotě volanou metodou jsou sledovány volajícím. Referenční *vrácená hodnota* znamená, že metoda vrátí *odkaz* (nebo alias) na nějakou proměnnou. Rozsah této proměnné musí obsahovat metodu. Životnost této proměnné musí přesahovat vrácení metody. Změny návratové hodnoty metody volajícím jsou provedeny na proměnnou, která je vrácena metodou.

Deklarování, že metoda vrátí *referenční vrácená hodnota* označuje, že metoda vrátí alias proměnné. Záměr návrhu je často, že volající kód by měl mít přístup k této proměnné prostřednictvím aliasu, včetně jeho úpravy. Z toho vyplývá, že metody vracející se `void`odkazem nemůže mít návratový typ .

Existují určitá omezení výrazu, který může metoda vrátit jako referenční vrácenou hodnotu. Omezení zahrnují:

- Vrácená hodnota musí mít životnost, která přesahuje provádění metody. Jinými slovy nemůže být místní proměnnou v metodě, která ji vrací. Může se jedná o instanci nebo statické pole třídy nebo může být argumentem předaným metodě. Pokus o vrácení místní proměnné generuje chybu kompilátoru CS8168, "Nelze vrátit místní obj' odkazem, protože není ref místní."

- Vrácená hodnota nemůže být `null`literál . Vrácení `null` generuje chybu kompilátoru CS8156, "Výraz nelze použít v tomto kontextu, protože nemusí být vrácena odkazem."

   Metoda s návratem ref může vrátit alias proměnné, jejíž hodnota je aktuálně hodnota null (uninstantiated) nebo [typ hodnoty s možnou hodnotou s možnou hodnotou](../../language-reference/builtin-types/nullable-value-types.md) pro typ hodnoty.

- Vrácená hodnota nemůže být konstanta, člen výčtu, vrácená hodnota podle hodnoty `class` z `struct`vlastnosti nebo metoda a nebo . Porušení tohoto pravidla generuje chybu kompilátoru CS8156, "Výraz nelze použít v tomto kontextu, protože nemusí být vrácena odkazem."

Kromě toho referenční vrácené hodnoty nejsou povoleny na asynchronní metody. Asynchronní metoda může vrátit před dokončením spuštění, zatímco jeho vrácená hodnota je stále neznámý.

## <a name="defining-a-ref-return-value"></a>Definování vrácené hodnoty ref

Metoda, která vrací *referenční vrácenou hodnotu,* musí splňovat následující dvě podmínky:

- Podpis metody obsahuje klíčové slovo [ref](../../language-reference/keywords/ref.md) před návratovým typem.
- Každý [příkaz return](../../language-reference/keywords/return.md) v těle metody obsahuje klíčové slovo [ref](../../language-reference/keywords/ref.md) před názvem vrácené instance.

Následující příklad ukazuje metodu, která splňuje tyto podmínky `Person` a `p`vrátí odkaz na objekt s názvem :

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Spotřeba vrácené hodnoty ref

Vrácená hodnota ref je alias jiné proměnné v oboru volané metody. Jakékoli použití ref return můžete interpretovat jako použití proměnné, kterou aliasuje:

- Když přiřadíte její hodnotu, přiřazujete hodnotu proměnné, kterou aliasuje.
- Při čtení jeho hodnoty čtete hodnotu proměnné, kterou aliasuje.
- Pokud jej vrátíte *odkazem*, vracíte alias stejné proměnné.
- Pokud ji předáte jiné metodě *odkazem*, předáváte odkaz na proměnnou, kterou aliasuje.
- Když vytvoříte místní alias [ref,](#ref-locals) vytvoříte nový alias pro stejnou proměnnou.

## <a name="ref-locals"></a>Ref místní obyvatelé

Předpokládejme, `GetContactInformation` že metoda je deklarována jako ref return:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Přiřazení podle hodnoty přečte hodnotu proměnné a přiřadí ji k nové proměnné:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Předchozí přiřazení deklaruje `p` jako místní proměnné. Jeho počáteční hodnota je zkopírována ze čtení hodnoty vrácené `GetContactInformation`. Žádná budoucí přiřazení `p` nezmění hodnotu proměnné vrácené `GetContactInformation`. Proměnná `p` již není alias proměnné vrácené.

Deklarujete místní proměnnou *ref* pro kopírování aliasu na původní hodnotu. V následujícím přiřazení `p` je alias proměnné vrácené z `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Následné použití `p` je stejné jako použití `GetContactInformation` proměnné `p` vrácené, protože je alias pro tuto proměnnou. Změní `p` také změnu proměnné `GetContactInformation`vrácené z .

Klíčové `ref` slovo se používá jak před *deklarací* místní proměnné, tak před voláním metody.

Můžete přistupovat k hodnotě odkazem stejným způsobem. V některých případech přístup k hodnotě odkazem zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování. Například následující příkaz ukazuje, jak lze definovat ref místní hodnotu, která se používá k odkazu na hodnotu.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Klíčové `ref` slovo se používá jak před *deklarací* místní proměnné, tak před hodnotou v druhém příkladu. Pokud nezahrnete obě `ref` klíčová slova do deklarace proměnné a přiřazení v obou příkladech, výsledkem je chyba kompilátoru CS8172, "Nelze inicializovat proměnnou odkazu s hodnotou."

Před C# 7.3 ref místní proměnné nelze znovu přiřadit odkazovat na různé úložiště po inicializování. Toto omezení bylo odstraněno. Následující příklad ukazuje přeřazení:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Ref místní proměnné musí být stále inicializovány, když jsou deklarovány.

## <a name="ref-returns-and-ref-locals-an-example"></a>Ref vrátí a ref místní: příklad

Následující příklad definuje `NumberStore` třídu, která ukládá pole celé hodnoty. Metoda `FindNumber` vrátí odkazem na první číslo, které je větší nebo rovno číslo předáno jako argument. Pokud žádné číslo je větší než nebo rovno argument, metoda vrátí číslo v indexu 0.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Následující příklad volá `NumberStore.FindNumber` metodu k načtení první hodnoty, která je větší nebo rovna 16. Volající pak zdvojnásobí hodnotu vrácenou metodou. Výstup z příkladu ukazuje změnu, která se odráží `NumberStore` v hodnotě prvků pole instance.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Bez podpory pro referenční vrácené hodnoty, taková operace se provádí vrácením indexu prvku pole spolu s jeho hodnotou. Volající pak můžete použít tento index upravit hodnotu v samostatné volání metody. Volající však můžete také upravit index pro přístup a případně upravit jiné hodnoty pole.  

Následující příklad ukazuje, `FindNumber` jak by metoda mohla být přepsána po C# 7.3 pro použití místního přeřazení ref:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Tato druhá verze je efektivnější s delší sekvence ve scénářích, kde požadované číslo je blíže ke konci pole.

## <a name="see-also"></a>Viz také

- [klíčové slovo ref](../../language-reference/keywords/ref.md)
- [Zapisujte bezpečný efektivní kód](../../write-safe-efficient-code.md)
