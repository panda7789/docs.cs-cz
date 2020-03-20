---
title: Co je zastaralé v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 7cfebfde859a95495e9d2d5e42bd034ad5d55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79143132"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a>Co je zastaralé v knihovně tříd rozhraní .NET Framework

Rozhraní .NET se v průběhu času mění. Každá nová verze přidává nové typy a členy typu, které poskytují nové funkce. Stávající typy a jejich členové se také v průběhu času mění. Některé typy se například stávají méně důležitými, protože technologie, kterou podporují, je nahrazena novou technologií a některé metody jsou nahrazeny novějšími metodami, které jsou nějakým způsobem lepší.

Rozhraní .NET Framework a soubor RUNTIME common language usilují o podporu zpětné kompatibility (povolení spuštění aplikací vyvinutých s jednou verzí rozhraní .NET Framework v další verzi rozhraní .NET Framework). To ztěžuje jednoduše odebrat typ nebo člen typu. Místo toho .NET označuje, že typ nebo člen typu by již neměly být používány označením jako zastaralé nebo zastaralé. Zavržení typu nebo člena zahrnuje jeho označení tak, aby vývojáři věděli, že zmizí a bude mít čas reagovat na jeho odebrání. Existující kód, který používá typ nebo člen však nadále spuštěna v nové verzi .NET.

> [!NOTE]
> Termíny *zastaralé* a *zastaralé* mají stejný význam při použití na typy a členy rozhraní .NET.

## <a name="the-obsoleteattribute-attribute"></a>Atribut ObsoleteAttribute

Rozhraní .NET Framework označuje, že typ nebo člen <xref:System.ObsoleteAttribute> typu je zastaralý tím, že jej označíte atributem. Použití atributu na typ nebo člen znamená, že typ nebo člen budou odebrány v některé budoucí verzi rozhraní .NET Framework bez porušení zkompilovaný kód, který používá tento člen.

Kromě označení, že typ nebo člen typu <xref:System.ObsoleteAttribute> je zastaralý, definuje, jak kompilátor zpracovává zdrojový kód, který obsahuje tento typ nebo člen. Kompilátor může zkompilovat kód, ale vyzařuje varovnou zprávu, nebo může považovat použití typu nebo člena za chybu. V prvním případě může kód úspěšně zkompilovat, ale varovná zpráva označuje, že typ nebo člen je zastaralý. V druhém případě kompilace se nezdaří.

I v případě, že kompilace vytvoří <xref:System.ObsoleteAttribute> chybu namísto varovné zprávy, nemá vliv na chování za běhu. To znamená, že aplikace, které používají typ nebo člen a které byly úspěšně zkompilovány, budou vždy úspěšně spuštěny. Pouze pokus o překompilování aplikace, která používá typ nebo člen nezdaří.

## <a name="how-to-handle-obsolete-types-and-members"></a>Jak zacházet se zastaralými typy a členy

Při upgradu a překompilovat existující kód, pomocí zastaralého typu nebo člen, který vytváří upozornění kompilátoru ve vaší aplikaci je naprosto přijatelné. Měli byste však zkontrolovat zprávu upozornění kompilátoru k určení, zda byste měli změnit kód aplikace. Pokud zpráva neukazuje na vhodnou alternativu, měli byste provést jednu z následujících akcí:

- Změňte kód odebráním použití typu nebo člena, pokud je to možné.

     -nebo-

- Projděte si dokumentaci pro tuto oblast technologie a zjistěte, jak reagovat na vyřazení.

Můžete se rozhodnout, že existující kód nebudete znovu kompilovat s novější verzí rozhraní .NET Framework. Místo toho můžete zadat verzi rozhraní .NET Framework, proti které je spuštěn existující zkompilovaný kód. Předpokládejme například, že máte aplikaci s názvem app1.exe, která byla zkompilována proti rozhraní .NET Framework 3.5, ale chcete, aby aplikace běžela proti rozhraní .NET Framework 4.5. To vyžaduje následující kroky:

1. Vytvořte konfigurační soubor pro hlavní spustitelný soubor a pojmenujte jej *appName*.exe.config, kde *appName* je název spustitelného souboru aplikace. Pro aplikaci s názvem *app1.exe* v našem příkladu byste vytvořili konfigurační soubor s názvem *app1.exe.config*.

2. Přidejte do konfiguračního souboru následující.

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

Chcete-li cílit na konkrétní verzi rozhraní .NET Framework, přiřaďte atributu jednu `version` z následujících hodnot řetězce:

|Verze rozhraní .NET Framework|`version`Řetězec|
|-|-|
|4.8|v4.0|
|4.7 (včetně 4.7.1 a 4.7.2)|v4.0|
|4.6 (včetně 4.6.1 a 4.6.2)|v4.0|
|4.5 (včetně 4.5.1 a 4.5.2)|v4.0|
|4|v4.0|
|3,5|v2.0.50727|
|2.0|v2.0.50727|
|1.1|v1.1.4322|
|1.0|v1.0.3705|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a>Zastaralá rozhraní API pro rozhraní .NET Framework 4.5 a novější verze

- [Zastaralé typy](obsolete-types.md)
- [Zastaralé členy](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a>Zastaralá úložiště API pro předchozí verze

- [Zastaralé typy v rozhraní .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))
- [Zastaralé členy v rozhraní .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))
- [Seznam zastaralých rozhraní .NET Framework 3.5](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))
- [Seznam zastaralých rozhraní .NET Framework 2.0](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))

## <a name="see-also"></a>Viz také

- [\<podporovaný modul> Modul runtime](../configure-apps/file-schema/startup/supportedruntime-element.md)
