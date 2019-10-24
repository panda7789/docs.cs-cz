---
title: Úvod do událostí
description: Přečtěte si o událostech v .NET Core a cílech návrhu jazyka pro události v tomto přehledu.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: b1fd2ebe2ae91b55c9179f280d8894f6b40ced9b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771920"
---
# <a name="introduction-to-events"></a>Úvod do událostí

[Předchozí](delegates-patterns.md)

Události jsou, jako delegáti, *pozdní vazba* mechanismu. Ve skutečnosti jsou události postaveny na jazykové podpoře pro delegáty.

Události představují způsob, jak objekt vysílat (všem zúčastněným součástem v systému), ke kterému došlo něco. Kterákoli další součást se může přihlásit k odběru události a upozornit, až se událost vyvolá.

V některém z vašich programování jste pravděpodobně použili události. Mnoho grafických systémů má model událostí, který by mohl nahlásit interakci uživatele. Tyto události by mohly vykazovat pohyb myši, stisknutí tlačítek a podobné interakce. To je jeden z nejběžnějších, ale určitě ne jediným scénářem, kdy se události používají.

Můžete definovat události, které by měly být vyvolány pro vaše třídy. Jedním z důležitých aspektů při práci s událostmi je, že pro konkrétní událost nemusí být registrován žádný objekt. Je nutné napsat kód tak, aby nevyvolávají události, pokud nejsou nakonfigurovány naslouchací procesy.

Přihlášení k odběru události také vytvoří propojení mezi dvěma objekty (zdrojem událostí a jímkou událostí). Je nutné zajistit, aby jímka událostí odhlásila odběr ze zdroje událostí, pokud již nebude zajímat události.

## <a name="design-goals-for-event-support"></a>Cíle návrhu pro podporu událostí

Návrh jazyka pro události, které cílí na tyto cíle.

Nejdřív povolte velmi minimální spojení mezi zdrojem událostí a jímkou událostí. Tyto dvě komponenty možná nebudou zapsány stejnou organizací a mohou být aktualizovány i na zcela různých plánech.

Za druhé by mělo být velmi jednoduché přihlásit se k odběru události a zrušit odběr této události.

A konečně, zdroje událostí by měly podporovat více předplatitelů událostí. Měla by také podporovat nepřipojené předplatitele událostí.

Můžete vidět, že cíle pro události jsou velmi podobné cílům pro delegáty.
To je důvod, proč je podpora jazyka událostí založená na podpoře jazyka delegáta.

## <a name="language-support-for-events"></a>Jazyková podpora pro události

Syntaxe pro definování událostí a přihlášení k odběru nebo odhlášení z událostí je rozšířením syntaxe pro delegáty.

Chcete-li definovat událost, kterou použijete klíčové slovo `event`:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Typ události (v tomto příkladu `EventHandler<FileListArgs>`) musí být typu delegát. Při deklaraci události byste měli dodržovat několik konvencí. Typ delegáta události obvykle má návratovou hodnotu void.
Deklarace události by měly být slovesem nebo slovesovou frází.
V případě, že událost nahlásí něco, co se stalo, použijte dřívější vhodné. K hlášení toho, co se stane, použijte stávající vhodné příkaz (například `Closing`). Často se pomocí současných vhodné značí, že vaše třída podporuje nějaký druh chování přizpůsobení. Jedním z nejběžnějších scénářů je podpora zrušení. Například událost `Closing` může zahrnovat argument, který by označoval, zda by měla operace zavřít pokračovat, nebo ne.  V jiných scénářích může volající změnit chování aktualizací vlastností argumentů události. Můžete vyvolat událost, která indikuje navrženou další akci, kterou algoritmus provede. Obslužná rutina události může pověřit jinou akci úpravou vlastností argumentu události.

Pokud chcete vyvolat událost, zavolejte obslužné rutiny události pomocí syntaxe vyvolání delegáta:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Jak je popsáno v části [Delegáti](delegates-patterns.md),?.
operátor usnadňuje zajištění, že se nepokoušíte vyvolat událost, pokud k této události neexistují žádní předplatitelé.
 
Přihlásíte se k odběru události pomocí operátoru `+=`:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

Metoda obslužné rutiny je obvykle prefix "on" následovaný názvem události, jak je uvedeno výše.

Pomocí operátoru `-=` se odhlásíte k odběru:

```csharp
fileLister.Progress -= onProgress;
```

Je důležité si uvědomit, že jsem deklaroval místní proměnnou pro výraz, který představuje obslužnou rutinu události. To zajišťuje, že zrušení odběru odebere obslužnou rutinu.
Pokud místo toho jste použili tělo výrazu lambda, pokoušíte se odebrat obslužnou rutinu, která nebyla nikdy připojena, což nedělá nic.

V dalším článku se dozvíte víc o typických vzorcích událostí a o různých variacích v tomto příkladu.

[Next](event-pattern.md)
