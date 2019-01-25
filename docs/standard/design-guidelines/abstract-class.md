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
author: KrzysztofCwalina
ms.openlocfilehash: 6eec3bb4575b89c6476e6c3410050c705141777f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550408"
---
# <a name="abstract-class-design"></a>Návrh abstraktní třídy
**X DO NOT** definice veřejných nebo chráněného interní konstruktorů v abstraktních typech.  
  
 Konstruktory by měly být veřejné, pouze v případě, že uživatelé budou potřebovat k vytvoření instance daného typu. Protože nelze vytvořit instance abstraktního typu, abstraktní typ s veřejným konstruktorem je nesprávně navrženy a pro uživatele matoucí.  
  
 **✓ DO** definice s chráněným nebo interní konstruktor v abstraktní třídy.  
  
 Chráněný konstruktor je běžné a jednoduše umožňuje udělat vlastní inicializaci, když jsou vytvořeny podtypy základní třídy.  
  
 Interní konstruktor slouží k omezení konkrétní implementace abstraktní třídu pro sestavení, definice třídy.  
  
 **✓ DO** zadejte alespoň jeden konkrétní typ, který dědí z každé abstraktní třída, která můžete dodávat.  
  
 Provádí se to pomáhá k ověření návrh abstraktní třídy. Například <xref:System.IO.FileStream?displayProperty=nameWithType> je implementace <xref:System.IO.Stream?displayProperty=nameWithType> abstraktní třídy.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
