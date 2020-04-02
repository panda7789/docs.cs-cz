---
title: Rozlišování delegátů a událostí
description: Zjistěte rozdíl mezi delegáty a událostmi a kdy použít každou z těchto funkcí .NET Core.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 4179330fe5e88da5d5034a150a057f63e31b178b
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588263"
---
# <a name="distinguishing-delegates-and-events"></a>Rozlišování delegátů a událostí

[Předchozí](modern-events.md)

Vývojáři, kteří jsou na platformě .NET Core noví, `delegates` se často `events`potýkají s problémy při rozhodování mezi návrhem založeným na návrhu a návrhem založeným na . Jedná se o obtížný koncept, protože dva jazykové funkce jsou velmi podobné. Události jsou dokonce sestaveny pomocí jazykové podpory pro delegáty.

Oba nabízejí scénář pozdní vazby: umožňují scénáře, kde komponenta komunikuje voláním metody, která je známa pouze za běhu. Oba podporují metody jednoho a více odběratelů. Může se vám to líbit jako podpora jednoho vysílání a vícesměrového vysílání. Oba podporují podobnou syntaxi pro přidávání a odebírání obslužných rutin. Nakonec vyvolání události a volání delegáta použít přesně stejnou syntaxi volání metody. I oba podporují `Invoke()` stejnou syntaxi metody `?.` pro použití s operátorem.

Se všemi těmito podobnostmi, je snadné mít potíže s určením, kdy použít, které.

## <a name="listening-to-events-is-optional"></a>Naslouchání událostem je volitelné

Nejdůležitější mne v úvahu při určování, který jazyk funkce použít, je zda musí být připojené odběratel. Pokud váš kód musí volat kód dodaný předplatitelem, měli byste použít návrh založený na delegátech. Pokud váš kód může dokončit všechny své práce bez volání odběratele, měli byste použít návrh založený na událostech.

Vezměme si příklady vytvořené během této části. Kód, který `List.Sort()` jste vytvořili pomocí musí být poskytnuta funkce porovnávání, aby bylo možné správně třídit prvky. Linq dotazy musí být dodány s delegáty, aby bylo možné určit, jaké prvky vrátit. Oba používali návrh vytvořený s delegáty.

Vezměme `Progress` si událost. Hlásí průběh úkolu.
Úloha pokračuje pokračovat bez ohledu na to, zda existují naslouchací procesy.
Další `FileSearcher` příklad je. To by ještě hledat a najít všechny soubory, které byly vyhledávány, a to i bez události účastníků připojen.
Ovládací prvky uživatelského rozhraní stále fungují správně, i když neexistují žádní odběratelé, kteří poslouchají události. Oba používají návrhy založené na událostech.

## <a name="return-values-require-delegates"></a>Návratové hodnoty vyžadují delegáty

Dalším aspektem je prototyp metody, který byste chtěli pro metodu delegáta. Jak jste viděli, delegáti používané pro události všechny mají prázdný návratový typ. Také jste viděli, že existují idiomy k vytvoření obslužné rutiny událostí, které předávají informace zpět zdrojům událostí prostřednictvím úpravy vlastností objektu argumentu události. Zatímco tyto idiomy fungují, nejsou tak přirozené jako vrácení hodnoty z metody.

Všimněte si, že tyto dvě heuristiky mohou být často oba přítomny: Pokud vaše metoda delegáta vrátí hodnotu, bude pravděpodobně nějakým způsobem ovlivnit algoritmus.

## <a name="events-have-private-invocation"></a>Události mají soukromé vyvolání

Jiné třídy než ve kterém je událost obsažena můžete pouze přidat a odebrat posluchače událostí; pouze třída obsahující událost může vyvolat událost. Události jsou obvykle členy veřejné třídy.
Pro srovnání delegáti jsou často předávané jako parametry a uloženy jako soukromé členy třídy, pokud jsou uloženy vůbec.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Posluchači událostí mají často delší životnost

To je o něco slabší ospravedlnění. Můžete však zjistit, že návrhy založené na událostech jsou přirozenější, když zdroj události bude vyvolávat události po dlouhou dobu. Můžete zobrazit příklady tohoto pro ovládací prvky uživatelského rozhraní v mnoha systémech. Jakmile se přihlásíte k odběru události, zdroj události může vyvolat události po celou dobu životnosti programu.
(Z odběru se můžete odhlásit, když je již nepotřebujete.)

Kontrast, že s mnoha návrhy založené na delegáta, kde delegát se používá jako argument k metodě a delegát se nepoužívá po této metody vrátí.

## <a name="evaluate-carefully"></a>Pečlivě vyhodnoťte

Výše uvedené úvahy nejsou tvrdá a rychlá pravidla. Místo toho představují pokyny, které vám pomohou rozhodnout, která volba je nejvhodnější pro konkrétní použití. Vzhledem k tomu, že jsou podobné, můžete dokonce prototyp oba, a zvážit, které by bylo přirozenější pracovat. Oba dobře zvládnou pozdní vazebné scénáře. Použijte ten, který komunikuje váš návrh nejlepší.
