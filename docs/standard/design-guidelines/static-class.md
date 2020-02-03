---
title: Návrh statické třídy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 104fa204a95ef31d34e224348068e3a6505aded5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743592"
---
# <a name="static-class-design"></a>Návrh statické třídy
Statická třída je definována jako třída, která obsahuje pouze statické členy (samozřejmě kromě členů instance zděděných z <xref:System.Object?displayProperty=nameWithType> a případně z privátního konstruktoru). Některé jazyky poskytují integrovanou podporu pro statické třídy. V C# 2,0 a novějších, pokud je třída deklarována jako statická, je zapečetěná, abstraktní a žádné členy instance nelze přepsat nebo deklarovat.

 Statické třídy představují kompromis mezi čistě objektově orientovaným návrhem a jednoduchostí. Obvykle se používají k poskytnutí zástupců pro jiné operace (například <xref:System.IO.File?displayProperty=nameWithType>), držitelům rozšiřujících metod nebo funkcí, pro které není úplný objektově orientované obálka oprávněná (například <xref:System.Environment?displayProperty=nameWithType>).

 ✔️ použít statické třídy zřídka.

 Statické třídy by měly být použity pouze jako podpůrné třídy pro objektově orientované jádro architektury.

 ❌ nepovažují statické třídy za různé intervaly.

 ❌ Nedeklarujte nebo přepište členy instance ve statických třídách.

 ✔️ deklarovat statické třídy jako zapečetěné, abstraktní a přidat konstruktor privátní instance, pokud váš programovací jazyk nemá integrovanou podporu pro statické třídy.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
