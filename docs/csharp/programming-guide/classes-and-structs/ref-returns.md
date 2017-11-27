---
title: "Návratové hodnoty REF a ref lokální proměnné (Průvodce C#)"
description: "Zjistěte, jak definovat a použijte ref vrátit a místní hodnoty ref"
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 18cf7a4b-29f0-4b14-85b8-80af754aabd8
ms.openlocfilehash: 1d8fb092b578602b5d4f791a3fd14f47dfae1ba6
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="ref-returns-and-ref-locals"></a>Vrátí REF a místní hodnoty ref

Od verze jazyka C# 7, C# podporuje odkaz návratové hodnoty (ref vrátí). Odkaz vrátí hodnotu umožňuje metodu pro odkaz na objekt, nikoli hodnotu, vrátí zpět do volající. Volající může zvolte zacházet s vráceného objektu vrácena jako v případě, že byly vráceny, hodnotou nebo odkazem. Hodnota vrácená odkazem, volající zpracovává jako referenční místo místní ref je hodnota.

## <a name="what-is-a-reference-return-value"></a>Co je návratovou hodnotu odkazu?

Většina vývojářů obeznámeni s předáním argumentu volané metodě *odkazem*. Seznam obsahuje hodnotu předanou odkaz a veškeré změny provedené zavolat metodu na jeho hodnotu argumentu zavolat metodu jsou vrácen volajícímu. A *odkazovat návratovou hodnotu* protikladem:

- Vrácená hodnota zavolat metodu, místo, předaný argument je odkaz.

- Volající, nikoli zavolat metodu, můžete upravit hodnota vrácená metodou.

- Místo úpravy k argumentu, které se projeví v stav objektu na volajícího se projeví změny návratovou hodnotu metody volajícího ve stavu objektu, jehož metoda byla volána.

Návratové hodnoty odkaz můžete vytvořit kompaktnější kódu, jakož i povolit vystavit pouze jednotlivé datové položky, jako je například k elementu pole, které jsou důležité pro volající objekt. Tím se snižuje pravděpodobnost, že volající nechtěně změnit stav objektu.

Existují některá omezení na hodnotu, která metoda může vrátit jako návratová hodnota odkazu. Mezi ně patří:

- Návratová hodnota nemůže být `void`. Probíhá pokus o definovat metodu s `void` návratovou hodnotu odkazu vygeneruje Chyba kompilátoru CS1547, "– klíčové slovo 'void' nelze v tomto kontextu použít."
 
- Návratová hodnota nemůže být místní proměnné v metodu, která vrátí. musí mít obor, který je mimo metodu, která vrátí ji. Dá se instanci nebo statické pole třídy, nebo může být argument předaný metodě. Probíhá pokus o vraťte se generuje chyba kompilátoru CS8168, místní proměnné "nemůže vrátit místní 'obj' odkazem protože se nejedná o místní ref."

- Návratová hodnota nemůže být `null`. Probíhá pokus o vrátit `null` vygeneruje Chyba kompilátoru CS8156, "výraz nelze použít v tomto kontextu, protože nemusí být vrátil odkazem."

   Pokud metoda s návratovým ref musí vrátit hodnotu null, můžete buď vrátit hodnotu null (bez instancí) pro typ odkaz nebo [typ s možnou hodnotou Null](../nullable-types/index.md) pro typ hodnoty.
 
- Návratová hodnota nemůže být konstanta, člena výčtu nebo vlastnost `class` nebo `struct`. Na tyto vrácení vygeneruje Chyba kompilátoru CS8156, "výraz nelze použít v tomto kontextu, protože nemusí být vrátil odkazem."

Kromě toho protože asynchronní metodu může vrátit před dokončením provádění, zatímco vrácená hodnota je stále neznámé, odkaz návratové hodnoty nejsou povoleny u asynchronní metody.
 
## <a name="defining-a-ref-return-value"></a>Definice návratové hodnoty ref

Definice návratové hodnoty ref přidáním [ref](../../language-reference/keywords/ref.md) – klíčové slovo k návratový typ podpis metody. Například následující podpis znamená, že `GetContactInformation` vrátí odkaz na vlastnost `Person` objekt, který má volající:

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

Kromě toho název objektu vrácené každou [vrátit](../../language-reference/keywords/return.md) příkaz v těle metoda musí předcházet [ref](../../language-reference/keywords/ref.md) – klíčové slovo. Například následující `return` příkaz vrátí `Person` objekt s názvem `p` odkazem:

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>Využívání návratové hodnoty ref

Volající může zpracovat ref návratovou hodnotu v některém ze dvou způsobů:

- Jako obyčejnou hodnota vrácená metodou hodnotou. Volající můžete ignorovat, že návratová hodnota je odkaz návratovou hodnotu. V takovém případě změny provedené v hodnoty vrácené volání metody, které se neprojeví v stav volané typu. Pokud typ hodnoty vrácené hodnoty, všechny změny hodnoty vrácené volání metody, které se neprojeví v stav volané typu.

- Jako referenci vrátíte hodnotu. Volající musí definovat proměnnou, ke kterému je přiřazen návratovou hodnotu odkazu jako [ref místní](#ref-local), a všechny změny na hodnoty vrácené volání metody, které se projeví ve stavu volané typu. 

## <a name="ref-locals"></a>Místní hodnoty REF

Pro zpracování návratovou hodnotu odkazu jako odkaz, volající musí deklarovat hodnota, která má být *ref místní* pomocí `ref` – klíčové slovo. Například pokud je hodnota vrácené `Person.GetContactInfomation` metoda má být využívány jako odkaz, nikoli hodnotu, volání metody, které se zobrazí jako:

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Všimněte si, že `ref` – klíčové slovo se používá i před místní deklarace proměnné *a* před voláním metody. Nepodařilo se současně obsahovat `ref` klíčová slova v deklarace proměnné a přiřazení má za následek chyby kompilátoru CS8172, "nelze inicializovat proměnnou podle odkazu s hodnotou." 
 
Následné změny `Person` objekt vrácený metodou, se projeví v `contacts` objektu.

Pokud `p` není definován jako místní ref pomocí `ref` – klíčové slovo, všechny změny provedené v `p` volajícího se neprojeví v `contacts` objektu.
 
## <a name="ref-returns-and-ref-locals-an-example"></a>Vrátí REF a místní hodnoty ref: příklad

V následujícím příkladu definuje `NumberStore` třídu, která ukládá pole celočíselné hodnoty. `FindNumber` Metoda vrátí odkaz na číslo, kterým je větší než nebo rovná počtu předat jako argument. Pokud žádné číslo větší než nebo rovna hodnotě argument, metoda vrátí číslo v indexu 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

Následující příklad volání `NumberStore.FindNumber` metoda načíst první hodnotu, která je větší než nebo rovný 16. Volající pak zdvojnásobí hodnota vrácená metodou. Jak ukazuje výstup z příkladu, tato změna se projeví v hodnotě pole elementů `NumberStore` instance.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

Bez podpory pro odkaz vrácené hodnoty tyto operace obvykle provádí vrácení index pole element společně s jeho hodnotu. Volající potom můžete pomocí tohoto indexu změňte hodnotu v samostatné metodě volání. Volající však můžete také upravit index pro přístup a které by mohly mít úpravy ostatní hodnoty pole.  
 
## <a name="see-also"></a>Viz také

[REF – klíčové slovo](../../language-reference/keywords/ref.md)
