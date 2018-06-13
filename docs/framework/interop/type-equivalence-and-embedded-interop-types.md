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
ms.openlocfilehash: e3eeba609349bb9d5b7c68e15e0e0e6ff3f1b7ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390930"
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Ekvivalence typů a vestavěné typy spolupráce

Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], běžné podporuje runtime jazyka vložení informací o typu pro typy modelu COM přímo do spravované sestavení, místo aby spravované sestavení, které chcete získat informace o typu pro typy modelu COM z spolupráce – sestavení. Informace o vložených typu zahrnuje jenom typy a členy, které jsou spravované sestavení. ve skutečnosti používány, a proto může mít dva spravované sestavení velmi různá zobrazení stejného typu COM. Každé spravované sestavení má jiné <xref:System.Type> objekt představující jeho zobrazení typu modelu COM. Modul common language runtime podporuje ekvivalence typů mezi tyto různá zobrazení pro rozhraní, struktury, výčty a delegáti.

Ekvivalence typů znamená, že objekt modelu COM, který je předán z jedné spravované sestavení do jiného lze převést na odpovídající typ v přijímající sestavení spravované.

> [!NOTE]
> Ekvivalence typů a vestavěné typy spolupráce zjednodušit nasazení aplikace a doplňky, které používají komponenty modelu COM, protože to není nezbytné pro nasazení sestavení vzájemné spolupráce s aplikacemi. Vývojáři sdílené komponenty modelu COM ještě vytvořit primární spolupracující sestavení (PIA), pokud chtějí jejich součásti použije ve starších verzích rozhraní .NET Framework.

## <a name="type-equivalence"></a>Ekvivalence typů

 Ekvivalence typů COM je podporován pro rozhraní, struktury, výčty a delegáti. Typy modelu COM kvalifikaci jako ekvivalentní, pokud jsou splněny všechny z následujících akcí:

- Typy jsou obě rozhraní, nebo jak struktur, nebo jak výčty nebo oba delegáti.

- Typy mít stejnou identitu, jak je popsáno v následující části.

- Oba typy jsou způsobilé pro ekvivalence typů, jak je popsáno v [označení COM typy ekvivalence typů](#marking-com-types-for-type-equivalence) části.

### <a name="type-identity"></a>Typ identity

Dva typy, které jsou určeny k mít stejnou identitu při jejich obory a identity odpovídat jinými slovy, pokud každá má <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atribut a dva atributy mají odpovídající <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> a <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> vlastnosti. Porovnání pro <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> je velká a malá písmena.

Pokud typ nemá <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atribut, nebo pokud nemá <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atribut, který není uveden oboru a identifikátor, typ lze i nadále považovat za pro ekvivalenční následujícím způsobem:

- Pro rozhraní, hodnota <xref:System.Runtime.InteropServices.GuidAttribute> se používá místo <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> vlastnost a <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnost (to znamená, že název typu včetně oboru názvů) se používá namísto <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> vlastnost.

- Struktury, výčty a delegáti <xref:System.Runtime.InteropServices.GuidAttribute> obsahující sestavení, které se používá namísto <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> vlastnost a <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnost se používá namísto <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> vlastnost.

### <a name="marking-com-types-for-type-equivalence"></a>Označení typy modelu COM pro ekvivalence typů

 Můžete označit typu jako vhodné pro ekvivalence typů dvěma způsoby:

- Použít <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atributu typu.

- Ujistěte se, typ typ importu COM. Rozhraní je typ importu COM, pokud má <xref:System.Runtime.InteropServices.ComImportAttribute> atribut. Rozhraní, struktura, výčet nebo delegáta je typ importu COM, pokud má sestavení, ve kterém je definovaný <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> atribut.

## <a name="see-also"></a>Viz také

<xref:System.Type.IsEquivalentTo%2A>  
[Použití typy modelu COM ve spravovaném kódu](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))  
[Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)  
