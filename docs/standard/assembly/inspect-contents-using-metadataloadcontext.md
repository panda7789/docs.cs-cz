---
title: 'Postup: Kontrola obsahu sestavení pomocí nástroje MetadataLoadContext'
description: Zjistěte, jak používat MetadataLoadContext, což je rozhraní API, které umožňuje načíst sestavení .NET pro účely kontroly.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: d2589d51a6e0611504c0133d293d3fdfae32553c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242657"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>Postup: Kontrola obsahu sestavení pomocí nástroje MetadataLoadContext

Reflexní rozhraní API v rozhraní .NET ve výchozím nastavení umožňuje vývojářům kontrolovat obsah sestavení načtených do hlavního kontextu spuštění. Někdy však není možné načíst sestavení do kontextu spuštění, například proto, že byl zkompilován pro jinou platformu nebo architekturu procesoru, nebo je to [referenční sestavení](reference-assemblies.md). Rozhraní <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> API umožňuje načíst a zkontrolovat tyto sestavení. Sestavení načtená <xref:System.Reflection.MetadataLoadContext> do jsou považována pouze za metadata, to znamená, že můžete prozkoumat typy v sestavení, ale nelze spustit žádný kód obsažený v něm. Na rozdíl od hlavního kontextu spuštění <xref:System.Reflection.MetadataLoadContext> není automaticky načíst závislosti z aktuálního adresáře; místo toho používá vlastní vazby <xref:System.Reflection.MetadataAssemblyResolver> logiky poskytované předány k němu.

## <a name="prerequisites"></a>Požadavky

Chcete-li použít <xref:System.Reflection.MetadataLoadContext>, nainstalujte balíček [System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) NuGet. Je podporován v libovolném cílovém rámci kompatibilním se standardem .NET Standard 2.0, například v rozhraní .NET Core 2.0 nebo .NET Framework 4.6.1.

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>Vytvořit metadataAssemblyResolver pro MetadataLoadContext

Vytvoření <xref:System.Reflection.MetadataLoadContext> vyžaduje poskytnutí instance <xref:System.Reflection.MetadataAssemblyResolver>. Nejjednodušší způsob, jak poskytnout jeden <xref:System.Reflection.PathAssemblyResolver>je použití , který řeší sestavení z dané kolekce řetězců cesty sestavení. Tato kolekce, kromě sestavení, které chcete zkontrolovat přímo, by měla také obsahovat všechny potřebné závislosti. Chcete-li například číst vlastní atribut umístěný v externím sestavení, měli byste zahrnout toto sestavení nebo bude vyvolána výjimka. Ve většině případů byste měli zahrnout alespoň *základní sestavení*, tedy sestavení obsahující předdefinované <xref:System.Object?displayProperty=nameWithType>typy systému, například . Následující kód ukazuje, jak <xref:System.Reflection.PathAssemblyResolver> vytvořit pomocí kolekce skládající se z kontrolovaného sestavení a aktuální sestavení jádra za běhu:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

Pokud potřebujete přístup ke všem typům BCL, můžete zahrnout všechna sestavení za běhu do kolekce. Následující kód ukazuje, jak <xref:System.Reflection.PathAssemblyResolver> vytvořit pomocí kolekce skládající se z kontrolovaného sestavení a všech sestavení aktuálního běhu:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>Vytvořit metadataLoadContext

Chcete-li <xref:System.Reflection.MetadataLoadContext>vytvořit , <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>vyvolat jeho konstruktor , předávání dříve vytvořené <xref:System.Reflection.MetadataAssemblyResolver> jako první parametr a název základního sestavení jako druhý parametr. Můžete vynechat název základní ho sestavení, v takovém případě se konstruktor pokusí použít výchozí názvy: "mscorlib", "System.Runtime" nebo "netstandard".

Po vytvoření kontextu do něj můžete načíst sestavení pomocí <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>metod, jako je například . Můžete použít všechna reflexní API na načtených sestaveních s výjimkou těch, které zahrnují spuštění kódu. Metoda <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> zahrnuje provádění konstruktory, takže použijte <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> metodu místo toho, když potřebujete <xref:System.Reflection.MetadataLoadContext>prozkoumat vlastní atributy v .

Následující ukázka <xref:System.Reflection.MetadataLoadContext>kódu vytvoří , načte sestavení do něj a výstupy atributy sestavení do konzoly:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>Příklad

Úplný příklad kódu naleznete v tématu [Kontrola obsahu sestavení pomocí ukázky MetadataLoadContext](https://github.com/dotnet/samples/tree/master/core/assembly/MetadataLoadContext).
