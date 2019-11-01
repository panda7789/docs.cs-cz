---
title: Silné názvy a knihovny .NET
description: Doporučení osvědčených postupů pro silné pojmenovávání knihoven .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: 3e7cc9a3a1be05d8fcb02b34f7027126697d15d0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196968"
---
# <a name="strong-naming"></a>Vytváření silných názvů

Silné pojmenování odkazuje na podepsání sestavení klíčem a vytváření [sestavení se silným názvem](../assembly/strong-named.md). Je-li sestavení se silným názvem, vytvoří jedinečnou identitu na základě názvu a čísla verze sestavení a může přispět k prevenci konfliktů sestavení.

Nevýhodou na silné názvy je, že .NET Framework ve Windows umožňuje striktní načítání sestavení, jakmile je sestavení silným názvem. Odkaz na sestavení se silným názvem se musí přesně shodovat s verzí, na kterou odkazuje sestavení. při použití sestavení vynutí vývojáři [nakonfigurovat přesměrování vazby](../../framework/configure-apps/redirect-assembly-versions.md) .

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

Když vývojáři rozhraní .NET nakladou stížnost na silné pojmenování, k čemu obvykle dochází, je striktní načítání sestavení. Naštěstí je tento problém izolovaný od .NET Framework. .NET Core, Xamarin, UWP a většina dalších implementací .NET nemají striktní načítání sestavení a odstraňují Hlavní nevýhodou silných názvů.

Jedním z důležitých aspektů silného pojmenování je to, že je to virové: silné pojmenované sestavení může odkazovat jenom na další silná pojmenovaná sestavení. Pokud vaše knihovna nemá silný název, měli byste vyloučit vývojáře, kteří sestavují aplikaci nebo knihovnu, která potřebuje silné názvy jejich použití.

Výhody silného pojmenování:

1. Sestavení lze odkazovat a používat v jiných sestavení se silným názvem.
2. Sestavení může být uloženo v globální mezipaměti sestavení (GAC).
3. Sestavení lze načítat souběžně s jinými verzemi sestavení. Souběžné načítání sestavení je běžně vyžadováno aplikacemi s architekturami modulů plug-in.

## <a name="create-strong-named-net-libraries"></a>Vytvořit silně pojmenované knihovny .NET

Měli byste silně pojmenovat open source knihovny .NET. Silné pojmenování sestavení zajišťuje, aby ho nejvíc uživatelé mohl použít a striktní načítání sestavení ovlivňuje jenom .NET Framework.

> [!NOTE]
> Tyto doprovodné materiály jsou specifické pro veřejně distribuované knihovny .NET, jako jsou knihovny .NET publikované v NuGet.org. Pro většinu aplikací .NET není vyžadováno silné pojmenování a ve výchozím nastavení by se nemělo provádět.

**✔️ zvažte** silné pojmenovávání sestavení vaší knihovny.

**✔️ zvažte** přidání klíče silného pojmenování do systému správy zdrojů.

> Veřejně dostupný klíč umožňuje vývojářům změnit a znovu zkompilovat zdrojový kód knihovny se stejným klíčem.
> 
> Silný klíč pro pojmenovávání by neměl být veřejný, pokud byl v minulosti použit k udělení zvláštních oprávnění ve [scénářích s částečnou důvěryhodností](../../framework/misc/using-libraries-from-partially-trusted-code.md). V opačném případě může dojít k ohrožení stávajících prostředí.

> [!IMPORTANT]
> Pokud je požadována identita vydavatele kódu, doporučujeme podepisování prostřednictvím [technologie Authenticode](/windows-hardware/drivers/install/authenticode) a [balíčku NuGet](/nuget/create-packages/sign-a-package) . Zabezpečení přístupu kódu (CAS) by nemělo být použito jako zmírnění zabezpečení.

**✔️ zvažte** zvýšení verze sestavení pouze při změnách hlavní verze, které uživatelům pomůžou snížit přesměrování vazby a jak často se aktualizují.

> Přečtěte si další informace o způsobu [správy verzí a verzi sestavení](./versioning.md#assembly-version).

**❌** Nepřidávat, odebírat ani měnit silný názvový klíč.

> Úprava silného klíče pro pojmenování sestavení změní identitu sestavení a přeruší zkompilovaný kód, který ho používá. Další informace najdete v tématu [binární změny v binárním souboru](./breaking-changes.md#binary-breaking-change).

**❌** nepublikujte v knihovně silně pojmenované a nedostatečně pojmenované verze vaší knihovny. Například `Contoso.Api` a `Contoso.Api.StrongNamed`.

> Publikování dvou balíčků rozvětvení ekosystém pro vývojáře. Také Pokud aplikace skončí v závislosti na obou balíčcích, může vývojář zaznamenat konflikty názvů typů. V případě, že se týká .NET, jsou různými typy v různých sestaveních.

>[!div class="step-by-step"]
>[Předchozí](cross-platform-targeting.md)
>[Další](nuget.md)
