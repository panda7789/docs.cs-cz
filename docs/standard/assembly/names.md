---
title: Názvy sestavení
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 7a1a4d2512ebb002a3153fe2d51f47157136744d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733097"
---
# <a name="assembly-names"></a>Názvy sestavení
Název sestavení je uložen v metadatech a má významný dopad na rozsah sestavení a použití aplikací. Sestavení se silným názvem má plně kvalifikovaný název, který obsahuje název sestavení, jazykovou verzi, veřejný klíč a číslo verze. To se často označuje jako zobrazovaný název a pro načtená <xref:System.Reflection.Assembly.FullName%2A> sestavení lze získat pomocí vlastnosti.

 Runtime používá tyto informace k vyhledání sestavení a odlišit ji od jiných sestavení se stejným názvem. Například sestavení se silným `myTypes` názvem s názvem může mít následující plně kvalifikovaný název:

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> Architektura procesoru je přidána k identitě sestavení v rozhraní .NET Framework verze 2.0, aby bylo možné verze sestavení specifické pro procesor. Můžete vytvořit verze sestavení, jejichž identita se liší pouze podle architektury procesoru, například 32bitové a 64bitové verze specifické pro procesor. Architektura procesoru není vyžadována pro silné názvy. Další informace naleznete v tématu <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 V tomto příkladu plně kvalifikovaný `myTypes` název označuje, že sestavení má silný název s tokenem veřejného klíče, má hodnotu jazykové verze pro americkou angličtinu a má číslo verze 1.0.1234.0. Jeho architektura procesoru je "msil", což znamená, že bude zkompilován na 32bitový kód nebo 64bitový kód v závislosti na operačním systému a procesoru.

 Kód, který požaduje typy v sestavení, musí používat plně kvalifikovaný název sestavení. To se nazývá plně kvalifikovaná vazba. Částečná vazba, která určuje pouze název sestavení, není povolena při odkazování na sestavení v rozhraní .NET Framework.

 Všechny odkazy na sestavení, které tvoří rozhraní .NET Framework, musí také obsahovat plně kvalifikovaný název sestavení. Například odkaz na sestavení System.Data .NET Framework pro verzi 1.0 by zahrnoval:

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

 Všimněte si, že verze odpovídá číslo verze všech sestavení rozhraní .NET Framework, které jsou dodávány s rozhraním .NET Framework verze 1.0. Pro sestavení rozhraní .NET Framework je hodnota jazykové verze vždy neutrální a veřejný klíč je stejný, jak je znázorněno ve výše uvedeném příkladu.

 Chcete-li například přidat odkaz na sestavení do konfiguračního souboru pro nastavení posluchače trasování, zahrnete plně kvalifikovaný název sestavení rozhraní .NET Framework systému:

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> Za běhu zachází názvy sestavení jako malá a velká písmena při vazbě na sestavení, ale zachová jakékoli případ se používá v názvu sestavení. Několik nástrojů v sadě Windows SDK zpracovává názvy sestavení jako malá a velká písmena. Nejlepších výsledků dosáhnete, když spravujte názvy sestavení, jako by rozlišovaly malá a velká písmena.

## <a name="name-application-components"></a>Pojmenovat součásti aplikace
 Runtime nebere v úvahu název souboru při určování identity sestavení. Identita sestavení, která se skládá z názvu sestavení, verze, jazykové verze a silného názvu, musí být vymazána do běhu.

 Například pokud máte sestavení s názvem *myAssembly.exe,* který odkazuje na sestavení s názvem *myAssembly.dll*, vazba dojde správně, pokud spustíte *myAssembly.exe*. Pokud však jiná aplikace provede metodu *myAssembly.exe* <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>pomocí `myAssembly` metody , určuje, že je již `myAssembly`načten, když *myAssembly.exe* požaduje vazbu na . V tomto případě *myAssembly.dll* je nikdy načten. Vzhledem k *tomu, že myAssembly.exe* neobsahuje požadovaný typ, <xref:System.TypeLoadException> dojde k.

 Chcete-li se tomuto problému vyhnout, ujistěte se, že sestavení, která tvoří vaši aplikaci, nemají stejný název sestavení nebo sestavení se stejným názvem v různých adresářích.

> [!NOTE]
> Pokud v rámci rozhraní .NET Framework vložíte sestavení se silným názvem do globální mezipaměti sestavení, musí se název souboru sestavení shodovat s názvem sestavení, bez rozšíření názvu souboru, například *.exe* nebo *dll*. Pokud je například název souboru sestavení *myAssembly.dll*, `myAssembly`musí být název sestavení . Privátní sestavení nasazená pouze v kořenovém adresáři aplikace mohou mít název sestavení, který se liší od názvu souboru.

## <a name="see-also"></a>Viz také

- [Postup: Určení plně kvalifikovaného názvu sestavy](find-fully-qualified-name.md)
- [Vytváření sestavení](create.md)
- [Sestavení se silným názvem](strong-named.md)
- [Globální mezipaměť sestavení](../../framework/app-domains/gac.md)
- [Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
