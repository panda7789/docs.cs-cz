---
title: Ekvivalence typů a vestavěné typy spolupráce
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 137aeaab4e63adbb81c0f3d90718def10f906e6a
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489232"
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Ekvivalence typů a vestavěné typy spolupráce

Od verze rozhraní .NET Framework 4, modul common language runtime podporuje vkládání informací o typu pro typy modelu COM přímo do spravovaných sestavení, namísto nutnosti spravované sestavení, které chcete získat informace o typu pro typy modelu COM ze sestavení vzájemné spolupráce. Informace o typu embedded zahrnuje pouze typy a členy, které jsou skutečně používané spravovaným sestavením, a proto může mít dvě spravovaná sestavení velmi různá zobrazení stejného modelu COM typu. Každé spravované sestavení má jiné <xref:System.Type> objekt reprezentující jeho zobrazení modelu COM typu. Modul common language runtime podporuje typu ekvivalence mezi tyto různá zobrazení pro rozhraní, struktury, výčty a delegáti.

Porovnávání znamená, že objekt modelu COM, který je předán z jednoho spravovaného sestavení do jiného lze převést na odpovídající typ v sestavení přijímající spravované.

> [!NOTE]
> Ekvivalence typů a vestavěné typy spolupráce Zjednodušte nasazování aplikací a doplňky, které používají model COM, protože to není nezbytné pro nasazení sestavení vzájemné spolupráce s aplikacemi. Vývojáři sdílené komponenty modelu COM ještě k vytvoření sestavení primární spolupráce (PIA), pokud je to vyžadováno jejich součástí použitého v předchozích verzích rozhraní .NET Framework.

## <a name="type-equivalence"></a>Ekvivalence typů

 Ekvivalence typů modelu COM je podporován pro rozhraní, struktury, výčty a delegáti. Typy modelu COM kvalifikovat jako ekvivalentní, pokud jsou splněny všechny z následujících akcí:

- Jak rozhraní, nebo jak struktury, nebo jak výčty nebo oba delegátů jsou tyto typy.

- Typy mají stejnou identitu, jak je popsáno v další části.

- Oba typy jsou způsobilý pro ekvivalenci typu, jak je popsáno v [typy označení modelu COM pro ekvivalenci typu](#marking-com-types-for-type-equivalence) oddílu.

### <a name="type-identity"></a>Typ identity

Dva typy, které jsou určeny k mít stejnou identitu při jejich obory a identity shodují, jinými slovy, pokud každý z nich <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> a dva atributy mají odpovídající <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> a <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> vlastnosti. Porovnání pro <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> je velká a malá písmena.

Pokud typ nemá <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atribut, nebo jestli bylo <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atribut, který není určen oboru a identifikátor, typ lze stále považovat za pro ekvivalenci následujícím způsobem:

- Pro rozhraní, hodnota <xref:System.Runtime.InteropServices.GuidAttribute> se použije namísto <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> vlastnost a <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnosti (to znamená, název typu včetně oboru názvů) se použije namísto <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> vlastnost.

- Struktury, výčty a delegáti <xref:System.Runtime.InteropServices.GuidAttribute> obsahující sestavení se použije namísto <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> vlastnost a <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnost se používá namísto <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> vlastnost.

### <a name="marking-com-types-for-type-equivalence"></a>Označení typy modelu COM pro ekvivalenci typu

 Můžete označit typ jako způsobilý pro ekvivalenci typu dvěma způsoby:

- Použít <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atribut typu.

- Učiňte typ typu modelu COM importu. Rozhraní je typ importu modelu COM, pokud má <xref:System.Runtime.InteropServices.ComImportAttribute> atribut. Rozhraní, strukturu, výčet nebo delegát je typ importu modelu COM, pokud má sestavení, ve kterém je definována <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> atribut.

## <a name="see-also"></a>Viz také:

- <xref:System.Type.IsEquivalentTo%2A>
- [Používání typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
