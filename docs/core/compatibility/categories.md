---
title: Přerušující kategorie změn – .NET Core
description: Přečtěte si o způsobech, kterými jsou zásadní změny zařazené do kategorií v .NET Core.
ms.date: 06/10/2019
ms.openlocfilehash: 32cf55dc3ba0b16bae8cfe6179211150b2c90e2c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343602"
---
# <a name="breaking-change-categories"></a>Kategorie změn způsobujících chyby

*Kompatibilita* odkazuje na schopnost zkompilovat nebo spustit kód ve verzi implementace rozhraní .NET, která je jiná než ta, se kterou byl kód původně vyvinut. Konkrétní změna může mít vliv na kompatibilitu šesti různými způsoby. [Jednotlivé druhy změn](index.md) , které jsou zváženy při hodnocení kompatibility, spadají do následujících kategorií:

- [Změna chování](#behavioral-change)
- [binární kompatibilita](#binary-compatibility)
- [Kompatibilita zdrojů](#source-compatibility)
- [Kompatibilita při návrhu](#design-time-compatibility)
- [zpětná kompatibilita](#backwards-compatibility)
- [dopředná kompatibilita](#forward-compatibility) (nejedná se o cíl .NET Core)

## <a name="behavioral-change"></a>Změna chování

Změna chování představuje změnu chování člena. Změna může být externě viditelná (například metoda může vyvolat jinou výjimku), nebo může představovat změněnou implementaci (například změnu způsobu, jakým se počítá návratová hodnota, přidání nebo odebrání volání vnitřní metody nebo dokonce i výrazné zlepšení výkonu.

Pokud jsou změny chování externě viditelné a upravují veřejné kontrakty typu, je možné je snadno vyhodnotit, protože mají vliv na binární kompatibilitu. Změny implementace jsou mnohem obtížně vyhodnoceny. v závislosti na povaze změny a četnosti a vzorcích použití rozhraní API může být dopad změny v rozsahu od závažných až po neškodného.

## <a name="binary-compatibility"></a>Binární kompatibilita

Binární kompatibilita odkazuje na schopnost příjemce rozhraní API používat rozhraní API v novější verzi bez nutnosti rekompilace. Takové změny jako přidání metod nebo přidání nové implementace rozhraní do typu neovlivňují binární kompatibilitu. Nicméně odebrání nebo změna veřejných podpisů sestavení, aby příjemci již nemohly přistupovat ke stejnému rozhraní zveřejněnému sestavením, ovlivní binární kompatibilitu. Změna tohoto druhu je označována jako *binární nekompatibilní změna*.

## <a name="source-compatibility"></a>Kompatibilita zdrojů

Kompatibilita zdrojů odkazuje na schopnost stávajících uživatelů rozhraní API znovu kompilovat v novější verzi bez jakýchkoli změn ve zdroji. Ke *zdroji nekompatibilní změny* dochází, když příjemce potřebuje upravit zdrojový kód, aby se vytvořil úspěšně na novější verzi rozhraní API.

## <a name="design-time-compatibility"></a>Kompatibilita při návrhu

Kompatibilita v době návrhu označuje zachování prostředí v době návrhu napříč verzemi sady Visual Studio a dalšími prostředími v době návrhu. I když to může zahrnovat chování nebo uživatelské rozhraní návrháře, nejdůležitější aspekt kompatibility při návrhu se týká kompatibility projektů. Projekt nebo řešení musí být možné otevřít a použít v novější verzi prostředí pro dobu návrhu.

## <a name="backwards-compatibility"></a>Zpětná kompatibilita

Zpětná kompatibilita znamená, že stávajícímu spotřebiteli rozhraní API může běžet na nové verzi, a přitom se chová stejným způsobem. Změny chování a změny binární kompatibility mají vliv na zpětnou kompatibilitu. Pokud se příjemce nedokáže při spuštění v novější verzi rozhraní API spustit jinak, je rozhraní API *zpětně nekompatibilní*.

Změny, které mají vliv na zpětnou kompatibilitu, se nedoporučuje, protože vývojáři očekávají zpětnou kompatibilitu v novějších verzích rozhraní API.

## <a name="forward-compatibility"></a>Dopředná kompatibilita

Dopředná kompatibilita odkazuje na schopnost existujícímu příjemci rozhraní API běžet na starší verzi a zároveň se projeví stejné chování. Pokud se příjemce nedokáže při spuštění na starší verzi rozhraní API spustit nebo se nechová jinak, rozhraní API je *předáno nekompatibilní*.

Udržování dopředné kompatibility prakticky vylučuje jakékoli změny nebo doplňky z verze na verzi, protože tyto změny brání příjemci, který cílí na novější verzi, ze spuštěné v dřívější verzi. Vývojáři očekávají, že příjemce, který spoléhá na novější rozhraní API, nemusí správně fungovat proti staršímu rozhraní API.

Udržování dopředné kompatibility není cílem rozhraní .NET Core.

## <a name="see-also"></a>Viz také:

- [Vyhodnotit poslední změny v .NET Core](index.md)
