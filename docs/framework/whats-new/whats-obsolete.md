---
title: Zastaralé položky v knihovně tříd .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 4de441ff55c3728f43742d6e467deeb47f400507
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140596"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a>Zastaralé položky v knihovně tříd .NET Framework

.NET Framework se v průběhu času mění. Každá nová verze přidává nové typy a členy typu, které poskytují nové funkce. Existující typy a jejich členové se také mění v průběhu času. Některé typy jsou například méně důležité, protože technologie, kterou podporují, je nahrazena novou technologií a některé metody jsou nahrazené novějšími metodami, které jsou vhodnější nebo jsou pro něj plně funkční.

.NET Framework a modul CLR (Common Language Runtime) se snaží podporovat zpětnou kompatibilitu (umožňující aplikacím vyvinutým pomocí jedné verze .NET Framework běžet v další verzi .NET Framework). Díky tomu je obtížné jednoduše odebrat typ nebo člen typu. Místo toho .NET Framework označuje, že typ nebo člen typu by již neměl být použit tak, že ho označíte jako zastaralé nebo zastaralé. Zahození typu nebo členu zahrnuje označení IT, aby se vývojáři dozvěděli, že se o jeho odebrání projeví a mají čas na reakci. Stávající kód, který používá typ nebo člen, však nadále běží v nové verzi .NET Framework.

> [!NOTE]
> *Zastaralé* a *zastaralé* výrazy mají stejný význam při použití na typy a členy .NET Framework.

## <a name="the-obsoleteattribute-attribute"></a>Atribut ObsoleteAttribute

.NET Framework označuje, že typ nebo člen typu je zastaralý, označením s atributem <xref:System.ObsoleteAttribute>. Použití atributu na typ nebo člen označuje, že typ nebo člen bude v některé budoucí verzi .NET Framework odebrán, aniž by došlo k narušení zkompilovaného kódu, který používá daného člena.

Kromě toho, že je typ nebo člen typu zastaralý, <xref:System.ObsoleteAttribute> definuje způsob, jakým kompilátor zpracovává zdrojový kód, který obsahuje daný typ nebo člen. Kompilátor může kompilovat kód, ale generovat zprávu upozornění nebo může zacházet s používáním typu nebo členu jako chyby. V prvním případě může být kód úspěšně zkompilován, ale varovná zpráva označuje, že typ nebo člen je zastaralý. Ve druhém případě kompilace dojde k chybě.

I v případě, že kompilace vytvoří chybu namísto zprávy upozornění, <xref:System.ObsoleteAttribute> nemá vliv na chování za běhu. To znamená, že aplikace, které používají typ nebo člena a které byly úspěšně kompilovány, budou vždy spouštěny úspěšně. Pouze pokus o rekompilaci aplikace, která používá typ nebo člen, se nezdaří.

## <a name="how-to-handle-obsolete-types-and-members"></a>Postup zpracování zastaralých typů a členů

Když upgradujete a znovu zkompilujete stávající kód pomocí zastaralého typu nebo členu, který vytvoří upozornění kompilátoru v aplikaci, je dokonale přijatelné. Měli byste ale zkontrolovat zprávu s upozorněním kompilátoru, abyste zjistili, jestli byste měli změnit kód aplikace. Pokud zpráva neodkazuje na vhodnou alternativu, měli byste provést jednu z následujících akcí:

- Pokud je to možné, změňte kód tak, že odeberete použití typu nebo členu.

     -nebo-

- Přečtěte si dokumentaci k této technologické oblasti a určete, jak reagovat na vyřazení.

Můžete se rozhodnout, že nebudete znovu kompilovat existující kód v novější verzi .NET Framework. Místo toho můžete určit verzi .NET Framework, na kterou se má existující zkompilovaný kód spouštět. Předpokládejme například, že máte aplikaci s názvem app1. exe, která byla zkompilována proti .NET Framework 3,5, ale chcete, aby aplikace běžela v .NET Framework 4,5. To vyžaduje následující kroky:

1. Vytvořte konfigurační soubor pro hlavní spustitelný soubor a pojmenujte jej *AppName*. exe. config, kde *AppName* je název spustitelného souboru aplikace. Pro aplikaci s názvem app1. exe v našem příkladu byste vytvořili konfigurační soubor s názvem app1. exe. config.

2. Do konfiguračního souboru přidejte následující.

    ```xml
    <configuration>
       <startup> 
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

V následující tabulce jsou uvedeny řetězcové hodnoty, které můžete přiřadit k atributu `version` pro cílení na konkrétní verzi .NET Framework:

|Verze rozhraní .NET Framework|`version` řetězec|
|-|-|
|4,8|4\.0|
|4,7 (včetně 4.7.1 a 4.7.2)|4\.0|
|4,6 (včetně 4.6.1 a 4.6.2)|4\.0|
|4,5 (včetně 4.5.1 a 4.5.2)|4\.0|
|4|4\.0|
|3.5|v 2.0.50727|
|2.0|v 2.0.50727|
|1.1|v 1.1.4322|
|1.0|v 1.0.3705|

## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a>Zastaralé seznamy pro .NET Framework 4,5 a novější verze

- [Zastaralé typy](obsolete-types.md)
- [Zastaralé členy](obsolete-members.md)

## <a name="obsolete-lists-for-previous-versions"></a>Zastaralé seznamy pro předchozí verze

- [Zastaralé typy v .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))

- [Zastaralí členové v .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))

- [Seznam zastaralých .NET Framework 3,5](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))

- [Seznam zastaralých .NET Framework 2,0](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))

## <a name="see-also"></a>Viz také:

- [\<element > supportedRuntime](../configure-apps/file-schema/startup/supportedruntime-element.md)
