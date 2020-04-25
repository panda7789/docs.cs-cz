---
title: 'Postupy: kontrola obsahu sestavení pomocí MetadataLoadContext'
description: Naučte se používat MetadataLoadContext, což je rozhraní API, které umožňuje načíst sestavení .NET pro účely kontroly.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 90c84147c52199afc42a2efc297bc7fe40658ec7
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141204"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>Postupy: kontrola obsahu sestavení pomocí MetadataLoadContext

Rozhraní API pro reflexi v rozhraní .NET ve výchozím nastavení umožňuje vývojářům kontrolovat obsah sestavení načtených do hlavního prováděcího kontextu. V některých případech však není možné načíst sestavení do kontextu spuštění, například protože byl zkompilován pro jinou architekturu platformy nebo procesoru, nebo se jedná o [referenční sestavení](reference-assemblies.md). <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> Rozhraní API umožňuje načíst a zkontrolovat taková sestavení. Sestavení načtená do <xref:System.Reflection.MetadataLoadContext> jsou zpracována pouze jako metadata, to znamená, že můžete prozkoumávat typy v sestavení, ale nelze spustit žádný kód obsažený v tomto sestavení. Na <xref:System.Reflection.MetadataLoadContext> rozdíl od hlavního kontextu spuštění nenačítá automaticky závislosti z aktuálního adresáře. místo toho používá vlastní logiku vazby poskytnutou <xref:System.Reflection.MetadataAssemblyResolver> předaným do IT.

## <a name="prerequisites"></a>Požadavky

Chcete- <xref:System.Reflection.MetadataLoadContext>li použít, nainstalujte balíček NuGet [System. Reflection. MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) . Podporuje se v jakémkoli cílovém rozhraní, které dodržuje .NET Standard 2,0, například .NET Core 2,0 nebo .NET Framework 4.6.1.

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>Vytvoření MetadataAssemblyResolver pro MetadataLoadContext

Vytváření <xref:System.Reflection.MetadataLoadContext> vyžaduje poskytnutí instance <xref:System.Reflection.MetadataAssemblyResolver>. Nejjednodušší způsob <xref:System.Reflection.PathAssemblyResolver>, jak jeden zadat, je použít, který překládá sestavení ze zadané kolekce řetězců cest sestavení. Tato kolekce, kromě sestavení, která chcete přímo prozkoumat, by měla také zahrnovat všechny potřebné závislosti. Chcete-li například načíst vlastní atribut umístěný v externím sestavení, měli byste zahrnout toto sestavení, nebo bude vyvolána výjimka. Ve většině případů byste měli zahrnout alespoň *základní sestavení*, to znamená sestavení obsahující předdefinované systémové typy, například <xref:System.Object?displayProperty=nameWithType>. Následující kód ukazuje, jak vytvořit <xref:System.Reflection.PathAssemblyResolver> pomocí kolekce sestávající z kontrolovaného sestavení a aktuálního základního sestavení modulu runtime:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

Potřebujete-li přístup ke všem typům BCL, můžete do kolekce zahrnout všechna sestavení modulu runtime. Následující kód ukazuje, jak vytvořit <xref:System.Reflection.PathAssemblyResolver> pomocí kolekce skládající se z kontrolovaného sestavení a všech sestavení aktuálního modulu runtime:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>Vytvořit MetadataLoadContext

Chcete-li <xref:System.Reflection.MetadataLoadContext>vytvořit, vyvolat jeho <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>konstruktor, předat dříve vytvořený <xref:System.Reflection.MetadataAssemblyResolver> jako první parametr a základní název sestavení jako druhý parametr. Základní název sestavení můžete vynechat. v takovém případě se konstruktor pokusí použít výchozí názvy: "mscorlib", "System. Runtime" nebo "netstandard".

Po vytvoření kontextu můžete do něj načíst sestavení pomocí metod, jako je například <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>. Můžete použít všechna rozhraní API reflexe u načtených sestavení kromě těch, která zahrnují provádění kódu. <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> Metoda zahrnuje spuštění konstruktorů, takže použijte <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> metodu místo toho, když potřebujete prošetřit vlastní atributy v <xref:System.Reflection.MetadataLoadContext>.

Následující ukázka kódu vytvoří <xref:System.Reflection.MetadataLoadContext>, načte do něj sestavení a výstupy atributů sestavení do konzoly:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>Příklad

Úplný příklad kódu naleznete v tématu [Kontrola obsahu sestavení pomocí MetadataLoadContext Sample](https://docs.microsoft.com/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/).
