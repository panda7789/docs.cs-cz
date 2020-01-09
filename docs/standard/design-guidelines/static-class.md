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
ms.openlocfilehash: 35bcf1d403c78cdfcbb476b2eb5de2251a564b9a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709059"
---
# <a name="static-class-design"></a>Návrh statické třídy
Statická třída je definována jako třída, která obsahuje pouze statické členy (samozřejmě kromě členů instance zděděných z <xref:System.Object?displayProperty=nameWithType> a případně z privátního konstruktoru). Některé jazyky poskytují integrovanou podporu pro statické třídy. V C# 2,0 a novějších, pokud je třída deklarována jako statická, je zapečetěná, abstraktní a žádné členy instance nelze přepsat nebo deklarovat.  
  
 Statické třídy představují kompromis mezi čistě objektově orientovaným návrhem a jednoduchostí. Obvykle se používají k poskytnutí zástupců pro jiné operace (například <xref:System.IO.File?displayProperty=nameWithType>), držitelům rozšiřujících metod nebo funkcí, pro které není úplný objektově orientované obálka oprávněná (například <xref:System.Environment?displayProperty=nameWithType>).  
  
 **✓ DO** statické třídy používejte opatrně.  
  
 Statické třídy by měly být použity pouze jako podpůrné třídy pro objektově orientované jádro architektury.  
  
 **X DO NOT** statické třídy považovat za různé sady.  
  
 **X DO NOT** deklarovat nebo přepsání instance členové statické třídy.  
  
 **✓ DO** deklarovat statické třídy jako zapečetěné, abstraktní a přidejte konstruktor privátní instance, pokud si programovací jazyk nemá integrovanou podporu pro statické třídy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
