---
title: Abstrakce (abstraktní typy a rozhraní)
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
ms.openlocfilehash: 6a4f511af72aad916d367153090504e2a8e11cb8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741809"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Abstrakce (abstraktní typy a rozhraní)
Abstrakce je typ, který popisuje kontrakt, ale neposkytuje úplnou implementaci kontraktu. Abstrakce jsou obvykle implementovány jako abstraktní třídy nebo rozhraní a jsou dodávány s dobře definovanou sadou Referenční dokumentace popisující požadovanou sémantiku typů, které implementují kontrakt. Mezi nejdůležitější abstrakce v .NET Framework patří <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>a <xref:System.Object>.

 Rozhraní můžete roztáhnout implementací konkrétního typu, který podporuje kontrakt abstrakce, a použitím tohoto konkrétního typu s rozhraními API architektury, které spotřebovávají (pracuje na) abstrakce.

 Smysluplná a užitečná abstrakce, která může vydržet test času, je velmi obtížné navrhnout. Hlavní obtížnost je získání správné sady členů, ne více a méně. Pokud má abstrakce příliš mnoho členů, je obtížné nebo dokonce možné ji implementovat. Pokud má příliš málo členů pro přislíbenou funkci, je to v mnoha zajímavých scénářích zbytečné.

 Příliš mnoho abstrakcí v rámci architektury má také negativní vliv na použitelnost rozhraní. Je často poměrně obtížné pochopit abstrakci, aniž byste pochopili, jak se vejde na větší obrázek konkrétních implementací a rozhraní API, která na abstrakci pracují. Názvy abstrakcí a jejich členů jsou také nutně abstraktní, což často usnadňuje jejich nepřístupné a nepřístupné, aniž by bylo nutné nejprve pochopit širší kontext jejich využití.

 Abstrakce však poskytují extrémně výkonnou rozšiřitelnost, kterou jiné mechanismy rozšíření nemůžou často porovnat. Jsou v jádru mnoha vzorů architektury, jako jsou moduly plug-in, inverze řídicích prvků (IoC), kanály atd. Jsou také mimořádně důležité pro testování architektur. Dobré abstrakce umožňují, aby byly pro účely testování částí využívány těžké závislosti. V souhrnu jsou abstrakce zodpovědné za hledané – po bohatosti moderních rozhraní orientovaných na objekty.

 ❌ neposkytuje abstrakce, pokud nejsou testovány vývojem několika konkrétních implementací a rozhraní API, které spotřebovávají abstrakce.

 ✔️ Při navrhování abstrakce zvolit pečlivě mezi abstraktní třídou a rozhraním.

 ✔️ Zvažte poskytnutí referenčních testů pro konkrétní implementace abstrakcí. Tyto testy by uživatelům umožnily testovat, zda jejich implementace správně implementují kontrakt.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
