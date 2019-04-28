---
title: Rozlišování delegátů a událostí
description: Informace o rozdílu mezi Delegáti a události a kdy se má používat každý z těchto funkcí .NET Core.
ms.date: 06/20/2016
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 2f9c26519d93314f4991829191723df5426b23b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646641"
---
# <a name="distinguishing-delegates-and-events"></a>Rozlišování delegátů a událostí

[Předchozí](modern-events.md)

Vývojáři, kteří jsou nové pro platformu .NET Core často zápasí při rozhodování mezi návrh na základě `delegates` a návrhu na základě `events`. To je koncept obtížné, protože dvě jazykové funkce jsou velmi podobné. Události se ještě sestavují jazykovou podporu pro delegáty. 

Obě nabízejí pozdní vazby scénář: umožňují scénáře, ve kterém komponentu komunikuje pomocí volání metody, který je znám pouze za běhu. Obě podporují odběratele jednotlivých i několika metod. Může být pro vás tato podpora označované jako singlecast a vícesměrového vysílání. Oba podporuje podobné syntaxi pro přidávání a odebírání obslužných rutin. Nakonec použijte vyvolání události a volání delegáta přesně stejné syntaxe volání metody. Dokonce i podporují stejné `Invoke()` syntaxe využívající metody pro použití se službou `?.` operátor.

Pomocí těchto podobnosti se snadno mít potíže s určením, kdy co použít.

## <a name="listening-to-events-is-optional"></a>Naslouchání události je nepovinné

Nejdůležitější význam při určování, kterou funkci používat jazyk je zda musí být připojené odběratele. Pokud musí váš kód volat kód poskytnutých odběratele, měli byste použít architekturu založenou na delegáty. Pokud váš kód může dokončit svou práci bez nutnosti volat všechny předplatitele, měli byste použít návrhu na základě událostí. 

Je třeba brát příklady vytvořené během této části. Kód, který jste vytvořili pomocí `List.Sort()` musí předávat funkci porovnávače aby bylo možné správně řadí prvky. Je potřeba zadat dotazů LINQ s delegáty aby bylo možné určit, které prvky k vrácení. Používá návrhu vytvořených pomocí delegátů.

Vezměte v úvahu `Progress` událostí. To zobrazuje průběh úlohy.
Úloha bude nadále pokračovat, jestli jsou všechny moduly pro naslouchání.
`FileSearcher` Je další příklad. Stále by Hledat a najít všechny soubory, které byly usilovaly, i s žádné odběratelů událostí, které jsou připojené.
Ovládací prvky uživatelského rozhraní i nadále fungovat správně, i když neexistují žádné předplatitele naslouchání události. Obě používají návrhy na základě událostí.

## <a name="return-values-require-delegates"></a>Návratové hodnoty vyžadují delegátů

Dalším aspektem je prototyp metody, které je vhodné pro vaše metody delegáta. Jak už víte, delegáty používané pro všechny události mají návratový typ void. Také jste viděli, že jsou idiomy pro vytváření obslužných rutin událostí, které předávají informace zpět do zdroje událostí prostřednictvím úpravy vlastností objektu argumentu události. I když tyto idiomy fungují, nejsou jako přirozené jako návratová hodnota z metody.

Všimněte si, že tyto dvě heuristickými metodami může často vyskytovat současně: Pokud vaše metody delegáta vrací hodnotu, bude pravděpodobně ovlivňovat algoritmus nějakým způsobem.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Naslouchacích procesů událostí často mají delší životnost 

Toto je mírně slabší odůvodnění. Však můžete zjistit, že jsou založené na událostech návrhy přirozenější při zdroje událostí se vyvolání události po dlouhou dobu. Můžete zobrazit příklady pro ovládací prvky uživatelského rozhraní na více systémů. Jakmile se přihlásíte k odběru události, zdroj události může vyvolat události v rámci životnosti programu.
(Můžete zrušit odběr události, kdy je už nepotřebujete.)

Oproti, který mnoho delegáta návrhy, kde delegáta se používá jako argument pro metodu a delegáta se nepoužívá po návratu tato metoda.

## <a name="evaluate-carefully"></a>Pečlivě vyhodnotit

Výše uvedené požadavky nejsou pevné a rychlé pravidla. Místo toho které představují pokyny, které vám můžou pomoct rozhodnout, které je nejvhodnější pro vaše konkrétní použití. Protože jsou podobné, můžete dokonce prototypu i a zvažte, který bude přirozenější pro práci s. Oba dobře zvládnout pozdní vazby scénáře. Použijte ten, který komunikuje návrhu nejvhodnější.
