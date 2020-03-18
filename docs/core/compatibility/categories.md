---
title: Kategorie změn způsobujících chyby
description: Informace o způsobech, ve kterých jsou změny rozdělení zařazeny do kategorií v .NET Core.
ms.date: 06/10/2019
ms.openlocfilehash: b273ebbb82da803cde66ea34760aa1779c6c1ca5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093042"
---
# <a name="breaking-change-categories"></a>Kategorie změn způsobujících chyby

*Kompatibilita* odkazuje na schopnost zkompilovat nebo spustit kód ve verzi implementace .NET než ten, se kterým byl kód původně vyvinut. Určitá změna může ovlivnit kompatibilitu šesti různými způsoby. [Jednotlivé druhy změn,](index.md) které jsou považovány při hodnocení kompatibility spadají do následujících kategorií:

- [změna chování](#behavioral-change)
- [binární kompatibilita](#binary-compatibility)
- [kompatibilita zdroje](#source-compatibility)
- [kompatibilita v době návrhu](#design-time-compatibility)
- [zpětná kompatibilita](#backwards-compatibility)
- [dopředná kompatibilita](#forward-compatibility) (není cílem .NET Core)

## <a name="behavioral-change"></a>Změna chování

Změna chování představuje změnu chování člena. Změna může být externě viditelná (například metoda může vyvolat jinou výjimku) nebo může představovat změněnou implementaci (například změnu způsobu výpočtu návratové hodnoty, přidání nebo odebrání interních volání metod nebo dokonce významné zlepšení výkonnosti).

Pokud jsou změny chování externě viditelné a upravují veřejnou smlouvu typu, lze je snadno vyhodnotit, protože ovlivňují binární kompatibilitu. Změny implementace je mnohem obtížnější vyhodnotit; v závislosti na povaze změny a četnosti a vzorcích používání rozhraní API se dopad změny může pohybovat od závažných po neškodné.

## <a name="binary-compatibility"></a>Binární kompatibilita

Binární kompatibilita odkazuje na schopnost příjemce rozhraní API používat rozhraní API v novější verzi bez rekompilace. Takové změny, jako je přidání metod nebo přidání nové implementace rozhraní do typu nemají vliv na binární kompatibilitu. Odebrání nebo změna veřejné podpisy sestavení tak, aby spotřebitelé již přístup ke stejnému rozhraní vystavené sestavení nemá vliv na binární kompatibilitu. Změna tohoto druhu se nazývá *binární nekompatibilní změna*.

## <a name="source-compatibility"></a>Kompatibilita zdroje

Kompatibilita zdroje odkazuje na schopnost stávajících spotřebitelů rozhraní API překompilovat proti novější verzi bez jakýchkoli změn zdroje. *Zdroj nekompatibilní změna* nastane, když spotřebitel potřebuje upravit zdrojový kód pro něj úspěšně sestavit proti novější verzi rozhraní API.

## <a name="design-time-compatibility"></a>Kompatibilita v době návrhu

Kompatibilita návrhu odkazuje na zachování návrhu v průběhu verze sady Visual Studio a jiných prostředí návrhu. I když to může zahrnovat chování nebo uI návrhářů, nejdůležitější aspekt kompatibility návrhu se týká kompatibility projektu. Projekt nebo řešení musí být možné otevřít a použít v novější verzi prostředí návrhu.

## <a name="backwards-compatibility"></a>Zpětná kompatibilita

Zpětná kompatibilita odkazuje na schopnost existujícího příjemce rozhraní API spustit proti nové verzi a zároveň se chovat stejným způsobem. Změny chování a změny v binární kompatibilitě ovlivňují zpětnou kompatibilitu. Pokud spotřebitel není schopen spustit nebo se chová odlišně při spuštění proti novější verzi rozhraní API, rozhraní API je *zpětně nekompatibilní*.

Změny, které mají vliv na zpětnou kompatibilitu, se neodradí, protože vývojáři očekávají zpětnou kompatibilitu v novějších verzích rozhraní API.

## <a name="forward-compatibility"></a>Dopředná kompatibilita

Dopředná kompatibilita odkazuje na schopnost existujícího příjemce rozhraní API spustit proti starší verzi při zobrazení stejné chování. Pokud spotřebitel není schopen spustit nebo se chová odlišně při spuštění proti starší verzi rozhraní API, rozhraní API je *vpřed nekompatibilní*.

Zachování dopředné kompatibility prakticky vylučuje všechny změny nebo dodatky z verze na verzi, protože tyto změny zabránit spotřebiteli, který se zaměřuje na novější verzi spuštění v dřívější verzi. Vývojáři očekávají, že příjemce, který spoléhá na novější rozhraní API nemusí fungovat správně proti starší rozhraní API.

Zachování dopředné kompatibility není cílem jádra .NET Core.

## <a name="see-also"></a>Viz také

- [Vyhodnocení nejnovějších změn v jádru .NET Core](index.md)
