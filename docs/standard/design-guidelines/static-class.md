---
title: Návrh statické třídy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3a0a51fc6055190f9a0189de2e17d98f88036ea
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48031757"
---
# <a name="static-class-design"></a>Návrh statické třídy
Statická třída je definována jako třída, která obsahuje pouze statické členy (samozřejmě kromě instance členy zděděné z <xref:System.Object?displayProperty=nameWithType> a pravděpodobně soukromého konstruktoru). Některé jazyky poskytují integrovanou podporu pro statické třídy. V jazyce C# 2.0 nebo novější Pokud třída je deklarován jako statický, je zapečetěná, abstraktní a žádné členy instance můžete přepisu nebo deklarován.  
  
 Statické třídy jsou kompromis mezi čistě objektově orientovaný návrh a jednoduchost. Se běžně používají k zajištění klávesové zkratky pro jiné operace (například <xref:System.IO.File?displayProperty=nameWithType>), držitele rozšiřující metody nebo funkce, pro kterou negarantované celý objekt objektově orientovanou obálku (například <xref:System.Environment?displayProperty=nameWithType>).  
  
 **✓ DO** statické třídy používejte opatrně.  
  
 Statické třídy by měl používat pouze jako pomocných tříd pro objektově orientované core Framework.  
  
 **X DO NOT** statické třídy považovat za různé sady.  
  
 **X DO NOT** deklarovat nebo přepsání instance členové statické třídy.  
  
 **✓ DO** deklarovat statické třídy jako zapečetěné, abstraktní a přidejte konstruktor privátní instance, pokud si programovací jazyk nemá integrovanou podporu pro statické třídy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
