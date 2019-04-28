---
title: Vztah mezi funkcí jazyka a knihovny typů | Dokumentace Microsoftu
description: Jazykové funkce se často spoléhat na knihovnu typů pro implementaci. Seznamte se s danou relaci.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706023"
---
# <a name="relationships-between-language-features-and-library-types"></a>Vztahy mezi funkcí jazyka a knihovny typů

C# Vyžaduje standardní knihovny měl určité typy a členy určitých přístupné pro tyto typy definice jazyka. Kompilátor generuje kód, který používá tyto požadované typy a členy pro mnoho funkcí v jiném jazyce. Pokud je to nezbytné, existují balíčky NuGet, které obsahují typy potřebné pro novější verze jazyka při psaní kódu pro prostředí, kde tyto typy nebo členy nejsou nasazeni ještě.

Tato závislost na funkce standardní knihovny, které bylo součástí C# jazyk od své první verze. V této verzi zahrnutý příklady:

* <xref:System.Exception> -používá pro všechny výjimky generované kompilátorem.
* <xref:System.String> - C# `string` je synonymum pro typ <xref:System.String>.
* <xref:System.Int32> -synonymum `int`.

Tento první verze byla jednoduché: kompilátor a standardní knihovny dodané společně a došlo jenom jednu verzi každého.

Další verze C# nové typy nebo členy příležitostně přidali do závislostí. Mezi příklady patří: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> a <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C#7.0 pokračuje to tak, že přidáte závislost na <xref:System.ValueTuple> k implementaci [řazených kolekcí členů](../tuples.md) funkci jazyka.

Tým návrhu jazyk pracuje minimalizovat útoku na typy a členy v kompatibilní standardní knihovna vyžaduje. Tohoto cíle je porovnán s čistým návrhem, kde nových funkcí knihovny jsou bezproblémově součástí jazyka. V budoucích verzích bude mít nové funkce C# , které vyžadují nové typy a členy ve standardní knihovně. Je důležité pochopit, jak spravovat tyto závislosti práce se změnami.

## <a name="managing-your-dependencies"></a>Správa závislostí

C#kompilačních nástrojů se nyní oddělený od cyklu vydávání verzí knihoven .NET na podporovaných platformách. Ve skutečnosti různé knihovny .NET mají cykly vydávání verzí různé: rozhraní .NET Framework na Windows nebude vydaná jako Windows Update, .NET Core se celá dodává v samostatném plánu a Xamarin verze knihovny aktualizace se dodávají s nástroje Xamarin pro každou cílovou platformu.

Většinu času, nebude Všimněte si těchto změn. Při práci s novější verzí jazyka, který vyžaduje funkce není dosud knihoven .NET na této platformě, ale budete odkazovat balíčky NuGet, k poskytování těchto nových typů.
Jako platformy nové instalace rozhraní framework, se aktualizují vaše aplikace podporuje můžete odebrat odkaz na další.

Toto oddělení znamená, že nové funkce jazyků můžete použít i v případě, že se zaměřujete na počítače, které nemusí mít odpovídající rozhraní.
