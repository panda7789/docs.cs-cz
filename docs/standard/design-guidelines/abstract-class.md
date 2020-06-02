---
title: Návrh abstraktní třídy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: e6a5923f293ed536fb272f6fe6c805067aede0ab
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280774"
---
# <a name="abstract-class-design"></a>Návrh abstraktní třídy

❌Nedefinujte veřejné nebo chráněné interní konstruktory v abstraktních typech.

 Konstruktory by měly být veřejné pouze v případě, že uživatelé budou muset vytvořit instance daného typu. Vzhledem k tomu, že nemůžete vytvořit instance abstraktního typu, je abstraktní typ s veřejným konstruktorem pro uživatele nesprávně navržený a zavádějící.

 ✔️ v abstraktních třídách definujte chráněný nebo interní konstruktor.

 Chráněný konstruktor je běžnější a jednoduše umožňuje základní třídě provádět vlastní inicializaci při vytváření podtypů.

 Vnitřní konstruktor lze použít k omezení konkrétní implementace abstraktní třídy na sestavení, které definuje třídu.

 ✔️ Zadejte alespoň jeden konkrétní typ, který dědí ze všech abstraktních tříd, které dodáváte.

 To pomáhá ověřit návrh abstraktní třídy. Například <xref:System.IO.FileStream?displayProperty=nameWithType> je implementací <xref:System.IO.Stream?displayProperty=nameWithType> abstraktní třídy.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny pro návrh typů](type.md)
- [Pokyny k návrhu architektury](index.md)
