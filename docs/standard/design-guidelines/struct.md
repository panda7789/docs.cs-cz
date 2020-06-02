---
title: Návrh struktury
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: c6ac53014e048da3a90dd7b8e961176f61e90355
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290808"
---
# <a name="struct-design"></a>Návrh struktury
Typ hodnoty pro obecné účely se nejčastěji označuje jako struktura, její klíčové slovo jazyka C#. V této části najdete pokyny pro obecný návrh struktury.

 ❌Neposkytněte konstruktor bez parametrů pro strukturu.

 Podle těchto pokynů umožňuje vytvořit pole struktur bez nutnosti spuštění konstruktoru pro každou položku pole. Všimněte si, že jazyk C# neumožňuje strukturám konstruktory bez parametrů.

 ❌Nedefinujte proměnlivé hodnoty typů.

 Proměnlivé typy hodnot mají několik problémů. Například pokud vlastnost getter vrátí typ hodnoty, volající obdrží kopii. Vzhledem k tomu, že kopie je vytvořena implicitně, vývojáři nemusí vědět, že se jedná o kopii, a nikoli původní hodnotu. Také některé jazyky (například dynamické jazyky) mají problémy s použitím proměnlivých hodnotových typů, protože i místní proměnné, pokud jsou převedené, způsobují vytvoření kopie.

 ✔️ Zajistěte, aby byl stav, kde jsou všechna data instance nastavena na hodnotu nula, false nebo null (podle potřeby).

 To brání nechtěnému vytvoření neplatných instancí při vytvoření pole struktury.

 ✔️ PROVÉST implementaci <xref:System.IEquatable%601> na typech hodnot.

 <xref:System.Object.Equals%2A?displayProperty=nameWithType>Metoda na hodnotových typech způsobuje zabalení a její výchozí implementace není velmi efektivní, protože používá reflexi. <xref:System.IEquatable%601.Equals%2A>může mít mnohem lepší výkon a může být implementováno tak, že nebude způsobovat zabalení.

 ❌Nepoužívejte explicitně <xref:System.ValueType> . Většinou tyto jazyky tuto skutečnost znemožňují.

 Obecně mohou být struktury velmi užitečné, ale měly by být použity pouze pro malé, jednoduché, neměnné hodnoty, které nebudou často zabaleny.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny pro návrh typů](type.md)
- [Pokyny k návrhu architektury](index.md)
- [Volba mezi třídou a strukturou](choosing-between-class-and-struct.md)
