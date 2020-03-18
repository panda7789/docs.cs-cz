---
title: Silné pojmenování a knihovny .NET
description: Doporučení osvědčených postupů pro silné pojmenování knihoven .NET.
ms.date: 10/16/2018
ms.openlocfilehash: db268093b07a2ece7cdb8329fd789b52da9c5c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744534"
---
# <a name="strong-naming"></a>Vytváření silných názvů

Silné pojmenování odkazuje na podepsání sestavení pomocí klíče, vytvoření [sestavení se silným názvem](../assembly/strong-named.md). Pokud je sestavení silně pojmenované, vytvoří jedinečnou identitu založenou na názvu a čísle verze sestavení a může pomoci zabránit konfliktům sestavení.

Nevýhodou silného pojmenování je, že rozhraní .NET Framework v systému Windows umožňuje přísné načítání sestavení, jakmile je sestavení silné s názvem. Odkaz na sestavení se silným názvem se musí přesně shodovat s verzí, na kterou odkazuje sestavení, což nutí vývojáře [konfigurovat přesměrování vazeb](../../framework/configure-apps/redirect-assembly-versions.md) při použití sestavení:

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

Když si vývojáři rozhraní .NET stěžují na silné pojmenování, obvykle si stěžují na přísné načítání sestavení. Naštěstí tento problém je izolován a rozhraní .NET Framework. .NET Core, Xamarin, UPW a většina ostatních implementací .NET nemají přísné načítání sestavení a odebere hlavní nevýhodu silného pojmenování.

Jedním z důležitých aspektů silného pojmenování je, že je virové: silné pojmenované sestavení může odkazovat pouze na další silná pojmenovaná sestavení. Pokud vaše knihovna není silná s názvem, pak jste vyloučili vývojáře, kteří budují aplikaci nebo knihovnu, která potřebuje silné pojmenování z jeho použití.

Výhody silného pojmenování jsou:

1. Na sestavení lze odkazovat a používat je jinými sestaveními se silným názvem.
2. Sestavení lze uložit do globální mezipaměti sestavení (GAC).
3. Sestava může být načtena vedle sebe s jinými verzemi sestavení. Zatížení sestavy vedle sebe je běžně vyžadováno aplikacemi s architekturou modulu plug-in.

## <a name="create-strong-named-net-libraries"></a>Vytvoření silných pojmenovaných knihoven .NET

Měli byste silné jméno open-source knihovny .NET. Silné pojmenování sestavení zajišťuje, že ji může používat většina lidí a přísné načítání sestavení ovlivní pouze rozhraní .NET Framework.

> [!NOTE]
> Tento návod je specifický pro veřejně distribuované knihovny .NET, jako jsou například knihovny .NET publikované v NuGet.org. Silné pojmenování není vyžadováno většinou aplikací .NET a ve výchozím nastavení by nemělo být prováděno.

✔️ ZVAŽTE silné pojmenování sestavení knihovny.

✔️ ZVAŽTe přidání silného pojmenovávacího klíče do systému správy zdrojového kódu.

> Veřejně dostupný klíč umožňuje vývojářům upravit a znovu zkompilovat zdrojový kód knihovny se stejným klíčem.
>
> Silný pojmenovávací klíč byste neměli zveřejňovat, pokud byl v minulosti použit k udělení zvláštních oprávnění ve [scénářích částečné důvěryhodnosti](../../framework/misc/using-libraries-from-partially-trusted-code.md). V opačném případě může dojít k ohrožení existujících prostředí.

> [!IMPORTANT]
> Pokud je požadována identita vydavatele kódu, [authenticode](/windows-hardware/drivers/install/authenticode) a NuGet package signing jsou [doporučeny.](/nuget/create-packages/sign-a-package) Zabezpečení přístupu kódu (CAS) by nemělbýt používán jako zmírnění zabezpečení.

✔️ ZVAŽTE zvýšení verze sestavení pouze na hlavní verze změny pomoci uživatelům snížit přesměrování vazby a jak často jsou aktualizovány.

> Přečtěte si další informace o [správu verzí a verzi sestavení](./versioning.md#assembly-version).

❌NEPŘIdávejte, neodebírejte ani neměňte silný pojmenovávacím klíčem.

> Úprava silného pojmenovávacího klíče sestavení změní identitu sestavení a přeruší zkompilovaný kód, který jej používá. Další informace naleznete v [tématu binární narušující změny](./breaking-changes.md#binary-breaking-change).

❌NEPublikujte verze knihovny se silným názvem a bez silného název. Například `Contoso.Api` a `Contoso.Api.StrongNamed`.

> Publikování dvou balíčků rozpisy váš vývojář ský eco-systém. Také pokud aplikace skončí v závislosti na obou balíčcích vývojář může dojít ke konfliktům názvu typu. Pokud jde o rozhraní .NET, jsou různé typy v různých sestaveních.

>[!div class="step-by-step"]
>[Předchozí](cross-platform-targeting.md)
>[další](nuget.md)
