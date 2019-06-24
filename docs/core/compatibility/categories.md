---
title: Zásadní změna kategorie – .NET Core
description: Další informace o způsobech, ve kterém jsou rozdělené rozbíjející změny v rozhraní .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: 68cd3580e80305e54b41610f05d939a6aff8b54d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307505"
---
# <a name="breaking-change-categories"></a>Zásadní změny kategorií

*Kompatibilita* odkazuje na možnost kompilace nebo spouštět kód na verzi implementace .NET jiného než ten, pomocí kterého byl původně vytvořen kód. Určité změny mohou ovlivnit kompatibilitu šest různými způsoby. [Jednotlivé typy změn, které jsou považovány za při vyhodnocování kompatibility](index.md) se dělí do pěti kategorií. 

## <a name="behavioral-change"></a>Změna chování

Chování změnit představuje změnu v chování člena. Tato změna může být externě viditelné (například metoda může vyvolat jinou výjimku), nebo to může představovat změněné implementace (například změnit tak, jak se počítá návratovou hodnotu, přidání nebo odebrání volání vnitřní metody nebo dokonce zlepšení výkonu).

Pokud nějaké změny jsou externě viditelné a upravit veřejný kontrakt typ, je snadné je vyhodnotit, protože ovlivňují binární kompatibilitu. Jsou mnohem obtížnější vyhodnotit; implementace změny v závislosti na povaze změny a četnost a vzorce použití rozhraní API dopad změny v rozsahu závažné až neškodného.  

## <a name="binary-compatibility"></a>Binární kompatibilita

Binární kompatibilita se týká schopnost příjemce rozhraní API pomocí rozhraní API na novější verzi bez opětovnou kompilaci. Tyto změny jako přidání metody nebo přidání nové implementace rozhraní na typ nemají vliv na binární kompatibilitu. Odebrání nebo změna veřejných podpisů sestavení tak, aby příjemci už mít přístup k stejné rozhraní vystavené sestavení však nemá vliv binární kompatibilitu. Říká změnu tohoto druhu *binární nekompatibilní změna*.

## <a name="source-compatibility"></a>Kompatibility zdroje

 Zdroj kompatibilita se týká schopnost stávajícím příjemcům rozhraní API znovu kompilovat s novější verzí bez nutnosti jakkoli měnit zdroj. A *zdrojů nekompatibilní změna* nastane, pokud se příjemce je potřeba změnit zdrojový kód, aby se sestavení úspěšně novější verzi rozhraní API.

## <a name="design-time-compatibility"></a>Kompatibility doby návrhu

Doby návrhu kompatibilita se týká zachování možnosti času návrhu ve verzích sady Visual Studio a jiných prostředích návrhu. Když to může zahrnovat chování nebo uživatelského rozhraní návrháře, nejdůležitější aspekty návrhu kompatibilita se týká kompatibilita projektu. Projekt nebo řešení musí být schopni otevřít a použít na novější verzi návrhové prostředí.

## <a name="backwards-compatibility"></a>Zpětné kompatibility

Zpětné kompatibility odkazuje na schopnost spotřebitel existující rozhraní API spustit s novou verzí při chovají stejným způsobem. Změny chování a změny v binární kompatibilitu vliv zpětné kompatibility. Pokud příjemce není možné spouštět nebo jak se bude chovat jinak při spuštění na novější verzi rozhraní API, rozhraní API je *zpětně kompatibilní*.

Změny, které ovlivňují zpětné kompatibility se důrazně nedoporučuje, protože vývojáři ve výchozím nastavení očekávat zpětné kompatibility v novějších verzích rozhraní API.

## <a name="forward-compatibility"></a>Dopředná kompatibilita

Dopředná kompatibilita popisuje schopnosti spotřebitel existující rozhraní API ke spuštění starší verze při vykazujících stejné chování. Pokud příjemce není možné spustit nebo se chová jinak se při spuštění na starší verzi rozhraní API, rozhraní API je *nekompatibilní dopředný*. 

Prakticky zachování dopředné kompatibility vylučuje všechny změny a dodatky verze, protože tyto změny brání příjemci, který cílí na novější verzi spuštění v rámci starší verze. Vývojáři očekávat, že příjemci, který závisí na novějších rozhraní API nemusí správně fungovat proti starší rozhraní API. 

Zachování dopředné kompatibility není cílem .NET Core.

## <a name="see-also"></a>Viz také:

[Vyzkoušejte nejnovější změny v rozhraní .NET Core](index.md)
