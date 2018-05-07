---
title: Úvod k událostem
description: Další informace o události v .NET Core a naše cíle návrhu jazyk pro události se v tomto přehledu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 2a2230ea5fba1b0cd5b13319677965e7a776549e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-events"></a>Úvod k událostem

[Předchozí](delegates-patterns.md)

Události jsou jako delegáti, *pozdní vazby* mechanismus. Ve skutečnosti události jsou postavené na jazyková podpora pro delegáti.

Události jsou způsob, jak k objektu pro všesměrové vysílání (pro všechny dotčené komponenty v systému), že něco došlo. Všechny ostatní součásti, které se mohou přihlásit k události a být upozorněni, když je aktivována událost.

Pravděpodobně jste použili události v některé z vaší programování. Mnoho grafické systémy mají model událostí k interakci s uživatelem sestavy. Tyto události by sestavy pohybu myši, stisknutí tlačítek a podobné interakce. Který je jedním nejběžnější, ale určitě ne jediný scénář, kdy se používá události.

Můžete definovat události, které by měl být aktivována pro vaše třídy. Při práci s událostmi je, že existuje jedna důležitý aspekt nemusí být libovolný objekt zaregistrovat pro určitá událost. Musíte napsat kód tak, aby nevyvolá události při žádné moduly pro naslouchání jsou nakonfigurované.

Odběr pro událost vytvoří také párování mezi dvěma objekty (zdroj události a jímky událostí). Je potřeba zajistit, že jímky událostí odhlásí zdroj událostí, když už máte zájem o události.

## <a name="design-goals-for-event-support"></a>Cíle návrhu pro podporu událostí

Návrh jazyk pro události cílem těchto cílů.

Nejprve povolte minimálními párování mezi zdroje událostí a jímky událostí. Tyto dvě součásti nemusí být zapsané ve stejné organizaci a může být aktualizován i na uvidíte úplně jiné plány.

Za druhé musí být velmi jednoduché k odběru události a zrušení této stejnou událost odběru.

A nakonec zdroje událostí by měly podporovat více odběrateli událostí. Také by měly podporovat, s žádné události odběratele připojen.

Uvidíte, že cíle pro události jsou velmi podobné cíle pro delegáti.
To je důvod, proč jazyková podpora událostí je založen na jazyková podpora delegáta.

## <a name="language-support-for-events"></a>Jazyková podpora pro události

Syntaxe pro definování události a přihlášení k odběru nebo Odhlašujete události je rozšíření syntaxe delegáti.

K definování událost použijete `event` – klíčové slovo:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Typ události (`EventHandler<FileListArgs>` v tomto příkladu), musí být typu delegáta. Existuje několik smluv, které byste měli postupovat při deklarování událost. Obvykle má tento typ delegáta události void vrátit.
Deklarace událostí musí být operaci nebo frázi operaci.
Pokud událost sestavy něco, co se stalo, použijte minulost (jako v tomto příkladu). Použít operaci přítomném (například `Closing`) tak, aby odesílaly něco, co dojde. Pomocí přítomném často označuje, že třídě podporuje nějaký druh přizpůsobení chování. Jeden z nejběžnějších scénářů je podpora zrušení. Například `Closing` události může zahrnovat argument, který může naznačovat, pokud by měl zavřít operace pokračovat, nebo ne.  V jiných scénářích může povolit volající chcete upravit chování pomocí aktualizace vlastností argumenty událostí. Může vyvolat událost označující navrhované další akci, kterou bude trvat algoritmu. Obslužné rutiny události může vyžádá různé akce úpravou vlastnosti argumentu události.

Když chcete k vyvolání události, volání obslužných rutin událostí pomocí syntaxe vyvolání delegáta:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Jak je popsáno v části na [delegáti](delegates-patterns.md),?.
operátor usnadňuje Ujistěte se, že nebude pokoušet o vyvolat událost, pokud nejsou žádné odběratele, kteří mají tuto událost.
 
Přihlášení k odběru události pomocí `+=` operátor:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

Metoda obslužná rutina obvykle představuje předponu "Na" následuje název události, jako v příkladu nahoře.

Odhlásit pomocí `-=` operátor:

```csharp
lister.Progress -= onProgress;
```

Je důležité si uvědomit, že I deklarovaný místní proměnné pro výraz, který představuje obslužné rutiny události. Který zajišťuje odebere unsubscribe obslužná rutina.
Pokud jste použili tělo výrazu lambda, se pokoušíte odebrat obslužnou rutinu, která nikdy nebyl přidán, který se nic nestane.

V další článek budete Další informace o typických událostí vzory a různých změn v tomto příkladu.

[Next](event-pattern.md)
