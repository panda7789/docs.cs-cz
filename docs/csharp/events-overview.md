---
title: Úvod do událostí
description: Další informace o událostech v .NET Core a našich cílech návrhu jazyka pro události v tomto přehledu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 4e660f85eecfd5668919baf21a0d26f858faf5a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146111"
---
# <a name="introduction-to-events"></a>Úvod do událostí

[Předchozí](delegates-patterns.md)

Události jsou, stejně jako delegáti, *pozdní vazebný* mechanismus. Ve skutečnosti jsou události postaveny na jazykové podpoře delegátů.

Události jsou způsob, jak objekt vysílat (pro všechny zúčastněné součásti v systému), že se něco stalo. K odběru události se může přihlásit jakákoli jiná součást a být upozorněna, když je vyvolána událost.

Pravděpodobně jste použili události v některých vašich programů. Mnoho grafických systémů má model událostí pro hlášení interakce uživatele. Tyto události by hlásit pohyb myši, stisknutí tlačítka a podobné interakce. To je jeden z nejběžnějších, ale rozhodně ne jediný scénář, kde se používají události.

Můžete definovat události, které by měly být vyvolány pro vaše třídy. Jedním z důležitých úvah při práci s událostmi je, že nemusí být žádný objekt registrován pro konkrétní událost. Je nutné napsat kód tak, aby nevyvolá události, když jsou nakonfigurovány žádné naslouchací procesy.

Přihlášení k odběru události také vytvoří spojení mezi dvěma objekty (zdroj události a jímka událostí). Je třeba zajistit, že jímky události odhlásí ze zdroje událostí, když již zájem o události.

## <a name="design-goals-for-event-support"></a>Cíle návrhu pro podporu událostí

Návrh jazyka pro události cílí na tyto cíle:

- Povolte velmi minimální párování mezi zdrojem událostí a jímkou událostí. Tyto dvě součásti nemusí být napsány stejnou organizací a mohou být dokonce aktualizovány v úplně odlišných plánech.

- Mělo by být velmi jednoduché přihlásit se k odběru události, a odhlásit se z tésamé události.

- Zdroje událostí by měly podporovat více odběratelů událostí. Měla by také podporovat bez připojených odběratelů událostí.

Můžete vidět, že cíle pro události jsou velmi podobné cíle pro delegáty.
Proto je podpora jazyka událostí postavena na jazykové podpoře delegáta.

## <a name="language-support-for-events"></a>Jazyková podpora pro akce

Syntaxe pro definování událostí a přihlášení nebo odhlášení z událostí je rozšíření syntaxe pro delegáty.

Chcete-li definovat událost, kterou použijete `event` klíčové slovo:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Typ události (`EventHandler<FileListArgs>` v tomto příkladu) musí být typ delegáta. Existuje několik konvencí, které byste měli dodržovat při deklarování události. Typ delegáta události má obvykle neplatné vrácení.
Deklarace událostí by měla být sloveso nebo slovesná fráze.
Pokud událost nahlásí něco, co se stalo, použijte minulý čas. Pomocí aktuálního slovesa `Closing`(například) nahlaste něco, co se má stát. Často pomocí přítomný čas označuje, že vaše třída podporuje nějaký druh přizpůsobení chování. Jedním z nejběžnějších scénářů je podpora zrušení. `Closing` Událost může například obsahovat argument, který by naznačoval, zda má operace zavřít pokračovat, nebo ne.  Jiné scénáře mohou umožnit volajícím změnit chování aktualizací vlastností argumentů události. Můžete vyvolat událost označující navrhovanou další akci, kterou algoritmus provede. Obslužná rutina události může nařídit jinou akci změnou vlastností argumentu události.

Pokud chcete vyvolat událost, volání obslužné rutiny události pomocí syntaxe vyvolání delegáta:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Jak je popsáno v sekci o [delegátech](delegates-patterns.md), ?.
operátor usnadňuje zajistit, že se nepokusíte vyvolat událost, pokud neexistují žádné předplatitele této události.

K odběru události se `+=` přihlásíte pomocí operátoru:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

Metoda obslužné rutiny má obvykle předponu "On" následovanou názvem události, jak je uvedeno výše.

Z odběru se `-=` odhlásíte pomocí operátora:

```csharp
fileLister.Progress -= onProgress;
```

Je důležité si uvědomit, že jsem deklaroval místní proměnnou pro výraz, který představuje obslužnou rutinu události. Tím zajistíte, že odhlášení odebere obslužnou rutinu.
Pokud jste místo toho použili tělo výrazu lambda, pokoušíte se odebrat obslužnou rutinu, která nebyla nikdy připojena, což neprovede nic.

V dalším článku se dozvíte více o vzorcích typických událostí a různých variantách v tomto příkladu.

[Další](event-pattern.md)
