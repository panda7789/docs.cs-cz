---
title: Silné názvy a knihoven .NET
description: Doporučené osvědčené postupy pro silné pojmenovávání knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: 6f5743c7a8c6fdbdcdcf3aa80d2f92f2e04621f2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201449"
---
# <a name="strong-naming"></a>Silné názvy

Silné názvy odkazuje na podepsání sestavení s klíčem, vytváření [sestavení se silným názvem](../../framework/app-domains/strong-named-assemblies.md). Po sestavení se silným názvem ho vytvoří jedinečnou identitu na základě čísla verze název a sestavení a může pomoci zabránit konfliktům při sestavení.

Silné názvy nevýhodou je, že rozhraní .NET Framework ve Windows umožňuje striktní načítání sestavení po sestavení je silný název. Odkaz sestavení se silným názvem musí přesně shodovat s verzí odkazuje sestavení, vynucení vývojářům [konfigurace přesměrování vazby](../../framework/configure-apps/redirect-assembly-versions.md) při použití sestavení:

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

Vývojáři na platformě .NET stěžovat silné názvy, co se budete obvykle stěžovat při načítání striktní sestavení. Naštěstí tento problém je izolovaná na rozhraní .NET Framework. .NET core, Xamarin, UPW a většina jiných implementace .NET není nutné přísnou načítání sestavení a odebere Hlavní nevýhodou silné názvy.

Jeden důležitý aspekt silné názvy je, že se jedná o virálního: silné s názvem pouze odkaz na sestavení mohou ostatní silné s názvem sestavení. Pokud vaše knihovna není silné s názvem, pak jste vyloučili vývojáři, kteří vytvářejí aplikace nebo knihovna, která musí využívat silné názvy.

Výhody silné názvy jsou:

1. Sestavení lze odkazovat a používat jiné sestavení se silným názvem.
2. Sestavení mohou být uloženy v globální mezipaměti sestavení (GAC).
3. Sestavení lze načíst souběžně s jinými verzemi sestavení. Načítání sestavení vedle sebe je běžně potřebné pro aplikace pomocí modulu plug-in architektury.

## <a name="create-strong-named-net-libraries"></a>Vytvořit silné s názvem knihovny pro .NET

Open source knihoven .NET by měl silný název. Silné názvy sestavení zajistí ho většina lidí může použít a ovlivňuje pouze načítání striktní sestavení rozhraní .NET Framework.

> [!NOTE]
> Tento návod je specifický pro veřejně distribuované knihovny .NET, například knihovny .NET publikovaná na NuGet.org. Silné názvy není vyžadováno pro většinu aplikací .NET a by neměla být provedena ve výchozím nastavení.

**✔️ ZVAŽTE** silné názvy sestavení své knihovny.

**✔️ ZVAŽTE** přidání silného pojmenování klíče do systému správy zdrojů.

> Veřejně dostupné klíče umožňuje vývojářům upravit a znovu zkompilovat zdrojový kód knihovny se stejným klíčem.
> 
> Silného pojmenování klíče by neměla provést veřejné, pokud byl udělit zvláštní oprávnění použili v minulosti [částečnou důvěryhodností scénářích](/dotnet/framework/misc/using-libraries-from-partially-trusted-code). V opačném případě by mohlo ohrozit existující prostředí.

> [!IMPORTANT]
> Potřebujete identity vydavatele kód [Authenticode](/windows-hardware/drivers/install/authenticode) a [podepisování balíčků NuGet](/nuget/create-packages/sign-a-package) doporučují. Zabezpečení přístupu kódu (CAS) není vhodné používat jako omezení rizik zabezpečení.

**✔️ ZVAŽTE** zvyšování verze sestavení na změny jenom hlavní verzi k poskytování pomoci uživatelům omezit přesměrování vazby a jak často se aktualizuje.

> Další informace o [správy verzí a verzí sestavení](./versioning.md#assembly-version).

**❌ NEPODPORUJÍ** přidat, odebrat nebo změnit silného pojmenování klíče.

> Úprava silného pojmenování klíče sestavení změní identitu sestavení a přeruší zkompilovaný kód, který ji používá. Další informace najdete v tématu [binární rozbíjející změny v](./breaking-changes.md#binary-breaking-change).

**❌ NEPODPORUJÍ** publikování silným názvem a jiných silným názvem verzí knihovny. Například `Contoso.Api` a `Contoso.Api.StrongNamed`.

> Publikování větve dva balíčky vaše vývojářské ekosystému. Také pokud aplikace končí v závislosti na oba balíčky vývojáři můžou mít typ název je v konfliktu. Co se týče .NET jsou různé typy v různých sestaveních.

>[!div class="step-by-step"]
[Předchozí](./cross-platform-targeting.md)
[další](./nuget.md)
