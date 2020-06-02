---
title: Pokyny k návrhu architektury
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 5a4edca70844a2b2a3972381b34efe85664f353d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276033"
---
# <a name="framework-design-guidelines"></a>Pokyny k návrhu architektury
V této části najdete pokyny pro návrh knihoven, které rozšíří a komunikují s .NET Framework. Cílem je pomáhat Návrháři knihovny zajistit konzistenci rozhraní API a snadné použití poskytnutím jednotného programovacího modelu, který je nezávislý na programovacím jazyku používaném pro vývoj. Při vývoji tříd a komponent, které .NET Framework rozšiřuje, doporučujeme postupovat podle těchto pokynů k návrhu. Nekonzistentní návrh knihovny nepříznivě ovlivňuje produktivitu vývojářů a nedoporučuje přijetí.  
  
 Pokyny jsou uspořádané jako jednoduchá doporučení s předponami,, `Do` `Consider` `Avoid` a `Do not` . Tyto pokyny jsou určeny k tomu, aby Návrháři knihoven tříd pochopili kompromisy mezi různými řešeními. Můžou nastat situace, kdy dobrý návrh knihovny vyžaduje, abyste ponarušili tyto pokyny k návrhu. Takové případy by měly být vzácné a je důležité, abyste měli jasný a přesvědčivý důvod pro vaše rozhodnutí.  
  
 Tyto pokyny jsou uvedené v *pokynech pro návrh Book Framework: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice*, Krzysztof Cwalina a Brad Abrams.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Pokyny pro pojmenování](naming-guidelines.md)  
 Poskytuje pokyny pro pojmenování sestavení, oborů názvů, typů a členů v knihovnách tříd.  
  
 [Pokyny pro návrh typů](type.md)  
 Poskytuje pokyny pro použití statických a abstraktních tříd, rozhraní, výčtů, struktur a dalších typů.  
  
 [Pokyny pro návrh členů](member.md)  
 Poskytuje pokyny pro návrh a používání vlastností, metod, konstruktorů, polí, událostí, operátorů a parametrů.  
  
 [Navrhování pro rozšiřitelnost](designing-for-extensibility.md)  
 Popisuje mechanismy rozšiřitelnosti, jako je například použití podtříd, používání událostí, virtuálních členů a zpětných volání, a vysvětluje, jak zvolit mechanismy, které nejlépe vyhovují požadavkům vašeho rozhraní.  
  
 [Pokyny k návrhu pro výjimky](exceptions.md)  
 Popisuje pokyny návrhu pro návrh, vyvolání a zachycení výjimek.  
  
 [Pokyny k použití](usage-guidelines.md)  
 Popisuje pokyny pro použití běžných typů, jako jsou pole, atributy a kolekce, podpora serializace a přetížení operátorů rovnosti.  
  
 [Běžné vzory návrhu](common-design-patterns.md)  
 Poskytuje pokyny pro výběr a implementaci vlastností závislosti.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také

- [Přehled](../../framework/get-started/overview.md)
- [Průvodce vývojem](../../framework/development-guide.md)
