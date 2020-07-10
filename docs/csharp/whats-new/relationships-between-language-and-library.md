---
title: Vztah mezi funkcemi jazyka a typy knihoven | Microsoft Docs
description: Funkce jazyka se často spoléhají na typy knihoven pro implementaci. Pochopení vztahu.
ms.date: 07/20/2017
ms.openlocfilehash: abf15385da3756c35db2df822cc2e11e9edf5758
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174098"
---
# <a name="relationships-between-language-features-and-library-types"></a>Vztahy mezi funkcemi jazyka a typy knihoven

Definice jazyka C# vyžaduje, aby standardní knihovna měla určité typy a určité dostupné členy na těchto typech. Kompilátor generuje kód, který používá tyto požadované typy a členy pro mnoho různých funkcí jazyka. V případě potřeby existují balíčky NuGet, které obsahují typy potřebné pro novější verze jazyka při psaní kódu pro prostředí, kde tyto typy nebo členy ještě nebyly nasazeny.

Tato závislost na standardní funkci knihovny byla součástí jazyka C# od první verze. V této verzi jsou zahrnuté příklady:

* <xref:System.Exception>– používá se pro všechny výjimky vygenerované kompilátorem.
* <xref:System.String>– Typ C# `string` je synonymum pro <xref:System.String> .
* <xref:System.Int32>– synonymum `int`

Tato první verze byla jednoduchá: kompilátor a standardní knihovna byly dodávány společně a existovala pouze jedna verze.

Další verze jazyka C# někdy do závislostí přidávají nové typy nebo členy. Mezi příklady patří <xref:System.Runtime.CompilerServices.INotifyCompletion> : <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> a <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute> . Jazyk C# 7,0 Tento postup pokračuje přidáním závislosti <xref:System.ValueTuple> k implementaci funkce jazyka [řazené kolekce členů](../language-reference/builtin-types/value-tuples.md) .

Tým návrhu jazyka funguje k minimalizaci oblasti povrchu typů a členů požadovaných v kompatibilní knihovně Standard. Tento cíl je vyvážený proti čistému návrhu, ve kterém se bezproblémově integruje nové funkce knihovny do jazyka. V budoucích verzích jazyka C# budou k dispozici nové funkce, které vyžadují nové typy a členy ve standardní knihovně. Je důležité pochopit, jak tyto závislosti spravovat ve vaší práci.

## <a name="managing-your-dependencies"></a>Správa závislostí

Nástroje kompilátoru C# jsou teď oddělené od cyklu vydání knihoven .NET na podporovaných platformách. Pro různé knihovny rozhraní .NET mají různé cykly vydání vydaných verzí: .NET Framework ve Windows je vydaný jako web Windows Update, dodává se .NET Core na samostatném plánu a verze Xamarin aktualizací knihoven se dodávají s nástroji Xamarin pro každou cílovou platformu.

Většinou si tyto změny nevšimnete. Pokud však pracujete s novější verzí jazyka, který vyžaduje funkce, které ještě nejsou v knihovnách .NET na této platformě, budete odkazovat na balíčky NuGet, aby tyto nové typy poskytovaly.
Protože platformy, které vaše aplikace podporuje, se aktualizují pomocí nových instalací rozhraní. Další informace můžete odebrat.

Toto oddělení znamená, že můžete použít nové funkce jazyka i v případě, že cílíte na počítače, které nemusí mít odpovídající rozhraní.
