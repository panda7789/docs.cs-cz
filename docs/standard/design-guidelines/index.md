---
title: "Pokyny k\_návrhu architektury"
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
  - 'libraries, .NET Framework class library'
  - 'class library design guidelines [.NET Framework], about'
  - 'class library design guidelines [.NET Framework]'
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: KrzysztofCwalina
---
# <a name="framework-design-guidelines"></a>Pokyny k návrhu architektury
Tato část obsahuje pokyny pro návrh knihoven, které rozšiřují a pracovat s rozhraním .NET Framework. Cílem je pomoct knihovny návrhářů tím, že poskytuje jednotný programovací model, který je nezávislý na programovací jazyk se používá pro vývoj pro zajištění konzistence rozhraní API a snadné použití. Doporučujeme postupovat podle následujících pokynů návrhu, při vytváření tříd a komponent, které rozšiřují rozhraní .NET Framework. Návrh nekonzistentní knihovny nepříznivě má vliv na produktivitu vývojářů a odrazuje od přijetí.  
  
 Pokyny jsou uspořádané jako jednoduchý doporučení předponu podmínky `Do`, `Consider`, `Avoid`, a `Do not`. Tyto pokyny jsou určeny k pomohou návrhářům tříd knihovny pochopit kompromisy mezi různými řešeními. Můžou nastat situace, kdy návrh dobrý knihovna vyžaduje, aby že porušují tyto pokyny k návrhu. Takové případy by měl být vzácné a je důležité, abyste měli vymazat a poutavé důvod svého rozhodnutí.  
  
 Tyto pokyny jsou výňatkem z knihy *pokyny k návrhu architektury: Konvence, Idiomy a vzory pro knihovny opakovaně použitelných .NET, 2nd Edition*, Krzysztof Cwalina a Brad Abrams.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Obsahuje pokyny pro pojmenování sestavení, oborů názvů, typy a členy v knihovnách tříd.  
  
 [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
 Poskytuje pokyny pro používání statických a abstraktní třídy, rozhraní, výčty, struktury a ostatní typy.  
  
 [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
 Obsahuje pokyny pro návrh a pomocí vlastnosti, metody, konstruktory, pole, události, operátory a parametry.  
  
 [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Popisuje rozšíření mechanismy, jako je vytváření podtříd, události, virtuální členy a zpětná volání a vysvětluje, jak zvolit mechanismy, které nejlépe splňovat požadavky na vaše architektura.  
  
 [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)  
 Popisuje pokyny k návrhu pro navrhování, vyvolání a zachycení výjimky.  
  
 [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Popisuje pokyny pro běžné typy, jako je například pole, atributy a kolekce pomocí, podpora serializace a operátory rovnosti přetížení.  
  
 [Obecné vzory návrhu](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Obsahuje pokyny pro výběr a implementace vlastnosti závislosti.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Přehled](../../../docs/framework/get-started/overview.md)
- [Průvodce vývojem](../../../docs/framework/development-guide.md)
