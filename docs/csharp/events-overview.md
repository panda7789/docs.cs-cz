---
title: Úvod do událostí
description: Další informace o události v rozhraní .NET Core a naše cíle návrhu jazyk pro události v tomto přehledu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 9f14954dd2e8aeacf3c5ae70a9e891ad11a6f0d7
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365300"
---
# <a name="introduction-to-events"></a>Úvod do událostí

[Předchozí](delegates-patterns.md)

Události jsou podobné delegátů, *pozdní vazby* mechanismus. Události ve skutečnosti jsou postavené na podporu jazyka pro delegáty.

Události jsou způsob, jakým objekt vysílání (pro všechny dotčené součásti v systému), že něco se stalo. Jakékoli další součásti můžete přihlásit k odběru události a upozorněni, když je vyvolána událost.

Pravděpodobně jste použili události v některé z vašich programování. Řada grafických systémů mají model událostí na interakci uživatele sestavy. Tyto události zasílat zprávy pohybu myši, stisknutí tlačítek a podobné interakce. Který je jedním z nejčastěji používaných, ale určitě ne pouze scénář, kde události se používají.

Události, které by měla být zvýšena můžete definovat pro své třídy. Jedním z důležitých faktorů při práci s událostmi je, že existuje, nemusí být libovolný objekt registrovaný při určité události. Psaní kódu tak, aby nevyvolával události, kdy žádný naslouchací procesy jsou nakonfigurované.

Přihlášení k odběru události vytvoří také párování mezi dvěma objekty (zdroj události a jímky událostí). Je potřeba zajistit, že ruší registraci stok události ze zdroje události, když už uvažujete o události.

## <a name="design-goals-for-event-support"></a>Cíle návrhu pro podporu událostí

Návrh jazyka pro události, zaměřuje těchto cílů.

Nejprve povolte minimální párování mezi zdrojem události a jímku událostí. Tyto dvě součásti nemusí napsané ve stejné organizaci a může aktualizovat i na úplně jiné plány.

Za druhé měla by být velmi jednoduché přihlásit odběr události a zrušit odběr této stejné události.

A nakonec zdroje událostí by měly podporovat několik předplatitelů události. Taky by měly podporovat, s žádné odběratelů událostí, které jsou připojené.

Uvidíte, že cíle pro události jsou velmi podobné cíle pro delegáty.
To je důvod, proč události jazykovou podporu je postavená na jazykové podpoře delegáta.

## <a name="language-support-for-events"></a>Podpora jazyků pro události

Syntaxe pro definování události a přihlášení k odběru nebo odpovězeno události je rozšířením syntaxe pro delegáty.

Chcete-li definovat událost použijete `event` – klíčové slovo:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Typ události (`EventHandler<FileListArgs>` v tomto příkladu) musí být typu delegáta. Existuje několik smluv, které byste měli postupovat při deklaraci události. Typ delegáta události obvykle má návratový typ void.
Deklarace událostí by měla být sloveso nebo v operaci frázi.
Pokud událost ohlásí něco, co se stalo, použijte minulý čas (jako v tomto příkladu). Použijte přítomný čas operací (například `Closing`) na něco, co se přiblíží sestavu. Pomocí přítomném často, označuje, že vaše třída podporuje nějaký druh přizpůsobení chování. Jedním z nejběžnějších scénářů je podporují zrušení. Například `Closing` událostí může obsahovat argument, který by označoval, pokud by měla operaci zavření pokračovat, nebo ne.  V jiných scénářích může umožnit tak volajícím k úpravě chování pomocí aktualizace vlastností argumentů události. Může vyvolat událost označující navrhované další akci, bude trvat algoritmus. Obslužná rutina události může ukládat povinnost různé akce úpravou vlastností argumentu události.

Pokud chcete vyvolat událost, volání obslužných rutin událostí pomocí syntaxe volání delegáta:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Jak je popsáno v části na [delegáti](delegates-patterns.md),?.
operátor usnadňuje Ujistěte se, že nebude pokoušet o vyvolat událost, když nejsou žádná Odběratelé této události.
 
Se přihlásíte k odběru události pomocí `+=` operátor:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += onProgress;
```

Metoda obslužné rutiny obvykle je předpona "Na" za nímž následuje název události, jak je znázorněno výše.

Zrušit pomocí `-=` operátor:

```csharp
lister.Progress -= onProgress;
```

Je důležité si uvědomit, že mám deklarovat lokální proměnná pro výraz, který představuje obslužnou rutinu události. Zajistí se tak odebere unsubscribe obslužné rutiny.
Pokud jste použili hlavní část výrazu lambda, se pokoušíte odebrat obslužnou rutinu, která nikdy byla přiřazena, který nemá žádný účinek.

V následujícím článku budete Další informace o vzory typické událostí a různých změn v tomto příkladu.

[Next](event-pattern.md)
