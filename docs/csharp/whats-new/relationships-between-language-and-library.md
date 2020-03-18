---
title: Vztah mezi jazykovými prvky a typy knihoven | Dokumenty společnosti Microsoft
description: Funkce jazyka často spoléhají na typy knihoven pro implementaci. Pochop ten vztah.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61706023"
---
# <a name="relationships-between-language-features-and-library-types"></a>Vztahy mezi funkcemi jazyka a typy knihoven

Definice jazyka C# vyžaduje standardní knihovny mít určité typy a některé přístupné členy na tyto typy. Kompilátor generuje kód, který používá tyto požadované typy a členy pro mnoho různých jazykových funkcí. V případě potřeby existují balíčky NuGet, které obsahují typy potřebné pro novější verze jazyka při psaní kódu pro prostředí, kde tyto typy nebo členy ještě nebyly nasazeny.

Tato závislost na standardní funkce knihovny byla součástí jazyka C# od jeho první verze. V této verzi jsou příklady:

* <xref:System.Exception>- používá se pro všechny výjimky generované kompilátorem.
* <xref:System.String>- C# `string` typ je <xref:System.String>synonymem pro .
* <xref:System.Int32>- synonymum `int`.

Tato první verze byla jednoduchá: kompilátor a standardní knihovna byly dodány společně a byla tam pouze jedna verze každého.

Následné verze jazyka C# příležitostně přidaly nové typy nebo členy do závislostí. Příklady: <xref:System.Runtime.CompilerServices.INotifyCompletion>a <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C# 7.0 pokračuje tím, že <xref:System.ValueTuple> přidá závislost na implementovat funkci jazyka [řazené kolekce členů.](../tuples.md)

Tým pronávrh jazyka pracuje na minimalizaci plochy typů a členů požadovaných v kompatibilní standardní knihovně. Tento cíl je vyvážen proti čistému designu, kde jsou nové funkce knihovny bezproblémově začleněny do jazyka. V budoucích verzích jazyka C# budou nové funkce, které vyžadují nové typy a členy ve standardní knihovně. Je důležité pochopit, jak spravovat tyto závislosti ve vaší práci.

## <a name="managing-your-dependencies"></a>Správa závislostí

Nástroje kompilátoru jazyka C# jsou nyní odděleny od cyklu vydání knihoven .NET na podporovaných platformách. Ve skutečnosti různé knihovny .NET mají různé cykly vydání: rozhraní .NET Framework v systému Windows je vydáno jako služba Windows Update, rozhraní .NET Core je dodáváno podle samostatného plánu a verze aktualizací knihovny Xamarin jsou dodávány s nástroji Xamarin pro každou cílovou platformu.

Po většinu času si těchto změn nevšimnete. Však při práci s novější verzi jazyka, který vyžaduje funkce, které ještě nejsou v knihovnách .NET na této platformě, budete odkazovat na balíčky NuGet poskytnout tyto nové typy.
Vzhledem k tomu, že platformy, které vaše aplikace podporuje, jsou aktualizovány novými instalacemi architektury, můžete odebrat další odkaz.

Toto oddělení znamená, že můžete použít nové funkce jazyka i v případě, že cílíte na počítače, které nemusí mít odpovídající rámec.
