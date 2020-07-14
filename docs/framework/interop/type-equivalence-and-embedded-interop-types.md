---
title: Ekvivalenci typů a vložené typy spolupráce
description: Pochopení typu rovnocennosti mezi typy .NET a členy se spravovaným sestavením a typy COM, které jsou vloženy do tohoto sestavení. Pro .NET 4 a novější.
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
ms.openlocfilehash: 2d572133c42f01af7d50f6f771588f5173853f9a
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282005"
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Ekvivalenci typů a vložené typy spolupráce

Počínaje .NET Framework 4, modul CLR (Common Language Runtime) podporuje vkládání informací o typu pro typy COM přímo do spravovaných sestavení, namísto vyžadování spravovaných sestavení pro získání informací o typu pro typy modelu COM ze sestavení Interop. Vzhledem k tomu, že informace o vloženém typu obsahují pouze typy a členy, které jsou ve skutečnosti používány spravovaným sestavením, může mít dvě spravovaná sestavení velmi různá zobrazení stejného typu COM. Každé spravované sestavení má jiný <xref:System.Type> objekt, který představuje své zobrazení typu modelu COM. Modul CLR (Common Language Runtime) podporuje rovnocennosti typů mezi různými zobrazeními pro rozhraní, struktury, výčty a delegáty.

Ekvivalenci typu znamená, že objekt COM, který je předán z jednoho spravovaného sestavení do jiného, lze přetypovat na příslušný spravovaný typ v přijímajícím sestavení.

> [!NOTE]
> Ekvivalenci typů a vložené definiční typy zjednodušují nasazení aplikací a doplňků, které používají komponenty modelu COM, protože není nutné nasazovat sestavení vzájemné spolupráce s aplikacemi. Vývojáři sdílených komponent modelu COM stále musí vytvářet primární spolupracující sestavení (PIA), pokud chtějí, aby jejich komponenty používaly starší verze .NET Framework.

## <a name="type-equivalence"></a>Ekvivalenci typu

 Ekvivalence typů modelu COM je podporována pro rozhraní, struktury, výčty a delegáty. Typy modelu COM jsou způsobilé jako ekvivalent, pokud jsou splněny všechny následující podmínky:

- Typy jsou obě rozhraní, nebo oba struktury, nebo oba delegáti.

- Typy mají stejnou identitu, jak je popsáno v následující části.

- Oba typy jsou způsobilé pro ekvivalenci typu, jak je popsáno v oddílu [označování typů com pro typ ekvivalence](#marking-com-types-for-type-equivalence) .

### <a name="type-identity"></a>Identita typu

Pro dva typy jsou určeny stejné identity, když jejich obory a identity odpovídají jiným slovům, pokud mají každý z nich <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atribut a dva atributy mají odpovídající <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> a <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> Vlastnosti. Porovnání pro <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> rozlišuje velká a malá písmena.

Pokud typ nemá <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atribut, nebo pokud má <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atribut, který neurčuje rozsah a identifikátor, typ může být stále považován za rovnocenný, jak je znázorněno níže:

- V rozhraních se místo vlastnosti používá hodnota, a proto se jako vlastnost používá <xref:System.Runtime.InteropServices.GuidAttribute> <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> <xref:System.Type.FullName%2A?displayProperty=nameWithType> název typu, včetně oboru názvů <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> .

- Pro struktury, výčty a delegáty se <xref:System.Runtime.InteropServices.GuidAttribute> místo vlastnosti používá nadřazené sestavení <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> a <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnost je použita namísto <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> Vlastnosti.

### <a name="marking-com-types-for-type-equivalence"></a>Označení typů modelu COM pro ekvivalenci typů

 Typ můžete označit jako způsobilý pro ekvivalenci typu dvěma způsoby:

- Použijte <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atribut pro typ.

- Zadejte typ importu typu COM. Rozhraní je typ importu COM, pokud má <xref:System.Runtime.InteropServices.ComImportAttribute> atribut. Rozhraní, struktura, výčet nebo delegát je typ importu COM, pokud sestavení, ve kterém je definován, má <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> atribut.

## <a name="see-also"></a>Viz také

- <xref:System.Type.IsEquivalentTo%2A>
- [Použití typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
