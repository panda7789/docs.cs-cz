---
title: Vztah mezi funkce jazyka a typy knihovny | Microsoft Docs
description: Jazykové funkce často spoléhají na knihovny typů pro implementaci. Pochopení relace.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="relationships-between-language-features-and-library-types"></a>Vztahy mezi funkce jazyka a knihovny typů

Definice jazyka C# vyžaduje standardní knihovnu, kterou chcete mít určité typy a členy určité dostupné v těchto typů. Kompilátor generuje kód, který používá tyto požadované typy a členy mnoha funkcí v jiném jazyce. Pokud je to nezbytné, existují balíčky NuGet, které obsahují typy třeba novější verze jazyka při psaní kódu v prostředích, kde tyto typy nebo členy nebyly nasazeny ještě.

Tuto závislost na funkce standardní knihovny byl součástí jazyka C# od jeho první verzi. V této verzi zahrnuté příklady:

* <xref:System.Exception> -použít pro všechny výjimky kompilátoru vygenerovat.
* <xref:System.String> -C# `string` typ se jedná o synonymum <xref:System.String>.
* <xref:System.Int32> -synonymum z `int`.

Tento první verze je jednoduchý: standardní knihovna a kompilátor dodané společně a došlo jenom jedna verze jednotlivých.

Další verze jazyka C# příležitostně přidali nové typy nebo členy pro závislosti. Příklady: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> a <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C# 7.0 pokračuje to přidáním závislost na <xref:System.ValueTuple> implementovat [řazených kolekcí členů](../tuples.md) funkce jazyka.

Tým návrhu jazyk pracuje na minimalizujte možnosti útoku typů a členů vyžaduje kompatibilní standardní knihovny. Tento cíl je porovnán s čistou návrhu, kde nových funkcí knihovny jsou bezproblémově součástí jazyk. Bude mít nové funkce v budoucích verzích systému C#, které vyžadují nové typy a členy ve standardní knihovně. Je důležité pochopit, jak ke správě těchto závislostí v práci.

## <a name="managing-your-dependencies"></a>Správa závislostmi

Nástroje pro kompilátor jazyka C# jsou nyní odpojené od vydání cyklus na knihovny .NET na podporovaných platformách. Ve skutečnosti různé knihovny .NET mít jinou verzi cykly: rozhraní .NET Framework v systému Windows je vydané jako Windows Update, .NET Core dodávky samostatné plán a Xamarin verzích lodě aktualizace knihovny nástroje Xamarin pro každou cílovou platformu.

Většinu doby, nebude zjistíte, tyto změny. Při práci s novější verzí jazyka, který vyžaduje funkce není ještě v na knihovny .NET na této platformě, ale budete odkazovat balíčky NuGet k poskytování těchto nových typů.
Jako platforem, vaše aplikace podporuje jsou aktualizované o nové instalace framework můžete odebrat odkaz na další.

Toto rozdělení znamená, že můžete použít nové jazykové funkce i v případě, že volíte počítače, které nemusí mít odpovídající framework.
