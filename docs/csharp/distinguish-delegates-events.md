---
title: Rozlišování delegátů a událostí
description: Přečtěte si rozdíl mezi delegáty a událostmi a kdy použít každou z těchto funkcí .NET Core.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: ff90af1d2b1a92f06eed58228f8e8ca5ff6b93ca
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037322"
---
# <a name="distinguishing-delegates-and-events"></a>Rozlišování delegátů a událostí

[Předchozí](modern-events.md)

Vývojáři, kteří jsou noví na platformě .NET Core, se často bojovat při rozhodování mezi návrhem založeným na `delegates` a návrhem na základě `events`. Toto je obtížné koncept, protože tyto dvě jazykové funkce jsou velmi podobné. Události jsou dokonce vytvořené pomocí jazykové podpory pro delegáty. 

Nabízí jak scénář pozdní vazby: umožňuje scénáře, kdy komponenta komunikuje, voláním metody, která je známá pouze za běhu. Obě tyto metody podporují jednu i více předplatitelů. Můžete to zjistit jako singlecast a podpora vícesměrového vysílání. Obě podporují podobnou syntaxi pro přidávání a odebírání obslužných rutin. Nakonec vyvolání události a volání delegáta používá přesně stejnou syntaxi volání metody. I oba podporují stejnou syntaxi metody `Invoke()` pro použití s operátorem `?.`.

U všech podobných funkcí je snadné mít problémy s určením, kdy se má použít.

## <a name="listening-to-events-is-optional"></a>Naslouchat události je nepovinné.

Nejdůležitějším aspektem při rozhodování o tom, kterou jazykovou funkci použít, je, zda musí být připojen předplatitel. Pokud váš kód musí volat kód dodaný předplatitelem, měli byste použít návrh založený na delegátech. Pokud váš kód může dokončit veškerou práci bez volání jakýchkoli předplatitelů, měli byste použít návrh založený na událostech. 

Vezměte v úvahu příklady vytvořené v této části. Kód, který jste vytvořili pomocí `List.Sort()`, musí být předána funkci Comparer, aby bylo možné správně seřadit prvky. Dotazy LINQ musí být dodány s delegáty, aby bylo možné určit, jaké prvky se mají vrátit. Používali jsme návrh sestavený s delegáty.

Zvažte `Progress` událost. Oznamuje průběh úkolu.
Úloha bude pokračovat bez ohledu na to, zda existují nějaké naslouchací procesy.
`FileSearcher` je další příklad. Pořád bude hledat a najít všechny hledané soubory, a to i v případě, že nejsou připojeni žádní Odběratelé.
Ovládací prvky uživatelského rozhraní i nadále fungují správně, i když neexistují předplatitelé, kteří na ně naslouchajíi událostmi. Používají návrhy založené na událostech.

## <a name="return-values-require-delegates"></a>Návratové hodnoty vyžadují delegáty.

Dalším aspektem je prototyp metody, který byste chtěli pro metodu delegáta. Jak jste viděli, delegáti, kteří používají pro události, mají návratový typ void. Viděli jste také, že jsou k dispozici idiomy k vytváření obslužných rutin událostí, které přecházejí informace zpět do zdrojů událostí prostřednictvím úprav vlastností objektu argumentu události. I když tyto idiomy fungují, nejsou tak přirozené jako vrácení hodnoty z metody.

Všimněte si, že tyto dvě heuristiky mohou být často k dispozici: Pokud vaše metoda delegáta vrací hodnotu, bude pravděpodobně ovlivněn algoritmus nějakým způsobem.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Naslouchací procesy událostí mají často delší životnost 

Jedná se o mírně slabší odůvodnění. Můžete ale zjistit, že návrhy založené na událostech jsou přirozenější, když zdroj události vyvolává události v dlouhou dobu. V mnoha systémech si můžete prohlédnout příklady pro ovládací prvky UX. Jakmile se přihlásíte k odběru události, může zdroj události vyvolat události po celou dobu životnosti programu.
(Odběr událostí můžete zrušit, pokud je už nepotřebujete.)

Na rozdíl od mnoha návrhů založených na delegátech, kde je delegát použit jako argument metody a delegát se nepoužívá poté, co metoda vrátí.

## <a name="evaluate-carefully"></a>Pečlivě vyhodnoťte

Výše uvedené požadavky nejsou pevná a rychlá pravidla. Místo toho představují pokyny, které vám mohou pomoci při rozhodování, která volba je nejvhodnější pro vaše konkrétní využití. Vzhledem k tomu, že jsou podobné, můžete dokonce prototypovat jak obojí, tak zvážit, který by byl přirozený pro práci s. Oba zpracovávají i pozdní spojování scénářů. Použijte ten, který komunikuje s návrhem nejlépe.
