---
title: Pokyny k návrhu architektury
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2674acf14aae5e892dfb9707a19cca12b4797c90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572980"
---
# <a name="framework-design-guidelines"></a>Pokyny k návrhu architektury
Tato část obsahuje pokyny pro návrh knihovny, které rozšiřují a interakci s rozhraním .NET Framework. Cílem je pomoct knihovny Designer zajistit konzistentnost rozhraní API a snadné použití tím, že poskytuje jednotný programovací model, která je nezávislá programovací jazyk používaný pro vývoj. Doporučujeme vám, postupujte podle těchto pokynů pro návrh, při vývoji třídy a součásti, které rozšiřují rozhraní .NET Framework. Návrh nekonzistentní knihovny nepříznivě ovlivní produktivita vývojářů a nedoporučuje přijetí.  
  
 Pokyny jsou uspořádána jako jednoduchý doporučení předponu s podmínkami `Do`, `Consider`, `Avoid`, a `Do not`. Tyto pokyny jsou určeny k pomoci třídy knihovny Designer pochopit kompromis mezi různá řešení. Můžou nastat situace, kdy dobrý knihovny návrhu vyžaduje způsobila porušení těchto pokynů pro návrh. Takových případech by měl být výjimečná a je důležité, abyste měli vymazat a poutavých důvod pro vaše rozhodnutí.  
  
 Tyto pokyny jsou převzaty z knihy webových stránek *pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání*, Krzysztof Cwalina a Abrams Brada.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Obsahuje pokyny pro pojmenování sestavení, obory názvů, typy a členy v knihovny tříd.  
  
 [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
 Poskytuje pokyny pro používání statických a abstraktní třídy, rozhraní, výčty, struktur a dalších typů.  
  
 [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
 Obsahuje pokyny pro návrh a pomocí vlastnosti, metody, konstruktory, pole, operátory, události a parametry.  
  
 [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Popisuje rozšiřitelnost mechanismy, jako je vytváření podtříd, pomocí události, virtuální členové a zpětná volání a vysvětluje, jak zvolit mechanismy, které nejlépe splňují požadavky vašeho framework.  
  
 [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)  
 Popisuje pokyny pro návrh pro navrhování, vyvolání a zachycení výjimky.  
  
 [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Popisuje pokyny pro použití běžné typy, jako je například pole, atributy a kolekce, podporu serializace a přetížení operátory rovnosti.  
  
 [Obecné vzory návrhu](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Obsahuje pokyny pro výběr a implementace vlastností závislostí a vzoru uvolnění.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Přehled](../../../docs/framework/get-started/overview.md)  
 [Plán pro rozhraní .NET Framework](https://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [Průvodce vývojem](../../../docs/framework/development-guide.md)
