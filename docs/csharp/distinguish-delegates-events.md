---
title: Rozlišovací Delegáti a události
description: Informace o rozdílu mezi Delegáti a události a při použití každé z těchto funkcí .NET Core.
ms.date: 06/20/2016
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 2f9c26519d93314f4991829191723df5426b23b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="distinguishing-delegates-and-events"></a>Rozlišovací Delegáti a události

[Předchozí](modern-events.md)

Vývojáři, kteří jsou často nové pro platformu .NET Core potýkat s tím zajistily při rozhodování mezi návrh na základě `delegates` a návrh na základě `events`. To je obtížné koncept, protože jsou velmi podobné funkce dvě jazyka. Události jsou i vytvořená s využitím jazyková podpora pro delegáti. 

Obě nabízejí scénáři pozdní vazby: umožňují scénáře, kde součást komunikuje pomocí volání metody, které je známé pouze za běhu. Obě podporovat odběratele jednotlivé a vícenásobné metody. Můžete zjistit, tato podpora označují jako singlecast a vícesměrového vysílání. Obě podporují podobné syntaxe pro přidávání a odebírání obslužné rutiny. Nakonec vyvolání události a volání metody delegáta pomocí přesně stejnou syntaxi volání metody. Dokonce i podporují stejné `Invoke()` syntaxe využívající metody pro použití s `?.` operátor.

Pomocí těchto podobnosti je snadné potíží s určením, kdy se má použít, který.

## <a name="listening-to-events-is-optional"></a>Naslouchá událostem je volitelné

Většina důležitý aspekt při určení, kterou funkci používat jazyk je zda musí být připojené odběratele. Pokud váš kód musí volat kód poskytl odběratele, měli byste použít návrh podle delegáti. Pokud váš kód dokončení všech práce bez volání všechny odběratele, měli byste použít návrh na základě událostí. 

Je třeba brát příklady vytvořené během této části. Kód, který jste vytvořili pomocí `List.Sort()` musí mít funkci porovnávače aby bylo možné správně řazení elementů. Je nutné zadat dotazů LINQ s delegáti Chcete-li určit, které prvky vrátit. Jak použít návrh vytvořené s nástroji delegáti.

Vezměte v úvahu `Progress` událostí. Ho hlásí průběh úlohy.
Úloha i nadále pokračovat, zda jsou všechny moduly pro naslouchání.
`FileSearcher` Je další příklad. By stále Hledat a najít všechny soubory, které byly žádá o, i když žádné události odběratele připojen.
Ovládací prvky UX i nadále fungovat správně, i když neexistují žádné odběratele naslouchání událostem. Obě používají návrhy na základě událostí.

## <a name="return-values-require-delegates"></a>Návratové hodnoty vyžadují delegáti

Je potřeba zamyslet se metoda prototyp, které je vhodnější pro metodu delegáta. Protože jste se seznámili, delegáty použít pro všechny události mít typ vrácené hodnoty void. Také jste viděli, že jsou idioms pro vytváření obslužných rutin událostí, které předávají informace zpět do zdroje událostí prostřednictvím Úprava vlastností objektu argumentu události. I když tyto idioms fungují, nejsou jako přirozené jako vrací hodnotu z metody.

Všimněte si, že tyto dvě heuristiky může často i být k dispozici: Pokud metodu delegáta vrátí hodnotu, ovlivní pravděpodobně algoritmus nějakým způsobem.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Naslouchacích procesů událostí mají často delší životnosti 

Toto je mírně nižší zarovnání do bloku. Však můžete zjistit, že založený na událostech návrzích přirozenější při zdroj události bude vyvolání události po dlouhou dobu. Zobrazí se to příklady pro ovládací prvky UX na mnoha systémy. Jakmile se přihlásíte k odběru události, zdroj události může vyvolat události po celou dobu programu.
(Můžete odhlášení odběru událostí, pokud je už nepotřebujete.)

Oproti který řada na základě delegáta návrhů, kde delegáta se používá jako argument pro metodu, a delegát není po návratu této metody.

## <a name="evaluate-carefully"></a>Pečlivě vyhodnotit

Výše uvedené požadavky nejsou pravidla pevný a rychlé. Místo toho představují pokyny, které vám pomohou rozhodnout, které možnosti je vhodné pro vaše konkrétní použití. Protože jsou podobné, můžete dokonce i prototypu obou a zvažte, který bude pracovat s více fyzických. Obě dobře zpracovávat scénáře pozdní vazbu. Použijte ten, který komunikuje návrhu nejvhodnější.
